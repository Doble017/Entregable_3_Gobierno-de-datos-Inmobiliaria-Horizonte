# Gobierno de datos en una inmobiliaria

## Propósito

Este repositorio reúne el análisis, el modelo ArchiMate y las evidencias del diseño de un Portal de Gobierno de Datos para el caso académico de una inmobiliaria. El portal busca centralizar el inventario de atributos, sus metadatos de negocio y técnicos, las definiciones del catálogo y la trazabilidad necesaria para apoyar a Gobierno de Datos y Jurídica.

El diseño distingue el proceso manual descrito en la entrevista académica de las funciones objetivo del portal. La aplicación apoya el inventario y la consulta; no reemplaza los sistemas fuente, no decide automáticamente la clasificación, no ejecuta tratamientos legales y no garantiza por sí sola el cumplimiento normativo.

> **Estado de la entrega:** este README es el índice del proyecto. Las imágenes, el archivo fuente ArchiMate y algunos materiales originales de entrevista deben incorporarse en las rutas indicadas. No se debe presentar una imagen o un modelo como entregado hasta guardarlo y revisarlo en el repositorio.

## Índice

- [Fase 0 — Entrevista y evidencia](#fase-0--entrevista-y-evidencia)
- [Fase 1 — Motivación, capacidades y proceso](#fase-1--motivación-capacidades-y-proceso)
- [Fase 2 — Servicios y dominios](#fase-2--servicios-y-dominios)
- [Fase 3 — Modelo táctico DDD](#fase-3--modelo-táctico-ddd)
- [Fase 4 — Lenguaje ubicuo y contextos](#fase-4--lenguaje-ubicuo-y-contextos)
- [Fase 5 — Interoperabilidad y trazabilidad](#fase-5--interoperabilidad-y-trazabilidad)
- [Fase 6 — Bounded Context Canvas](#fase-6--bounded-context-canvas)
- [Aportes del equipo](#aportes-del-equipo)
- [Estructura del repositorio](#estructura-del-repositorio)
- [Exportar vistas desde Archi](#exportar-vistas-desde-archi)
- [Fuentes del proyecto](#fuentes-del-proyecto)

## Fase 0 — Entrevista y evidencia

Esta fase organiza el guion, la instrucción de rol, la conversación de entrevista y la lectura de sus hallazgos. La conversación disponible corresponde a una **entrevista académica simulada**; sus respuestas son evidencia del ejercicio, mientras que los datos marcados como supuestos siguen pendientes de validación.

- [Análisis de hallazgos](entrevista/analisis_hallazgos.md)
- [Guion de entrevista — pendiente de incorporar](entrevista/guion_fase_0.pdf)
- [Instrucción de rol — pendiente de incorporar](entrevista/instruccion_rol.md)
- [Conversación exportada — pendiente de incorporar](entrevista/conversacion_marcela.pdf)
- [Enlace a la conversación de la entrevista](https://claude.ai/share/85893f5c-724d-4f99-b14b-b0f54fca4205)

## Fase 1 — Motivación, capacidades y proceso

### V1. Motivación del Portal de Gobierno de Datos

![V1 — Motivación](vistas/V1_motivacion.png)

**Análisis y decisiones.** La vista conecta los impulsores del caso —dispersión, dificultad para demostrar autorización y necesidad de localizar información— con metas, resultados y requisitos. La solución se formula como apoyo al gobierno y a la trazabilidad, no como garantía automática de cumplimiento. Las expectativas cuantitativas de cobertura se conservan como pendientes de ratificación.

### V2. Mapa de capacidades

![V2 — Mapa de capacidades](vistas/V2_mapa_capacidades.png)

**Análisis y decisiones.** El mapa conserva los grupos y sus capacidades, clasificadas como estratégicas, misionales o de apoyo. El portal se contrasta con las capacidades pertinentes para mostrar cobertura e impacto; no se crean capacidades duplicadas ni se dibujan relaciones solo para conectar visualmente todos los grupos.

### V3. Cadena de valor y proceso E2E

![V3 — Cadena de valor y proceso E2E](vistas/V3_cadena_valor_proceso_e2e.png)

**Análisis y decisiones.** La vista representa el proceso actual de forma manual y reactiva: aviso, levantamiento, revisión de negocio y Jurídica, solicitud de datos técnicos, consolidación y aprobación. La extracción técnica puede ocurrir en otro orden; la actualización anual del inventario se mantiene como ciclo distinto. El apoyo futuro del portal se separa del estado actual.

## Fase 2 — Servicios y dominios

### V4. Descomposición de servicios

![V4 — Descomposición de servicios](vistas/V4_descomposicion_servicios.png)

**Análisis y decisiones.** La descomposición sigue desde el proceso de negocio hasta servicios, funciones y componente de aplicación. El flujo a sistemas fuente se mantiene manual o asistido mientras no se confirme acceso técnico; no se presupone API ni escritura de regreso. La vista enviada por un integrante se debe revisar para corregir cruces y validar cada relación contra el modelo.

### V5. Dominios del producto

![V5 — Dominios](vistas/V5_dominios.png)

**Análisis y decisiones.** Se propone el Diccionario de Datos como núcleo del inventario lógico y sus metadatos; el Catálogo de Términos conserva un lenguaje y ciclo de aprobación propios; Integración Técnica apoya la normalización y el mapeo físico-lógico. Jurídica y la atención integral de solicitudes quedan fuera del MVP, aunque el portal apoya la localización de atributos y fuentes. La identidad, seguridad y plataforma se dejan como dependencia genérica sin proveedor confirmado.

## Fase 3 — Modelo táctico DDD

### V6. Agregados, comandos y eventos

![V6a — Agregado Atributo Lógico](vistas/V6a_agregado_atributo_logico.png)
![V6b — Agregado Representación Física](vistas/V6b_agregado_representacion_fisica.png)
![V6c — Agregado Término de Negocio](vistas/V6c_agregado_termino_negocio.png)

**Análisis y decisiones.** La rúbrica pide un diagrama por dominio. Se preparan V6a para el agregado Atributo Lógico, V6b para Representación Física e integración técnica y V6c para Término de Negocio. Cada diagrama debe identificar raíz, límite, conceptos, invariantes, comandos, eventos y proceso de aplicación. Los comandos se documentan como solicitudes que inician comportamiento; no se presentan como tipos nativos de elemento ArchiMate. Los eventos de aplicación aparecen después de la aceptación y persistencia del comando.

- [Especificación de construcción V6a–V6c](Plan_construccion_vistas_Integrante_B.md#7-v6--agregados-comandos-y-eventos)

## Fase 4 — Lenguaje ubicuo y contextos

### V7. Lenguaje ubicuo

![V7 — Lenguaje ubicuo](vistas/V7_lenguaje_ubicuo.png)

**Análisis y decisiones.** El glosario diferencia atributo lógico, representación física y metadatos; registra término, definición, contexto y ejemplo. Los términos ambiguos —como “Cliente” en Comercial y Cartera— se muestran por contexto, evitando una definición única que oculte diferencias. Se usan elementos de representación y significado según la especificación de la vista.

### V8. Mapa de contextos

![V8 — Mapa de contextos](vistas/V8_mapa_contextos.png)

**Análisis y decisiones.** La vista delimita Diccionario, Catálogo e Integración Técnica y muestra a Jurídica, Tecnología, sistemas fuente y SIC/RNBD como colaboradores externos según el alcance. Los intercambios actuales se distinguen de los patrones objetivo. Customer-Supplier o Anti-Corruption Layer se incluyen solo cuando el flujo y la traducción estén justificados; no se asume una integración automática existente.

## Fase 5 — Interoperabilidad y trazabilidad

### V9. Interoperabilidad y anticorrupción

![V9 — Interoperabilidad y anticorrupción](vistas/V9_interoperabilidad_anticorrupcion.png)

**Análisis y decisiones.** La vista especifica participantes, datos, dirección y mecanismo de intercambio. La línea base es entrega manual de metadatos técnicos por Tecnología y coordinación humana con Jurídica. Un adaptador de traducción puede plantearse como objetivo, pero no se modela como componente actual hasta que exista evidencia.

### V10. Trazabilidad vertical

![V10 — Trazabilidad vertical](vistas/V10_trazabilidad_vertical.png)

**Análisis y decisiones.** La vista conecta motivación, resultado, curso de acción, capacidad, servicio y comportamiento de aplicación cuando la semántica y el modelo fuente respaldan cada vínculo. Las relaciones deben verificarse por tipo, dirección y existencia; una línea propuesta no cuenta como relación ya registrada.

## Fase 6 — Bounded Context Canvas

### V11. Canvas del contexto Diccionario de Datos

![V11 — Bounded Context Canvas](vistas/V11_bounded_context_canvas.png)

**Análisis y decisiones.** El canvas resume en una página propósito, clasificación estratégica, rol del contexto, lenguaje ubicuo, comunicación entrante y saliente, decisiones, supuestos, métricas de verificación y preguntas abiertas. Se usa el Diccionario de Datos como contexto principal porque concentra el inventario y la trazabilidad que responden al problema central descrito en la entrevista.

## Aportes del equipo

La tabla se debe completar con nombres y referencias reales del historial. En la revisión inicial de este repositorio no había commits; por eso no se atribuye trabajo verificable a integrantes hasta que el equipo registre sus cambios.

| Integrante | Aporte realizado | Evidencia en el repositorio | Commit(s) |
|---|---|---|---|
| Añadir una fila por integrante | Describir solo el trabajo efectivamente realizado | Rutas y archivos verificables | Hash y mensaje del commit |

**Regla de registro:** cada aporte debe corresponder a cambios que la persona realmente realizó. Revisar `git log --author="Nombre" --oneline` y confirmar que el commit incluye los archivos asociados; no asignar commits retroactivamente sin evidencia.

## Estructura del repositorio

```text
README.md
modelo/
  gobierno_datos.archimate       # archivo fuente editable de Archi
vistas/
  V1_motivacion.png
  V2_mapa_capacidades.png
  V3_cadena_valor_proceso_e2e.png
  V4_descomposicion_servicios.png
  V5_dominios.png
  V6a_agregado_atributo_logico.png
  V6b_agregado_representacion_fisica.png
  V6c_agregado_termino_negocio.png
  V7_lenguaje_ubicuo.png
  V8_mapa_contextos.png
  V9_interoperabilidad_anticorrupcion.png
  V10_trazabilidad_vertical.png
  V11_bounded_context_canvas.png
entrevista/
  guion_fase_0.pdf
  instruccion_rol.md
  conversacion_marcela.pdf
  analisis_hallazgos.md
decisiones/
  Propuesta_analisis_vistas_ArchiMate.md
  Plan_construccion_vistas_Integrante_B.md
```

V6 se exporta en tres imágenes separadas porque la rúbrica solicita un gráfico por dominio. Si el equipo usa nombres distintos, actualizar las rutas de las imágenes en este README.

## Exportar vistas desde Archi

### Guardar el modelo fuente `.archimate`

1. Abrir el modelo de trabajo en Archi.
2. Elegir **File → Save As…** y seleccionar la carpeta `modelo/` del repositorio.
3. Guardar con un nombre claro, por ejemplo `gobierno_datos.archimate`.
4. Cerrar y volver a abrir esa copia desde `modelo/` para confirmar que conserva el modelo y sus vistas.
5. Desde ese momento, trabajar sobre la copia del repositorio y usar **File → Save** con frecuencia.

`Save As…` guarda una copia del modelo con otro nombre. No confundirlo con exportar una imagen: el `.archimate` es el archivo editable con elementos, relaciones y vistas.

### Exportar imágenes de las vistas

1. Abrir el modelo `.archimate` en Archi y guardar los cambios.
2. En el árbol del modelo, abrir y seleccionar la **View** que se desea exportar.
3. Usar **File → Export → Export View As Image…**. También está disponible con clic derecho sobre la View seleccionada.
4. Elegir **PNG** para las imágenes que se insertarán en este README y seleccionar una escala legible. Para vistas grandes, exportar a 200 % o 300 % y comprobar que el texto se lea al abrir el archivo.
5. Guardar cada imagen dentro de `vistas/` con el nombre definido en la estructura anterior.
6. Para V6, exportar V6a, V6b y V6c como tres imágenes independientes.
7. Abrir las imágenes exportadas y revisar recortes, texto, conectores y legibilidad. Si la opción está deshabilitada, confirmar que la View esté abierta y seleccionada; esta exportación es para vistas ArchiMate, no para Canvas.
8. Guardar de nuevo el modelo editable en `modelo/` y verificar que abre desde esa carpeta.

Archi permite exportar vistas como BMP, JPG, PNG, PDF o SVG; para el README se recomienda PNG. [Guía oficial de Archi](https://www.archimatetool.com/downloads/archi/Archi%20User%20Guide.pdf).

## Fuentes del proyecto

- [Propuesta de análisis de vistas integrada](Propuesta_analisis_vistas_ArchiMate_mejorada.md)
- [Plan de construcción de vistas del Integrante B](Plan_construccion_vistas_Integrante_B.md)
- [Alcance revisado del Portal de Gobierno de Datos](Alcance_Gobierno_Datos_revisado.md)
- Enunciado y rúbrica del curso: incorporar el archivo original en la carpeta acordada por el equipo.
- Guion, instrucción de rol y conversación de entrevista: incorporar sus versiones fuente en `entrevista/`.

La propuesta de análisis es una base para construir y validar. El cumplimiento final se acredita con el modelo editable, las vistas exportadas, los materiales requeridos y la revisión de cada criterio de la rúbrica.
