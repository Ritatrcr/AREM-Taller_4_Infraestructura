# 🗒️ Registro de Trabajo en Clase - Taller: Mapa de Infraestructura RedExpress

## 📆 Fecha de la sesión
7 de Marzo de 2024

---

## 👥 Integrantes presentes
- Rita Trindade
- Brandon Merchan
- Daniel Forero

---

## 🧠 Actividades realizadas en clase

Durante la sesión el equipo trabajó en el modelado preliminar de la infraestructura tecnológica de **RedExpress**, una plataforma logística híbrida. Se abordaron las siguientes actividades:

- **Discusión con el equipo:** Se analizó el caso base de RedExpress, identificando los componentes principales del sistema: app móvil, plataforma web, API Gateway, servidores regionales y base de datos centralizada. Se debatió qué componentes representan mayor riesgo operacional.
- **Decisiones de modelado:** Se acordó representar la arquitectura en **6 capas funcionales** (Clientes → Edge/CDN → Ingreso → Microservicios → Datos → Infraestructura física), siguiendo una visión lógica de arriba hacia abajo que refleja el flujo real de las peticiones.
- **Herramientas usadas:** Se utilizó **draw.io** para el diagrama digital, complementado con bocetos en papel durante la fase inicial de discusión.
- **Avance alcanzado:** Se completó el mapa lógico-físico preliminar con los componentes principales, se identificaron los puntos de riesgo y se levantó un primer listado de problemas y posibles soluciones.

---

## Boceto inicial del modelo

> _(Insertar aquí la captura del diagrama draw.io o foto del boceto en papel realizado durante la sesión.)_

El modelo cubre las siguientes capas identificadas en clase:

```
[Clientes: App Móvil / Web / Admin / API Partners]
            ↓
[Edge: WAF Cloudflare + CDN Global]
            ↓
[Ingreso: Load Balancer + API Gateway + Auth Service]
            ↓
[Microservicios: Package · Tracking · Route Engine · Notifications · Analytics]
            ↓
[Datos: Message Queue · Redis Cache · DB Primaria · Read Replica · InfluxDB]
            ↓
[Infraestructura: Servidores Regionales (Bogotá / Cali) + Nube AWS/Azure]
```

---

## 🐛 Problemas identificados y cómo podrían abordarse

A continuación se documentan los problemas detectados durante el análisis en clase, organizados por área crítica:

### 1. Puntos Únicos de Falla (SPOF)

| Componente | Problema identificado | Cómo abordarlo |
|---|---|---|
| **Base de datos primaria (PostgreSQL)** | Instancia centralizada única: si falla, toda la plataforma deja de operar. | Migrar a arquitectura **Multi-AZ** con failover automático (RDS Multi-AZ o CockroachDB). El failover automático debería ocurrir en menos de 30 segundos. |
| **API Gateway** | Opera como instancia única sin réplica activa. | Configurar **Kong en modo activo-activo** con múltiples nodos y balanceo entre ellos. |
| **Redis Cache** | Nodo único: un reinicio invalida todas las sesiones activas. | Implementar **Redis Cluster** con mínimo 3 nodos maestros y réplicas. |
| **Load Balancer** | Modo Activo-Pasivo genera 30-60 segundos de corte durante el failover. | Migrar a configuración **Activo-Activo** con balanceo real entre dos instancias. |

### 2. Cuellos de Botella de Rendimiento

| Síntoma | Causa raíz | Cómo abordarlo |
|---|---|---|
| **Latencia de rastreo > 340ms (p95)** | El Tracking Service consulta directamente la DB primaria sin capa de caché, y comparte recursos con queries transaccionales y analíticos. | Aplicar el patrón **CQRS**: las escrituras GPS van a un topic Kafka de forma asíncrona hacia InfluxDB; las lecturas de rastreo leen de **Redis con TTL de 5-10 segundos**. Esto reduce la latencia de lectura a menos de 25ms. |
| **Route Engine bloqueante** | El cálculo de rutas es CPU-intensivo y se ejecuta de forma síncrona, bloqueando el servicio durante el procesamiento. | Introducir un **sistema de colas de trabajos** (Celery + Redis o BullMQ). Los cálculos pesados se encolan y procesan en workers independientes sin bloquear el hilo principal. |
| **Analytics sobre DB primaria** | Las consultas analíticas compiten con operaciones transaccionales en la misma instancia. | Separar la carga analítica hacia la **Read Replica** (ya existente pero subutilizada) o, a mediano plazo, implementar un **Data Warehouse** dedicado (BigQuery / Redshift) con ETL periódico. |
| **Replication lag (2-5s)** | En picos de escritura, la réplica de lectura entrega datos desactualizados. | Agregar más réplicas de lectura y ajustar la configuración de replicación. Para analytics, tolerar el lag es aceptable; para rastreo, usar Redis como fuente de verdad en lugar de la réplica. |

### 3. Escalabilidad Geográfica

| Zona | Problema | Cómo abordarlo |
|---|---|---|
| **Región Norte (Bogotá)** | Servidor físico en co-location sin redundancia interna. Una falla de hardware requiere intervención manual. | Configurar un **servidor en standby en la misma zona** o usar instancias de nube elásticas como complemento para failover automático. |
| **Región Sur (Cali/Medellín)** | Enlace WAN de 100Mbps insuficiente durante campañas de alto volumen. | Ampliar el ancho de banda del enlace a 1Gbps o implementar un **modelo de offload a nube** en temporada alta (cloud bursting). |
| **Zonas Rurales** | Los mensajeros pierden actualizaciones de estado GPS al carecer de conectividad. La app no tiene modo offline. | Implementar **almacenamiento local con SQLite** en la app móvil, con una cola de sincronización que sube los eventos acumulados cuando se recupera la conexión. |
| **Sin balanceo geográfico inteligente** | Todo el tráfico pasa por los mismos balanceadores sin considerar la ubicación del usuario. | Implementar **GeoDNS o Anycast routing** para dirigir a los usuarios al nodo más cercano automáticamente. |

### 4. Observabilidad y Recuperación

| Problema | Cómo abordarlo |
|---|---|
| **Sin distributed tracing** | Implementar **OpenTelemetry** con Jaeger o Zipkin para trazas end-to-end entre microservicios. Esto permite identificar qué servicio introduce latencia en una cadena de llamadas. |
| **RTO de 6 horas en el plan de DR** | Inaceptable para temporada alta. Implementar un entorno de **warm standby** en nube con sincronización continua de la DB. El objetivo debería ser un RTO < 1 hora y un RPO < 15 minutos. |
| **Sin Dead Letter Queue (DLQ) en la cola de mensajes** | Configurar una DLQ en Kafka/RabbitMQ para capturar mensajes fallidos y permitir reintentos controlados sin pérdida de eventos. |
| **Alertas incompletas** | Las alertas actuales no cubren el replication lag de la DB ni la latencia del Tracking Service. Agregar alertas específicas en **Prometheus/Grafana** para estos indicadores con umbrales definidos. |

---

## 🔁 Tareas definidas para complementar el taller

| Tarea asignada | Responsable | Fecha estimada |
|---|---|---|
| Modelado final del diagrama en draw.io | Rita | 10/08 |
| Redacción del informe de diagnóstico técnico | Brandon | 11/08 |
| Investigación de soluciones (CQRS, Redis Cluster, Multi-AZ) | Daniel | 12/08 |
| Revisión conjunta y ajustes finales | Todo el equipo | 13/08 |

---

_Este documento resume el trabajo colaborativo realizado durante la sesión del taller de Infraestructura Tecnológica en el curso AREM - Universidad de La Sabana._