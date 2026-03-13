# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
**Taller 4 - Diagnóstico técnico de infraestructura y análisis de cuellos de botella en Élite Airsoft**

---

## 👥 Integrantes del equipo
- Daniel Forero
- Rita Trindade
- Brandon Merchans

---

## 🧠 Descripción general del trabajo

El presente trabajo tuvo como objetivo analizar la infraestructura actual del cliente real **Élite Airsoft**, identificar debilidades técnicas y operativas dentro de su funcionamiento actual, y redactar un diagnóstico técnico sustentado en el mapa de infraestructura elaborado por el equipo.

Para el desarrollo del taller se tomó como base la información recolectada en la ficha de caracterización del cliente, donde se evidenció que el negocio funciona actualmente mediante una combinación de herramientas digitales dispersas, principalmente **Instagram**, **WhatsApp**, **Google Forms**, **Nequi** y **Excel**, sin contar con una plataforma centralizada que integre reservas, pagos, consentimientos y seguimiento de clientes.

A partir de ello, el equipo construyó una representación del flujo real del negocio y realizó un análisis técnico orientado a detectar cuellos de botella, puntos críticos de dependencia, debilidades de trazabilidad y limitaciones de escalabilidad. Finalmente, se complementó el ejercicio con una breve investigación sobre buenas prácticas de arquitectura de infraestructura, especialmente en entornos **cloud**, **on-premise** e **híbridos**, para relacionarlas con la situación actual del cliente.

---

## 🔧 Proceso de desarrollo

El desarrollo del trabajo se realizó en varias etapas. En primer lugar, se revisó la información suministrada por el cliente para comprender el funcionamiento general del negocio, sus objetivos estratégicos, los procesos clave y las principales dificultades operativas. A partir de ese levantamiento inicial, se identificaron los componentes tecnológicos actualmente utilizados y la forma en que estos intervienen en la captación de clientes, la gestión de reservas, el registro de consentimientos y el proceso de pago.

Posteriormente, se estructuró el mapa de infraestructura actual del cliente. Para ello, se separó el modelo en cuatro zonas principales: **cliente/jugador**, **herramientas digitales**, **operador del negocio** y **debilidades o cuellos de botella identificados**. Esta organización permitió visualizar de forma clara no solo los componentes existentes, sino también la relación entre ellos y el alto nivel de intervención manual requerido para que la operación funcione.

Después de modelar la situación actual, se llevó a cabo el diagnóstico técnico. En esta etapa se analizaron los riesgos asociados a la falta de integración entre herramientas, la dependencia operativa de una sola persona, la ausencia de trazabilidad completa en pagos y reservas, y la carencia de una base centralizada de clientes. Finalmente, se contrastó el caso con buenas prácticas de arquitectura de infraestructura para proponer una interpretación más sólida del problema desde una perspectiva técnica y no únicamente operativa.

---

## 🧩 Análisis del modelo propuesto

### Cómo se estructura el modelo entregado

El modelo entregado representa la infraestructura actual del cliente mediante un flujo secuencial que inicia con la captación del jugador en redes sociales, continúa con el contacto por WhatsApp, el diligenciamiento del consentimiento informado en Google Forms, el pago del anticipo por Nequi, la asistencia a la partida y el pago final.

A nivel estructural, el modelo muestra tres elementos principales:

1. **Los actores involucrados**, especialmente el cliente/jugador y el operador del negocio.
2. **Las herramientas digitales utilizadas**, que actualmente están separadas y no comparten información de manera automática.
3. **Las debilidades de la arquitectura actual**, representadas como puntos críticos dentro del flujo.

Esta estructura permite entender que el negocio sí posee recursos tecnológicos, pero no cuenta con una arquitectura integrada que conecte de manera ordenada todos los procesos.

### Cómo representa las necesidades del cliente

El modelo refleja adecuadamente la situación real del cliente porque muestra que la operación depende de herramientas de bajo costo y fácil acceso, algo coherente con un emprendimiento pequeño en crecimiento. También evidencia que el negocio necesita mantener la operación activa mientras mejora sus procesos, lo cual implica que las soluciones futuras deben ser graduales y realistas.

Además, el modelo representa necesidades concretas del cliente como:

- Mejorar el control de reservas y asistencia.
- Reducir errores por gestión manual.
- Tener mayor trazabilidad de pagos.
- Disponer de una base organizada de clientes.
- Mejorar la visibilidad digital del negocio.
- Evitar una dependencia total del fundador para tareas operativas repetitivas.

### Qué supuestos se tomaron

Para construir el análisis se tomaron algunos supuestos razonables a partir de la información disponible:

- Se asumió que **WhatsApp es el principal canal operativo**, no solo para atención, sino también para reservas, confirmaciones y recepción de comprobantes.
- Se asumió que **Excel cumple un rol básico de control**, pero no funciona como sistema transaccional ni como base de datos central.
- Se asumió que **Google Forms no está integrado** con un sistema de reservas o validación automática.
- Se asumió que **Nequi se utiliza como mecanismo práctico de recaudo**, pero sin conciliación automática ni trazabilidad estructurada.
- Se asumió que el negocio tiene una operación pequeña, por lo que una migración tecnológica completa no sería viable de forma inmediata.
- Se asumió que la mejora más realista para el cliente sería una evolución progresiva hacia una arquitectura más integrada, posiblemente de tipo híbrido y de bajo costo.

---

## 🩺 Diagnóstico técnico de la infraestructura actual

La infraestructura actual de Élite Airsoft puede clasificarse como una operación digital funcional, pero **fragmentada y altamente manual**. Aunque el negocio utiliza herramientas ampliamente disponibles, estas no se encuentran articuladas dentro de una plataforma única, lo que provoca desorden informacional, dependencia operativa del fundador y baja trazabilidad en procesos clave.

### 1. Fragmentación de herramientas

Actualmente, el flujo del negocio se distribuye entre redes sociales para captación, WhatsApp para reservas y atención, Google Forms para consentimientos, Nequi para pagos y Excel para control básico. Esta fragmentación impide que exista una sola fuente de verdad sobre cada cliente, cada evento y cada pago realizado.

### 2. Cuello de botella en reservas

La reserva depende casi completamente de la atención manual del operador. No existe un sistema centralizado que valide cupos, disponibilidad, pagos y confirmaciones en tiempo real. Esto genera riesgo de sobrecupos, errores de coordinación y pérdida de trazabilidad histórica.

### 3. Verificación manual de pagos

Los pagos se realizan en dos momentos, pero su validación depende de mensajes enviados por el cliente y revisados manualmente por el operador. Este proceso no genera historial financiero estructurado, dificulta conciliaciones y aumenta la probabilidad de pérdida de evidencia.

### 4. Desconexión entre consentimiento y operación

Aunque existe un Google Forms para consentimiento informado, este elemento no está integrado automáticamente con el proceso de reserva ni con la lista final de asistentes. Esto provoca que información importante quede aislada y no haga parte de un flujo validado de punta a punta.

### 5. Dependencia total del fundador

El modelo actual presenta una dependencia crítica de una sola persona. El operador publica, responde, verifica, confirma, cobra y registra. Desde la perspectiva de arquitectura, esto constituye un punto único de falla, ya que cualquier ausencia, retraso o saturación del responsable afecta directamente la continuidad operativa.

### 6. Baja capacidad de escalabilidad

La infraestructura actual puede funcionar para una operación pequeña, pero presenta dificultades para crecer. Si el negocio aumenta el número de clientes, eventos o campañas, también crecerá el volumen de conversaciones, comprobantes, formularios y registros, haciendo más probable la aparición de errores, duplicidades y descontrol operativo.

### 7. Limitaciones de seguimiento comercial

Al no existir una base centralizada de clientes ni un CRM, el negocio no puede aprovechar de forma adecuada la información histórica de jugadores, asistencia, frecuencia de compra o comportamiento de consumo. Esto reduce la capacidad de fidelización, remarketing y segmentación comercial.

En conjunto, el diagnóstico muestra que el problema principal no es la ausencia total de tecnología, sino la falta de **integración, trazabilidad, automatización y escalabilidad** dentro de la infraestructura actual.

---

## 📈 Diagrama final entregado

Inserte aquí la imagen o referencia del diagrama final.

Ejemplo en Markdown:

![Mapa de infraestructura actual de Élite Airsoft](./img/mapa_infraestructura_elite_airsoft.png)

O si prefieren dejar referencia al archivo:

- `modelo-final.drawio`
- `mapa-infraestructura.pdf`

---

## 📋 Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---|---|---|---|
| Cliente / Jugador | Actor | Persona interesada en reservar y asistir a una partida de airsoft | Cliente |
| Instagram / Facebook | Canal digital | Medio principal de captación y promoción del negocio | Operador del negocio |
| WhatsApp | Canal operativo | Medio principal de atención, reservas, confirmaciones y recepción de comprobantes | Operador del negocio |
| Google Forms | Herramienta digital | Formulario usado para consentimiento informado previo a la partida | Operador del negocio / Cliente |
| Nequi | Herramienta de pago | Medio usado para recibir adelantos y pagos finales | Cliente / Operador |
| Excel | Herramienta de control | Registro básico y manual de reservas, ingresos o listados | Operador del negocio |
| Operador del negocio | Actor | Persona que administra reservas, pagos, atención y coordinación general | Fundador |
| Reserva | Proceso | Solicitud y confirmación de participación en una partida o evento | Operador del negocio |
| Pago anticipado | Proceso financiero | Adelanto del 50% para asegurar la reserva | Cliente |
| Consentimiento informado | Documento / proceso | Registro previo requerido antes de participar en la actividad | Cliente |
| Asistencia a partida | Proceso operativo | Participación presencial en la experiencia de airsoft | Cliente / Operador |
| Base de clientes | Componente ausente | Repositorio estructurado de historial, datos y seguimiento comercial | No existe actualmente |

---

## 🔍 Investigación complementaria

### Tema investigado:
**Buenas prácticas de arquitectura de infraestructura: confiabilidad, integración progresiva y enfoque híbrido para negocios en crecimiento**

### Resumen

La investigación permitió identificar que los marcos de arquitectura de infraestructura más reconocidos, como los de **AWS**, **Microsoft Azure** y **Google Cloud**, coinciden en varios principios clave: confiabilidad, resiliencia, trazabilidad, simplicidad operativa y capacidad de recuperación ante fallos. En particular, estos enfoques recomiendan diseñar soluciones que reduzcan puntos únicos de falla, faciliten la automatización, mejoren el monitoreo y permitan una recuperación ordenada frente a incidentes. Para el caso analizado, esto es relevante porque actualmente la operación depende en gran medida de una sola persona y de varias herramientas aisladas sin integración formal.

Otra idea importante de la investigación es que no todas las organizaciones necesitan pasar de inmediato a una arquitectura completamente empresarial o a una nube compleja. En muchos casos, especialmente en emprendimientos o negocios pequeños, resulta más adecuado adoptar un enfoque **gradual** o **híbrido**, en el que se mantengan algunas herramientas actuales mientras se incorporan componentes de integración, automatización y centralización de datos. Este principio aplica al caso de Élite Airsoft, ya que el cliente tiene restricciones de presupuesto, necesita seguir operando sin interrupciones y requiere soluciones realistas de bajo costo.

Relacionando estas buenas prácticas con el taller, se concluye que la situación del cliente no debe resolverse con una transformación tecnológica abrupta, sino con una evolución progresiva hacia una arquitectura más ordenada. El primer objetivo no sería migrar todo a una gran plataforma, sino reducir la fragmentación actual mediante un sistema más centralizado de reservas, pagos, consentimientos y base de clientes. Desde la perspectiva de arquitectura, la prioridad debería estar en mejorar la trazabilidad, disminuir la dependencia operativa del fundador y sentar bases para una escalabilidad futura.

---

## ✅ Conclusiones

El análisis realizado evidencia que Élite Airsoft cuenta con una infraestructura digital básica que le permite operar, pero no con una arquitectura integrada que soporte de manera sólida su crecimiento. El negocio depende de varias herramientas útiles, aunque desconectadas entre sí, lo que provoca procesos manuales, pérdida de trazabilidad y alta dependencia de una sola persona.

Los cuellos de botella más importantes se concentran en la gestión manual de reservas, la verificación no estructurada de pagos, la desconexión entre consentimiento y operación, y la inexistencia de una base centralizada de clientes. Estas condiciones afectan tanto la eficiencia operativa como la capacidad futura de escalabilidad y fidelización.

Finalmente, el contraste con buenas prácticas de arquitectura de infraestructura permite concluir que el caso requiere una mejora progresiva y no una transformación radical inmediata. Una evolución hacia una arquitectura más integrada, simple y de bajo costo sería coherente con las necesidades, restricciones y contexto real del cliente.

---

## 📚 Referencias

[1] Amazon Web Services. *AWS Well-Architected Framework – Reliability Pillar*. AWS Documentation.  
[2] Microsoft. *Azure Well-Architected Framework*. Microsoft Learn.  
[3] Microsoft. *Reliability design principles*. Microsoft Learn.  
[4] Google Cloud. *Google Cloud Well-Architected Framework: Reliability pillar*. Google Cloud Documentation.  
[5] Microsoft. *Hybrid architecture design*. Azure Architecture Center.  
[6] Ficha de caracterización del cliente – Élite Airsoft. Documento base del caso analizado.
