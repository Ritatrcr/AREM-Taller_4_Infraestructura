# 📄 Informe Técnico del Taller

## 🔖 Taller 4 – Mapa de Infraestructura y Diagnóstico Técnico

## 👥 Integrantes del equipo
- Rita Trindade da Cruz (ritatrcr)
- Brandon Merchan Sandoval (merchito12)
- Daniel Felipe Forero Sánchez (DanielForero14)

---

## 🧠 Descripción general del trabajo
El objetivo de este taller fue construir un **mapa de infraestructura tecnológica** y realizar un **diagnóstico técnico** sobre componentes críticos, riesgos operativos, cuellos de botella y oportunidades de mejora dentro de un sistema de información.

El trabajo se desarrolló inicialmente a partir del caso base **RedExpress**, una plataforma de logística con infraestructura híbrida, la cual fue utilizada en clase para identificar nodos, servicios, dependencias, zonas de carga y riesgos técnicos asociados a la disponibilidad, el monitoreo y la escalabilidad.

Posteriormente, el análisis fue adaptado al cliente real **Elite Airsoft**, con el fin de aplicar los conceptos vistos en clase a una situación más cercana a un entorno real, evaluando su infraestructura actual, sus posibles debilidades y las recomendaciones técnicas más relevantes para fortalecer su operación.

Esta aproximación permitió comprender la importancia de representar la infraestructura de un sistema no solo desde sus componentes, sino también desde sus riesgos, puntos únicos de falla y capacidad de crecimiento.

---

## 🔧 Proceso de desarrollo
El desarrollo del taller inició con la lectura y análisis del caso base RedExpress, identificando los componentes principales de su arquitectura, tales como balanceadores de carga, API Gateway, servicios en la nube, servidores regionales, módulos de procesamiento, base de datos y herramientas de monitoreo.

Durante la sesión de clase se construyó un **mapa preliminar de infraestructura** del caso base, con el propósito de visualizar cómo se conectan los distintos elementos del sistema y detectar posibles zonas sensibles relacionadas con latencia, disponibilidad, redundancia y escalabilidad geográfica.

A partir de este primer ejercicio, se documentaron observaciones y hallazgos técnicos en torno al comportamiento esperado del sistema, especialmente en escenarios de alta demanda como campañas promocionales o temporadas de alto volumen.

Posteriormente, fuera de clase, se trasladó esta metodología al cliente real **Elite Airsoft**, elaborando un mapa de infraestructura final y redactando un informe técnico con el diagnóstico de debilidades reales o potenciales, junto con recomendaciones fundamentadas en buenas prácticas de arquitectura de infraestructura.

Como herramienta principal para el modelado visual se utilizó **draw.io**, lo que facilitó la representación gráfica de la infraestructura y la iteración sobre los diagramas.

---

## 🧩 Análisis del modelo propuesto

### 🖥️ Mapa de infraestructura
El mapa de infraestructura elaborado representa de forma clara:
- Los componentes tecnológicos principales del sistema.
- La relación entre usuarios, servicios, procesamiento y almacenamiento.
- Los puntos de entrada y distribución de carga.
- Los elementos críticos de operación, monitoreo y disponibilidad.
- Las dependencias entre componentes internos y externos.

Este mapa permite entender cómo se soporta técnicamente la operación del sistema y cuáles son las áreas que requieren mayor atención desde el punto de vista arquitectónico.

### ⚠️ Diagnóstico técnico
El diagnóstico realizado permitió identificar aspectos relevantes como:
- Riesgo de **puntos únicos de falla** en componentes centrales.
- Posibles **cuellos de botella** en bases de datos o servicios críticos.
- Problemas de **latencia** en procesos que requieren trazabilidad o respuesta en tiempo real.
- Limitaciones en la **escalabilidad por zonas geográficas** o por crecimiento de la demanda.
- Necesidad de fortalecer mecanismos de **monitoreo, redundancia y recuperación**.

Este análisis permitió proponer acciones de mejora orientadas a aumentar la disponibilidad, resiliencia y capacidad de crecimiento de la infraestructura.

---

## 📈 Diagramas entregados
- Mapa de infraestructura preliminar – Caso base RedExpress
- Mapa de infraestructura final – Cliente real Elite Airsoft

*(Los diagramas finales se encuentran en la carpeta `/entrega` del repositorio).*

---

## 🗂️ Organización del repositorio
El repositorio se encuentra organizado de la siguiente manera:

- **/clase**: contiene el mapa borrador del caso base RedExpress y las notas generadas durante la sesión de clase.
- **/entrega**: contiene el mapa final del cliente real Elite Airsoft, el informe técnico y el documento de referencias.

Esta estructura permite evidenciar tanto el proceso de análisis realizado en clase como la aplicación final del taller a un caso real.

---

## 🔍 Investigación complementaria

### Tema investigado
Buenas prácticas de arquitectura de infraestructura en entornos cloud, on-premise e híbridos, con énfasis en escalabilidad, redundancia, monitoreo y alta disponibilidad.

### Resumen
La arquitectura de infraestructura cumple un papel fundamental en la estabilidad y continuidad operativa de los sistemas de información. Un diseño adecuado debe considerar distribución de carga, tolerancia a fallos, monitoreo constante, recuperación ante incidentes y capacidad de escalado frente al crecimiento de usuarios o transacciones.

En entornos híbridos o distribuidos, estas decisiones son aún más importantes, ya que los sistemas dependen de múltiples componentes interconectados. Por ello, el uso de balanceadores, replicación de datos, monitoreo proactivo y eliminación de puntos únicos de falla son prácticas clave para mejorar la resiliencia y el rendimiento de la plataforma.

---

## 📚 Referencias
- [1] Universidad de La Sabana. Material de clase – Arquitectura Empresarial. s.f.  
- [2] Amazon Web Services (AWS). Best Practices for High Availability and Scalability. s.f.  
- [3] Microsoft Azure Architecture Center. Reliability and Infrastructure Design Principles. s.f.  
- [4] Google Cloud Architecture Framework. Operational Excellence and Reliability. s.f.

---

## ✅ Licencia
Este taller hace parte del curso de **Arquitectura Empresarial – Universidad de La Sabana**.  
Uso académico bajo licencia **MIT**.