# 📄 Informe Técnico del Taller

## 🔖 Taller 4 – Mapa de Infraestructura y Diagnóstico Técnico

## 👥 Integrantes del equipo
- Rita Trindade da Cruz (ritatrcr)
- Brandon Merchan Sandoval (merchito12)
- Daniel Felipe Forero Sánchez (DanielForero14)

---

## 🧠 Descripción general del trabajo
El objetivo de este taller fue construir un **mapa de infraestructura tecnológica** y realizar un **diagnóstico técnico** sobre un sistema base, con el fin de identificar componentes críticos, riesgos operativos, cuellos de botella y oportunidades de mejora en términos de disponibilidad, escalabilidad y monitoreo.

El trabajo se desarrolló tomando como referencia el caso base **RedExpress (Plataforma de Logística)**, el cual fue analizado inicialmente en clase para comprender la arquitectura tecnológica del sistema, sus componentes principales y sus posibles limitaciones. Posteriormente, este análisis sirvió como base para aplicar los conceptos al sistema real del cliente.

Esta aproximación permitió comprender la importancia de representar visualmente la infraestructura de un sistema, así como la necesidad de evaluar sus puntos sensibles para proponer mejoras alineadas con buenas prácticas de arquitectura empresarial e infraestructura tecnológica.

---

## 🔧 Proceso de desarrollo
El desarrollo del taller inició con el análisis del caso base de RedExpress, identificando los elementos principales de su infraestructura, entre ellos la aplicación móvil, la plataforma web, los balanceadores de carga, el API Gateway, los módulos de procesamiento, los servicios en la nube, los servidores regionales y la base de datos centralizada o distribuida.

Durante la sesión de clase se construyó un **primer borrador del mapa de infraestructura**, el cual permitió representar de manera general la relación entre los distintos componentes tecnológicos del sistema. A partir de este modelo preliminar, se identificaron posibles zonas críticas relacionadas con la latencia en el rastreo en tiempo real, la existencia de puntos únicos de falla y las limitaciones de escalabilidad geográfica.

Posteriormente, el mapa fue refinado fuera de clase, organizando de forma más clara los componentes, sus dependencias y sus mecanismos de soporte, como el monitoreo y las alertas. De manera complementaria, se elaboró un **diagnóstico técnico** que describe las principales debilidades detectadas y propone posibles acciones de mejora.

Como herramienta principal se utilizó **draw.io**, lo que facilitó la construcción, iteración y ajuste del mapa de infraestructura durante el desarrollo del taller.

---

## 🧩 Análisis del modelo propuesto

### 🗺️ Mapa de infraestructura
El mapa de infraestructura propuesto se estructura a partir de:
- Componentes de acceso al sistema, como aplicación móvil y plataforma web.
- Elementos de distribución de tráfico, como balanceadores de carga y API Gateway.
- Servicios de negocio relacionados con el procesamiento de rutas, rastreo y gestión de estados de paquetes.
- Infraestructura de datos, incluyendo base de datos distribuida o centralizada.
- Componentes de soporte, como monitoreo, alertas y servidores regionales.

Este modelo permite representar de forma clara cómo se conectan los elementos tecnológicos del sistema y cómo fluye la información entre usuarios, servicios y almacenamiento.

### ⚠️ Diagnóstico técnico
A partir del análisis del mapa se identificaron las siguientes áreas críticas:
- **Latencia en rastreo en tiempo real**, debido a la alta dependencia de servicios centrales y la posible saturación de consultas.
- **Riesgo de puntos únicos de falla**, especialmente en componentes como gateway, balanceadores o base de datos si no cuentan con redundancia.
- **Limitaciones de escalabilidad por zonas geográficas**, considerando que RedExpress opera con servidores regionales y requiere disponibilidad en distintos territorios.
- **Necesidad de monitoreo continuo**, para detectar incidentes, degradación del servicio y fallos en componentes críticos.

El diagnóstico permitió no solo identificar posibles fallos, sino también plantear medidas de mejora orientadas a fortalecer la resiliencia y el rendimiento de la plataforma.

---

## 📈 Diagramas entregados
- Mapa de Infraestructura Tecnológica – Caso base
- Diagnóstico técnico de riesgos, debilidades y oportunidades de mejora

*(Los archivos finales se encuentran en la carpeta `/entrega` del repositorio).*

---

## 🗂️ Organización del repositorio
El repositorio se encuentra organizado de la siguiente manera:
- **/clase**: contiene los borradores y notas generadas durante la sesión de clase.
- **/entrega**: contiene el mapa final, el informe técnico y las referencias utilizadas.

Esta organización permite evidenciar tanto el proceso de construcción del análisis como la entrega final del taller.

---

## 🔍 Investigación complementaria
### Tema investigado
Buenas prácticas de arquitectura de infraestructura en entornos cloud, on-premise e híbridos, con enfoque en disponibilidad, redundancia, monitoreo y escalabilidad.

### Resumen
La arquitectura de infraestructura es un elemento fundamental en el diseño de sistemas empresariales, ya que permite garantizar que las aplicaciones sean estables, escalables y resilientes frente a fallos o aumentos de demanda. En este contexto, prácticas como el uso de balanceadores de carga, bases de datos distribuidas, mecanismos de monitoreo, redundancia de componentes y despliegues híbridos son esenciales para asegurar la continuidad operativa.

El análisis de infraestructura no solo ayuda a visualizar la composición técnica de un sistema, sino que también permite identificar debilidades arquitectónicas y plantear mejoras sostenibles que respondan a las necesidades del negocio y de los usuarios.

---

## 📚 Referencias
- [1] Universidad de La Sabana. Material de clase – Arquitectura Empresarial. s.f.  
- [2] Amazon Web Services (AWS). Infrastructure and Architecture Best Practices. s.f.  
- [3] Microsoft Azure. Cloud Architecture Framework. s.f.  
- [4] Google Cloud. Reliability, Scalability and High Availability Concepts. s.f.

---

## ✅ Licencia
Este taller hace parte del curso de **Arquitectura Empresarial – Universidad de La Sabana**. Uso académico bajo licencia **MIT**.