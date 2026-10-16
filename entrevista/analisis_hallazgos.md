# Análisis de hallazgos de la entrevista

## 1. Propósito y alcance

Este análisis organiza los hallazgos de la entrevista académica simulada sobre el gobierno de datos en una inmobiliaria. Se emplea para orientar las decisiones del modelo ArchiMate y el alcance del Portal de Gobierno de Datos. La entrevista es evidencia del ejercicio académico; no se presenta como una auditoría ni como una validación independiente de una organización real.

El análisis distingue cuatro categorías:

- **Hallazgo de la entrevista:** contenido expresado en la conversación simulada.
- **Decisión de diseño:** respuesta arquitectónica que se plantea para el proyecto.
- **Supuesto:** afirmación marcada como hipotética o que requiere confirmación.
- **Pendiente:** pregunta que el equipo debe resolver con la fuente original, Tecnología, las áreas o Jurídica.

## 2. Síntesis del proceso descrito

La conversación describe un proceso de gobierno de datos principalmente manual y reactivo. Puede activarse por un reclamo, una auditoría, un sistema nuevo o la notificación de un campo. Gobierno de Datos registra el aviso y coordina la revisión con el área dueña y Jurídica; solicita a Tecnología los metadatos técnicos disponibles; consolida información de negocio y técnica en un registro maestro; y el jefe del área revisa y aprueba la ficha.

> El orden no es completamente lineal: la solicitud de extracción técnica puede ocurrir antes de la reunión. La actualización anual del inventario se describe como un ciclo adicional, no como el cierre obligatorio de cada alta de atributo.

La entrevista atribuye responsabilidades distintas: Marcela coordina, los analistas levantan información y detectan duplicados, los jefes de área aprueban la definición y la clasificación de sus datos, Jurídica resuelve dudas de autorización y clasificación, y Gerencia aprueba políticas generales. Tecnología aporta los datos técnicos cuando están disponibles.

## 3. Hallazgos principales y decisiones de diseño

| Hallazgo de la entrevista | Consecuencia para el proyecto | Decisión de diseño documentada | Estado |
|---|---|---|---|
| La información está dispersa en archivos y el registro se consolida manualmente. | Aumenta el esfuerzo de búsqueda y dificulta mantener una referencia común. | Proponer un diccionario integrado con atributos lógicos, representaciones físicas y trazabilidad. | Decisión de diseño basada en la entrevista. |
| La autorización no siempre se puede localizar o verificar con facilidad. | Se dificulta responder consultas y sustentar revisiones. | El portal registra el estado y una referencia localizable de evidencia según los criterios que defina Jurídica. No se plantea como sistema integral de consentimiento. | Decisión; campos y criterios pendientes de Jurídica. |
| La responsabilidad del dato puede ser ambigua cuando intervienen varias áreas. | Una ficha sin responsable claro puede quedar incompleta o sin aprobación. | Mantener responsable y aprobador como metadatos explícitos; hacer visible el caso sin dueño en vez de asignarlo automáticamente. | Decisión de diseño. |
| La clasificación involucra al jefe del área y a Jurídica. | No corresponde inferir la clasificación solo por el nombre del atributo. | La clasificación se representa como una decisión humana con contexto, responsable y justificación. El portal registra, pero no decide automáticamente. | Decisión; reglas y casos dudosos pendientes de Jurídica. |
| Tecnología aporta tipo, longitud, nulabilidad y ubicación técnica cuando se solicita. | Hay dependencia de las áreas técnicas y la disponibilidad de extracción. | El MVP admite carga manual o asistida de metadatos; no presume API ni conexión directa a fuentes. | Decisión de diseño; disponibilidad por sistema pendiente. |
| Un atributo puede tener nombres físicos distintos, por ejemplo `cedula` y `nit_cc`. | La coincidencia o diferencia de nombres no basta para identificar equivalencia. | Separar el atributo lógico de sus representaciones físicas y mantener un mapeo revisable por fuente. | Decisión de diseño; equivalencias concretas deben validarse. |
| El catálogo de términos está separado y “Cliente” puede tener significados distintos entre Comercial y Cartera. | Un glosario único sin contexto puede mezclar conceptos de negocio. | Mantener términos y definiciones por contexto y asociarlos a atributos mediante referencias controladas. | Decisión de diseño. |
| Jurídica lidera el trámite de solicitudes de titulares y la relación con la SIC/RNBD. | El portal no debe asumir una función legal que la entrevista atribuye a Jurídica. | El MVP apoya la búsqueda de atributos y fuentes; Jurídica conserva la decisión y respuesta del caso. No se modela envío automático a SIC/RNBD. | Decisión de alcance; detalles operativos por confirmar. |
| Seguridad pertenece a Tecnología y actualmente aprovecha poco las clasificaciones. | La transferencia de clasificación a controles técnicos no puede presentarse como operación consolidada. | Mostrarla como brecha o colaboración objetivo, no como integración implementada. | Hallazgo reportado; proceso de mejora pendiente. |
| La retención no está definida en la conversación. | No hay base para automatizar conservación o eliminación. | Permitir documentar el estado o la política cuando se defina, sin ejecutar borrado automático en fuentes. | Decisión de alcance; política pendiente. |

## 4. Interpretación para el diseño de vistas

### V1 — Motivación

La motivación se centra en reducir la dispersión y mejorar la trazabilidad, la asignación de responsables y la localización de evidencia. Las metas numéricas mencionadas en la conversación se tratan como expectativas que requieren ratificación, no como compromisos del proyecto.

### V2 — Mapa de capacidades

El mapa organiza capacidades por grupos y por su naturaleza estratégica, misional o de apoyo. La entrevista ayuda a priorizar las capacidades relacionadas con gobierno, gestión de información, apoyo jurídico y tecnología. Las relaciones de impacto deben tener una justificación; no se deben convertir en conectores ArchiMate solo para llenar el mapa.

### V3 y V4 — Proceso y servicios

Las vistas deben diferenciar la operación manual actual de la aplicación objetivo. La extracción técnica puede variar de orden, y la revisión anual es una rutina aparte. La aplicación apoya registro, consulta, importación y trazabilidad, pero no sustituye la aprobación de las áreas ni las decisiones de Jurídica.

### V5 y V6 — Dominios y agregados

El diseño delimita el Diccionario de Datos como núcleo del inventario lógico, metadatos y clasificación; el Catálogo conserva su lenguaje y ciclo de aprobación; Integración Técnica normaliza y relaciona metadatos físicos. La gestión completa de solicitudes de titulares queda fuera del MVP. Los agregados deben proteger invariantes sin absorber procesos de Jurídica o tecnología que excedan el contexto.

### V7 y V8 — Lenguaje y contextos

El glosario debe diferenciar atributo lógico, representación física y metadatos. Los términos ambiguos se registran por contexto. El mapa de contextos debe representar intercambios humanos actuales y distinguirlos de patrones de integración futuros; los sistemas fuente y SIC/RNBD no se deben mostrar como APIs del portal sin evidencia.

### V9 a V11 — Integración, trazabilidad y canvas

La interoperabilidad actual es principalmente manual; cualquier adaptador o servicio automatizado es una propuesta objetivo hasta validar la capacidad técnica. La trazabilidad vertical solo debe usar relaciones semánticamente válidas y presentes o justificadas en el modelo. El canvas resume propósito, clasificación, roles, entradas, salidas, lenguaje, decisiones, supuestos, métricas y preguntas abiertas del Diccionario de Datos.

## 5. Supuestos y datos que no se deben presentar como hechos

La propuesta del proyecto marca como supuestos o pendientes varios datos de contexto: ciudades, cantidades de empleados y registros, cobertura actual de responsables/clasificación, tiempos objetivo, algunos canales informales, proveedores, detalles de nube, ciertos sistemas y conexiones entre ellos. La entrevista también contiene aspectos por verificar sobre disponibilidad de fuentes y acceso técnico.

Por tanto:

- No se presentan cifras hipotéticas como línea base confirmada o KPI aprobado.
- No se afirma que todas las fuentes tengan API, exportación automática o acceso directo.
- No se representa escritura del Portal en sistemas operativos.
- No se afirma ubicación internacional de datos sin confirmación de Jurídica.
- No se trata el registro de una referencia de autorización como prueba automática de suficiencia legal.
- No se modela la actualización del RNBD como integración automática del Portal.

## 6. Preguntas pendientes de validación

1. ¿Qué campos y granularidad de evidencia de autorización debe registrar el portal según Jurídica?
2. ¿Qué sistemas y tablas pueden entregar metadatos, con qué formato y bajo qué autorización?
3. ¿Quién resuelve los atributos compartidos entre áreas cuando no hay un responsable único?
4. ¿Qué atributos y áreas forman la primera población del MVP y qué indicadores aprueba el equipo?
5. ¿Qué términos de negocio requieren definiciones diferentes por contexto y quién los aprueba?
6. ¿Qué regla de conservación se aplicará al historial y a las referencias de evidencia?

## 7. Cierre

La entrevista orienta un MVP centrado en el inventario/diccionario, la clasificación con decisión humana, el mapeo lógico-físico, el catálogo contextual de términos y la trazabilidad. La propuesta reduce el alcance donde no hay respaldo suficiente: no presupone automatización, APIs, control de consentimiento, ejecución de retención ni gestión integral de casos de titulares. Las decisiones legales, los supuestos técnicos y la prioridad final de indicadores deben validarse antes de presentar el diseño como línea base aprobada.

## Fuente y trazabilidad

Este documento sintetiza la sección de entrevista, decisiones generales y trazabilidad de la propuesta integrada del proyecto. La conversación de entrevista exportada y el guion original deben incorporarse en esta carpeta para que cada hallazgo pueda cotejarse con la fuente primaria del ejercicio.

- [Propuesta de análisis de vistas](../Propuesta_analisis_vistas_ArchiMate_mejorada.md)
- [Alcance revisado](../Alcance_Gobierno_Datos_revisado.md)
