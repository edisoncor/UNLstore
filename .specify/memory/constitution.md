<!--
Sync Impact Report
- Versión: 1.0.0 → 1.1.0 (MINOR: ampliación de principios y stack aprobado por fase).
- Principios ampliados: I (SDD y convergencia), II (stack y arquitectura modular),
  III (BPMN, ADR y coherencia de modelos), V (revisión humana y uso responsable de IA),
  VI (autorización expresa para CI/CD).
- Principios añadidos: VII–XVII (SOLID, API, contrato universal, persistencia,
  seguridad, publicaciones, pruebas, errores, GitFlow, DevOps y observabilidad/rendimiento).
- Secciones añadidas: contexto y fuentes, stack tecnológico por fase, control de cambios.
- Secciones eliminadas: ninguna. Se resuelve TODO(APPROVED_BASELINE) con las
  instrucciones del responsable; las restricciones anteriores permanecen vigentes.
- ⚠ Pendiente: .specify/templates/plan-template.md (stack, controles y autorización CI/CD).
- ⚠ Pendiente: .specify/templates/spec-template.md (contrato, calidad y documentación).
- ⚠ Pendiente: .specify/templates/tasks-template.md (pruebas obligatorias aplicables,
  documentación, convergencia y autorización CI/CD; el texto genérico de pruebas opcionales
  no prevalece sobre esta constitución).
- Las plantillas permanecen intactas por el alcance autorizado: solo la constitución.
- .specify/templates/commands/ no existe. README.md y AGENTS.md remiten a un plan
  actual no localizado. No se ejecutaron hooks Git ni comandos del flujo de desarrollo.
- Fuentes: adjuntos del responsable, aclaración del stack por fase y documentos
  enumerados en «Contexto y fuentes». Guía PDF revisada en sus distintas secciones,
  incluidas las posteriores a arquitectura: API, datos, seguridad, calidad,
  operación, C4, GitFlow, Quarto, BPMN y SDD.
- Pendientes: fecha de ratificación original; versiones de dependencias y herramientas
  auxiliares; decisión condicional sobre Flutter; preguntas de negocio existentes.
- Converge no aparece entre las habilidades disponibles; se exige su resultado de
  verificación sin instalar ni simular un comando ausente.
-->


# Constitución de UNL Store

## Contexto y fuentes

UNL Store es una plataforma pública de distribución de productos tecnológicos de la
Carrera de Computación de la Universidad Nacional de Loja, provenientes de proyectos
académicos, de investigación y de vinculación con la sociedad. Admite aplicaciones web,
móviles y de escritorio, bibliotecas y componentes, modelos y soluciones de IA y recursos
tecnológicos adicionales. La distribución comprende archivos y enlaces externos, con
catálogo público y aprobación administrativa de publicaciones.

Esta constitución es única y transversal a F1, F2 y F3. Sus fuentes del proyecto son
`docs/01-proyecto/descripcion-proyecto.md`, `docs/02-analisis/identificacion-actores.md`,
`docs/02-analisis/mapa-actores.md`, `docs/02-analisis/fundamentos-sdd.md`,
`docs/02-analisis/preguntas-clarificacion.md` y `docs/03-requisitos/requisitos-iniciales.md`.
Las preguntas abiertas de esos documentos conservan ese estado salvo decisión expresa.

La referencia didáctica es
`references/backend/Guia_Didactica_Arquitectura_Backend_SOLID.pdf`, compilación de guías
sobre arquitectura, API, datos, seguridad, reglas de negocio, errores, pruebas,
documentación, observabilidad, rendimiento, DevOps, operación, codificación, contrato
universal, integración, C4, GitFlow, Quarto, BPMN y SDD/Spec Kit. Las referencias a guías
en cada principio identifican la justificación; sus ejemplos académicos no son requisitos
funcionales de UNL Store. Las instrucciones expresas del responsable prevalecen sobre
los ejemplos de herramientas y automatización de las guías.

## Principios fundamentales

### I. Desarrollo guiado por especificaciones y trazabilidad

UNL Store DEBE desarrollarse mediante Spec-Driven Development (SDD) con GitHub Spec Kit.
Las especificaciones, los planes y las tareas DEBEN preceder a la implementación que
regulan. Cada cambio DEBE poder relacionarse con sus requisitos, tareas, decisiones
arquitectónicas y evidencia de verificación. Las propuestas y asuntos pendientes DEBEN
distinguirse de las decisiones aprobadas; un documento de estudio o análisis no constituye
por sí solo una aprobación arquitectónica.

El flujo DEBE comprender constitution, specify, clarify, plan, tasks, implement y converge,
con sintaxis ajustada a la integración instalada. Se DEBEN distinguir problema, necesidad,
requisito y solución técnica, definir historias, reglas y criterios de aceptación comprobables
y resolver ambigüedades críticas antes de planificar. La convergencia DEBE comparar código,
especificaciones y pruebas, registrar brechas y verificar las correcciones. Si el comando
converge no está disponible, se DEBE registrar esa ausencia y realizar la comparación
con evidencia; no se DEBE fingir su ejecución ni instalarlo sin autorización.

Justificación y comprobación: guías 20 y 21 (SDD y Spec Kit); revisión humana de artefactos
y matriz requisito–diseño–tarea–código–prueba antes de aceptar un incremento.

### II. Arquitectura y evolución en tres fases

El proyecto DEBE conservar sus decisiones de arquitectura y stack previamente aprobadas.
Esta constitución no autoriza sustituirlas ni deducir aprobaciones a partir de ejemplos
incluidos en plantillas o materiales didácticos.

El desarrollo DEBE respetar tres fases: 1) Backend, 2) Frontend web y 3) Aplicación móvil.
Únicamente la fase 1: Backend está activa. Las fases posteriores requieren autorización
expresa del responsable del proyecto. Los clientes web y móvil DEBEN consumir los servicios
y contratos del backend y preservar sus reglas de negocio comunes. Admitir aplicaciones
móviles como productos del catálogo no activa el desarrollo del cliente móvil.

La arquitectura DEBE separar presentación/API, aplicación/casos de uso, dominio/reglas
de negocio e infraestructura/persistencia, con módulos por capacidades de negocio, alta
cohesión y bajo acoplamiento. El dominio NO DEBE depender de Django, DRF, HTTP ni del ORM;
los adaptadores de infraestructura DEBEN implementar las dependencias que requieran los
casos de uso. Las reglas centrales NO DEBEN quedar dispersas en vistas o serializers.
El plan DEBE justificar el monolito modular como punto de partida recomendado o documentar
por qué otra organización es necesaria, sin agregar capas ni servicios sin utilidad.
F1 DEBE ser autónoma y verificable sin clientes; F2 y F3 DEBEN preservar compatibilidad
con los contratos existentes y evitar duplicar las reglas centrales. Cada incremento
DEBE incluir documentación y pruebas.

Justificación y comprobación: guías de arquitectura, reglas de negocio e integración
(01, 05 y 15); revisar límites, dirección de dependencias y pruebas del dominio aislado.

### III. Modelado arquitectónico mediante Diagram as Code

Cuando la complejidad del sistema o las necesidades de análisis, comunicación o documentación
lo justifiquen, el modelo arquitectónico C4 DEBE construirse y mantenerse mediante Diagram as
Code. La selección de diagramas, o la decisión de no producirlos, DEBE justificarse en el plan.

- Se DEBE preferir Structurizr DSL para los niveles C4 que soporte. Cualquier alternativa
  DEBE justificarse en la decisión arquitectónica correspondiente.
- Se DEBE utilizar PlantUML cuando se necesiten diagramas UML o detalles de implementación
  complementarios.
- Se DEBEN considerar los cuatro niveles C4: contexto del sistema, contenedores, componentes
  y código; para este último se utilizarán diagramas UML de clases cuando corresponda.
- Solo se DEBEN generar los niveles y diagramas necesarios según el alcance y complejidad.
  Se DEBEN evitar diagramas excesivamente complejos o sin utilidad técnica identificable.
- Los archivos fuente DEBEN residir en el repositorio y versionarse mediante Git, en formatos
  textuales reproducibles e independientes del agente de IA utilizado. Una imagen exportada
  no sustituye el código fuente del diagrama.
- Los nombres DEBEN ser coherentes con el dominio y las especificaciones. Los diagramas
  DEBEN mantenerse sincronizados con las decisiones arquitectónicas aprobadas y resultar
  comprensibles para desarrolladores humanos y los distintos agentes de IA.
- Los diagramas pertinentes DEBEN incorporarse a la documentación técnica generada con Quarto.

Los diagramas DEBEN declarar límites claros y relaciones dirigidas con verbos, usar nombres
significativos y actualizarse cuando cambie la arquitectura. Se DEBE utilizar UML para dominio
y código, BPMN para procesos de negocio y ADR para decisiones arquitectónicas cuando aporten
valor al alcance. Los modelos DEBEN concordar con OpenAPI, requisitos e implementación,
sin generar vistas innecesarias. Los ADR DEBEN registrar contexto, alternativas, decisión,
estado y consecuencias.

Justificación y comprobación: guías 08, 16 y 19; revisión de coherencia entre niveles C4,
procesos, contratos y decisiones, conservando sus fuentes versionadas.

### IV. Documentación técnica y de usuario mediante Quarto

Quarto es la herramienta oficial para generar la documentación técnica y de usuario de
UNL Store. La documentación DEBE mantenerse progresivamente durante el desarrollo y ser
un entregable obligatorio, completo, coherente y revisado al cierre de cada una de las tres
fases. No se DEBE reservar su elaboración exclusivamente para el final.

La documentación técnica DEBE incluir los siguientes contenidos cuando sean aplicables
al alcance de la fase; no se DEBEN agregar apartados irrelevantes:

- Descripción general, alcance y requisitos funcionales y no funcionales implementados.
- Arquitectura, decisiones de diseño y diagramas C4 y UML pertinentes.
- Tecnologías, dependencias, estructura del proyecto y organización del código.
- Modelo de dominio, modelo de datos, especificación y contratos de API.
- Reglas de negocio, validaciones, seguridad, autenticación y autorización.
- Configuración de ambientes, instalación, ejecución y gestión de migraciones.
- Estrategia y resultados verificables de pruebas.
- Consideraciones de rendimiento y mantenibilidad.
- Procedimientos de operación y resolución de problemas.
- Limitaciones conocidas, trabajo pendiente y referencias a especificaciones, tareas
  y decisiones arquitectónicas.

La documentación de usuario DEBE emplear lenguaje claro, organizado y orientado a las personas
que utilizarán el sistema. DEBE corresponder exclusivamente a funcionalidades implementadas
y verificadas e incluir, según corresponda:

- Presentación, propósito, tipos de usuarios, roles y requisitos de acceso y uso.
- Primeros pasos, funcionalidades disponibles y procedimientos paso a paso de las
  operaciones principales.
- Capturas o ilustraciones pertinentes cuando exista una interfaz.
- Explicación de formularios, validaciones y mensajes.
- Recomendaciones de seguridad, preguntas frecuentes, resolución de problemas comunes
  y glosario de términos.

En la fase 1, la documentación de uso DEBE dirigirse a consumidores técnicos de la API e
incluir endpoints, autenticación, ejemplos de solicitudes y respuestas, errores y flujos
principales. No se DEBEN inventar pantallas ni procedimientos de interfaces web o móviles
que todavía no existan.

Los archivos fuente DEBEN mantenerse en formatos compatibles con Quarto, especialmente
`.qmd`, organizarse por fase y tipo de documentación y versionarse mediante Git. Se DEBE
permitir generar documentación navegable en HTML y contemplar exportaciones a PDF cuando
se requieran. Se DEBEN integrar los diagramas de Diagram as Code y mantener ejemplos,
comandos y capturas consistentes con la implementación. Se DEBEN evitar duplicaciones y
contradicciones e incorporar navegación, índice, referencias y enlaces internos cuando
correspondan.

Justificación y comprobación: guías 08 y 18; fuentes compartidas y entregables revisados
mediante el procedimiento obligatorio de cierre de fase.

### V. Interoperabilidad entre agentes de inteligencia artificial

Las especificaciones, la documentación y los archivos fuente de diagramas son recursos
compartidos del proyecto, independientes del proveedor de inteligencia artificial. DEBEN
poder mantenerse desde Codex, Antigravity, OpenCode, Copilot u otros agentes.

Antes de modificar arquitectura, API o funcionalidades, los agentes DEBEN consultar las
especificaciones y la documentación existentes. No se DEBEN crear sistemas paralelos de
documentación por agente. Los cambios DEBEN conservar nombres, contratos y trazabilidad
comunes para permitir la continuidad entre personas y herramientas.

Los agentes DEBEN documentar las fuentes y el uso de IA, mantener README, especificaciones
y ADR pertinentes y registrar los cambios asistidos. Las decisiones generadas con IA
DEBEN someterse a revisión humana. NO DEBEN inventarse pruebas ejecutadas, resultados,
aprobaciones ni funcionalidades. La documentación DEBE corresponder a la implementación.

Justificación y comprobación: guías 13, 18, 20 y 21; revisión humana, historial trazable
y evidencias reproducibles de los resultados declarados.

### VI. Autorización y alcance controlado

Las restricciones de autorización previamente aprobadas DEBEN conservarse. Una actualización
normativa no autoriza por sí misma instalar herramientas, modificar la implementación,
generar diagramas o documentación, activar pipelines CI/CD ni ejecutar tareas de desarrollo.
Cada actividad DEBE corresponder a una tarea autorizada y respetar la fase activa.

Esta enmienda autoriza exclusivamente editar la constitución. No se DEBEN instalar
Quarto, Structurizr, PlantUML ni otras dependencias; tampoco generar diagramas, construir
documentación, ejecutar comandos operativos del desarrollo ni activar pipelines como
consecuencia de esta actualización. La lectura y edición necesarias para esta enmienda
no habilitan esas actividades.

CI/CD forma parte del proyecto, pero NO DEBE ejecutarse automáticamente. Solo una solicitud
expresa del responsable autoriza su ejecución. Los agentes NO DEBEN disparar pipelines
manualmente ni mediante push, PR, etiquetas u otras acciones con disparadores automáticos
sin esa solicitud. Las configuraciones futuras DEBEN preservar este control de ejecución.
Las verificaciones obligatorias pendientes NO DEBEN declararse aprobadas ni omitirse para
integrar cambios: DEBE obtenerse la solicitud de ejecución correspondiente.

Justificación y comprobación: control de alcance exigido por el responsable; revisar
la autorización antes de cualquier operación que ejecute CI/CD o active otra fase.

### VII. SOLID y prácticas de codificación

El diseño DEBE aplicar SRP (responsabilidad única), OCP (extensiones sin alterar
repetidamente lógica estable), LSP (sustitución preservando garantías), ISP (interfaces
acotadas a consumidores) y DIP (dependencias hacia abstracciones del dominio).
Su aplicación DEBE justificarse por responsabilidades y cambios reales; NO DEBEN crearse
clases, interfaces ni capas sin necesidad. El código DEBE usar nombres del dominio,
funciones con propósito reconocible y convenciones de formato verificables. Se DEBEN
revisar duplicaciones y dependencias circulares y documentar deuda técnica con contexto.

Justificación y comprobación: guías 01 y 13; revisión de responsabilidades, contratos de
sustitución, dependencias y análisis estático definido en el plan.

### VIII. Diseño y estandarización de API

Las API DEBEN diseñar recursos HTTP consistentes, documentar contratos explícitos y
versionados en OpenAPI y respetar la semántica de métodos y códigos HTTP. DEBEN especificar
paginación, búsqueda, filtros y ordenamiento aplicables, límites, validaciones y errores.
Los cambios DEBEN evaluar compatibilidad, documentar deprecaciones y conservar pruebas
de contrato para web y móvil. Idempotencia, caché y control de concurrencia HTTP DEBEN
aplicarse cuando el caso lo requiera. Las solicitudes DEBEN ser trazables.
HTTP QUERY solo DEBE adoptarse con justificación y compatibilidad comprobada de clientes,
framework, proxies, servidor y herramientas; esta constitución no ordena incorporarlo.

Justificación y comprobación: guía 02 y guía 08; contrastar OpenAPI, respuestas reales,
compatibilidad y pruebas del contrato sin imponer versiones de herramientas no aprobadas.

### IX. Contrato universal de respuestas JSON

Las representaciones JSON administradas por el backend DEBEN incluir `success`, `message`,
`data`, `errors` y `meta`, con tipos estables documentados en OpenAPI:

- En éxito, `success` DEBE ser `true`, `errors` DEBE ser `null` y `data` DEBE contener
  el resultado definido por el contrato.
- En error, `success` DEBE ser `false`, `data` DEBE ser `null` y `errors` DEBE incluir
  un código interno estable y detalles estructurados seguros. `message` DEBE ser texto.
- El código HTTP DEBE concordar con el resultado; NO DEBE ocultarse un error bajo HTTP 200.
- `meta` DEBE incluir `request_id`, `timestamp` ISO 8601 en UTC y `version` de la API.
  La paginación DEBE residir en `meta`, con esquema documentado y consistente.
- Las respuestas 204, 304 y HEAD NO DEBEN tener cuerpo. Descargas binarias, streaming y
  redirecciones DEBEN respetar su protocolo sin forzar este envoltorio JSON. Los clientes
  DEBEN contemplar fallos de infraestructura anteriores al procesamiento de la API.

Justificación y comprobación: guía 14; pruebas de contrato de éxito, error, paginación,
correlación y excepciones HTTP para consumo uniforme por los distintos clientes.

### X. Persistencia e integridad

La persistencia DEBE garantizar integridad referencial, unicidad y transacciones según
las reglas aprobadas. Los cambios concurrentes DEBEN protegerse frente a actualizaciones
perdidas y transiciones inconsistentes. Las migraciones DEBEN revisarse y tener estrategia
de reversión cuando sea viable; si no lo es, DEBE documentarse recuperación alternativa.
El dominio DEBE mantenerse separado del almacenamiento. Se DEBEN definir respaldos y
comprobar su restauración antes de operar producción.

SQLite DEBE utilizarse en desarrollo. PostgreSQL es el motor de producción; el cambio de
entorno, la migración y su puesta en servicio DEBEN esperar la indicación expresa del
responsable. Las diferencias de restricciones, transacciones y concurrencia entre motores
DEBEN documentarse. Las pruebas con SQLite NO DEBEN presentarse como evidencia suficiente
de garantías específicas de PostgreSQL; esas comprobaciones DEBEN realizarse en un entorno
PostgreSQL autorizado antes de aprobar producción.

Justificación y comprobación: guías 03, 05, 07 y 12, ajustadas al stack aprobado; pruebas
de restricciones, migraciones, concurrencia aplicable y restauración con resultados registrados.

### XI. Seguridad y privacidad

El sistema DEBE autenticar las operaciones protegidas y autorizar por rol y recurso,
validar entradas y aplicar mínimo privilegio. DEBE proteger archivos no publicados,
validar enlaces externos y revisar los archivos antes de distribuirlos públicamente.
Las credenciales y secretos NO DEBEN incluirse en código, documentación pública ni logs.
Se DEBE utilizar HTTPS en las comunicaciones que lo requieran, proteger datos personales,
auditar acciones administrativas y gestionar errores sin revelar información sensible.
La revisión DEBE contemplar riesgos OWASP pertinentes y dejar evidencia de controles y
pruebas; el mecanismo concreto de identidad DEBE resolverse en la planificación autorizada.

Justificación y comprobación: guía 04; matriz de permisos, pruebas negativas por objeto,
validación de archivos/enlaces y revisión de secretos y exposición de datos.

### XII. Gobernanza de productos y publicaciones

Las especificaciones DEBEN identificar responsables, procedencia, condiciones de uso,
licenciamiento y versionado de productos. La distribución pública DEBE requerir aprobación
administrativa y comprobar integridad de archivos. Se DEBE conservar el historial de
solicitudes, decisiones y retiros con sus responsables y motivos. La separación entre
solicitud y aprobación DEBE responder a una política explícita; los conflictos de interés
y suplencias abiertos NO DEBEN tratarse como resueltos.
Los retiros DEBEN ser controlados y trazables. Las descargas de archivos internos DEBEN
distinguirse de accesos a enlaces externos; un acceso externo NO DEBE declararse descarga
ni instalación completada por terceros.

Justificación y comprobación: documentos de proyecto y guías 05 y 12; revisión de estados,
autorizaciones, auditoría e invariantes con pruebas, sin inventar políticas institucionales.

### XIII. Calidad, pruebas y condición de terminado

Los incrementos DEBEN aportar pruebas automatizadas unitarias, de integración, API/contrato,
autorización/seguridad, reglas de negocio y regresión según el comportamiento afectado.
Se DEBEN incluir pruebas de concurrencia cuando existan recursos o estados compartidos
y de rendimiento frente a objetivos medibles cuando corresponda. Una categoría no aplicable
DEBE justificarse en el plan; NO DEBE omitirse una prueba necesaria por conveniencia.
NO DEBEN imponerse porcentajes de cobertura sin decisión aprobada.

Un incremento solo DEBE declararse terminado con criterios de aceptación satisfechos,
evidencia de pruebas pertinentes, documentación y contratos actualizados, brechas críticas
de convergencia resueltas y revisión humana. Se DEBEN registrar pruebas no ejecutadas,
sus causas y los límites de lo verificado. El cierre de fase requiere además todos los
entregables y aprobaciones del procedimiento documental.

Justificación y comprobación: guías 07, 15, 20 y 21; matriz requisito–prueba y resultados
reproducibles. CI/CD sigue sujeto a solicitud expresa; ninguna evidencia se inventa.

### XIV. Gestión coherente de errores

El sistema DEBE distinguir errores de validación, negocio, autenticación/autorización e
infraestructura, traducirlos a códigos HTTP y códigos internos consistentes y conservar
identificadores de correlación. El diagnóstico DEBE registrarse de forma segura; los
mensajes públicos NO DEBEN revelar SQL, trazas, rutas internas, secretos ni datos personales
innecesarios. El dominio NO DEBE depender de excepciones HTTP; su traducción corresponde
al adaptador API y DEBE respetar el contrato universal.

Justificación y comprobación: guía 06; catálogo de errores y pruebas de respuestas,
correlación y ausencia de información sensible.

### XV. Versionamiento y colaboración con GitFlow

El proyecto DEBE utilizar Git con `main` para versiones publicadas, `develop` para
integración, `feature/*` para funcionalidades, `release/*` para estabilización y `hotfix/*`
para correcciones urgentes de producción. Las integraciones DEBEN pasar por Pull Requests
con revisión y verificaciones obligatorias satisfactorias; las ramas principales DEBEN
protegerse conforme a esta política. Los commits DEBEN ser claros y trazables, y las
publicaciones DEBEN tener etiquetas y registro de versiones. Los arreglos de release y
hotfix DEBEN incorporarse a las ramas correspondientes para evitar regresiones.
NO DEBEN integrarse cambios con verificaciones obligatorias fallidas o pendientes.

Justificación y comprobación: guías 17 y 22; revisar origen/destino, PR, evidencias y etiquetas.
Las acciones que disparen CI/CD requieren la solicitud expresa descrita en el principio VI.

### XVI. DevOps y automatización controlada

El proyecto DEBE contemplar CI/CD, configuración separada por entorno, entornos y
construcciones reproducibles, gestión segura de dependencias, análisis estático y pruebas
automatizadas. Las herramientas adicionales y sus versiones DEBEN justificarse en el plan;
los contenedores solo DEBEN incorporarse con necesidad demostrada. La entrega y el despliegue
DEBEN ser controlados, con estrategia de reversión y recuperación verificable.
La existencia de CI/CD NO autoriza ejecuciones automáticas: solo se DEBE ejecutar cuando
el responsable lo solicite expresamente, incluso para verificaciones o documentación.

Justificación y comprobación: guías 11 y 15, con la restricción expresa del responsable;
revisión de configuración, dependencias, reproducibilidad, permisos y plan de rollback.

### XVII. Observabilidad, operación, rendimiento y escalabilidad

El sistema DEBE disponer de logs estructurados, métricas, correlación por `request_id`,
monitoreo de errores y rendimiento, verificaciones de salud y trazas cuando correspondan.
Se DEBEN documentar respuesta a incidentes, mantenimiento, respaldos verificables,
restauración y recuperación. Los registros NO DEBEN exponer secretos ni información
personal innecesaria.

El plan DEBE definir objetivos medibles de rendimiento y carga. Las consultas DEBEN tener
paginación y límites aplicables; se DEBEN controlar consultas innecesarias y optimizar con
mediciones comparables. Caché, procesamiento asíncrono de operaciones prolongadas y cambios
de escala DEBEN justificarse por necesidades reales, con preservación de permisos y
consistencia. NO DEBEN imponerse tecnologías ni umbrales arbitrarios.

Justificación y comprobación: guías 09, 10 y 12; mediciones, pruebas de salud y recuperación,
procedimientos operativos y comparación antes/después para cambios de rendimiento.

## Stack tecnológico por fase

| Fase | Tecnologías aprobadas | Alcance y restricciones |
|---|---|---|
| F1 — Backend y API (activa) | Python, Django, Django REST Framework (DRF); SQLite en desarrollo; PostgreSQL en producción | Backend autónomo. Mantener SQLite hasta que el responsable indique cuándo preparar y efectuar el paso a PostgreSQL. |
| F2 — Frontend web (inactiva) | Angular | Consumir la API de F1. Su stack aprobado no autoriza iniciar la fase. |
| F3 — Aplicación móvil (inactiva) | Kotlin para aplicación nativa; Flutter si se decide desarrollar una aplicación híbrida | Flutter es una alternativa condicional, no una obligación de construir dos clientes. Su adopción y el inicio de F3 requieren decisión expresa. |
| Transversal | Git, GitFlow, GitHub Spec Kit, Quarto; Structurizr DSL y PlantUML según los principios de modelado; CI/CD | Versiones, herramientas auxiliares y proveedor de CI/CD se definirán en el plan. CI/CD solo se ejecuta a solicitud expresa. |

El plan DEBE fijar versiones compatibles y justificar dependencias auxiliares sin sustituir
este stack. La selección de tecnologías NO autoriza su instalación ni configuración
inmediata, el cambio de motor de datos ni la activación de fases futuras.

## Restricciones y continuidad de las decisiones aprobadas

Esta constitución no elimina ni contradice decisiones anteriores aprobadas. Las fuentes
recuperadas de esas decisiones DEBEN incorporarse con referencia verificable mediante el
procedimiento de enmienda; no se DEBEN reconstruir como hechos a partir de suposiciones.
Si una tarea depende de una decisión no disponible, se DEBE solicitar su fuente al
responsable antes de ejecutar esa parte de la tarea.

El catálogo público y la aprobación administrativa previa de publicaciones se conservan
como acuerdos identificados en la documentación existente. La consulta pública no exige
por sí misma autenticación; las operaciones de gestión DEBEN respetar los permisos aprobados.
No se DEBEN confundir propuestas de requisitos con reglas institucionales confirmadas.

## Desarrollo progresivo y cierre documental de fase

Las especificaciones, planes y tareas DEBEN identificar el trabajo documental aplicable
y evaluar la conformidad con esta constitución. Antes del cierre de cada fase se DEBE:

1. Revisar la correspondencia entre implementación y especificaciones.
2. Actualizar los diagramas arquitectónicos pertinentes.
3. Completar la documentación técnica.
4. Completar la documentación de usuario correspondiente a la fase.
5. Verificar ejemplos y procedimientos contra la implementación.
6. Comprobar enlaces, referencias y archivos incorporados.
7. Generar los entregables mediante Quarto.
8. Comprobar que los documentos generados sean navegables, legibles y coherentes.
9. Identificar explícitamente limitaciones y funcionalidades pendientes.
10. Solicitar y obtener la aprobación del responsable del proyecto para cerrar la fase.

No se DEBE declarar finalizada una fase con entregables documentales incompletos o sin
revisión y aprobación. La evidencia de las comprobaciones y de la aprobación DEBE quedar
registrada y vinculada a los entregables. El cierre de una fase no activa automáticamente
la siguiente.

## Gobernanza

Esta constitución rige las especificaciones, planes, tareas, implementación y documentación.
Cada revisión de esos artefactos DEBE comprobar su conformidad y registrar desviaciones;
una desviación no constituye una excepción aprobada. La constitución prevalece sobre
especificaciones, planes y tareas. El responsable del proyecto es la autoridad para revisar
su cumplimiento y aprobar enmiendas o excepciones. Una excepción DEBE registrar alcance,
motivo, riesgos, medidas compensatorias, vigencia y aprobación explícita; NO DEBE utilizarse
para omitir las restricciones expresas de autorización. Una modificación incompatible de
principios requiere enmienda MAJOR, no una excepción informal.

Las enmiendas DEBEN indicar motivo, alcance, impacto sobre decisiones anteriores, versión,
fecha y aprobación del responsable. DEBEN incluir un informe de sincronización que identifique
los artefactos revisados, actualizados y pendientes, y versionarse mediante Git cuando la
operación correspondiente esté autorizada. No se DEBE crear un commit automáticamente
como efecto de esta actualización.

El versionado DEBE seguir MAJOR.MINOR.PATCH: MAJOR para eliminaciones o redefiniciones
incompatibles de principios o gobernanza; MINOR para nuevos principios, secciones o
ampliaciones normativas; PATCH para aclaraciones sin cambio de significado. La versión
1.0.0 identifica la primera constitución concreta disponible en este repositorio y no
representa una reconstrucción de versiones anteriores desconocidas.

TODO(RATIFICATION_DATE): confirmar la fecha de adopción original con el responsable del
proyecto; la fecha de esta enmienda no se utiliza como sustituto de un dato desconocido.

## Control de cambios

| Versión | Fecha | Cambio y trazabilidad |
|---|---|---|
| 1.0.0 | 2026-10-15 | Sustitución autorizada de la plantilla por principios de Diagram as Code, Quarto, interoperabilidad y control de fases. |
| 1.1.0 | 2026-10-15 | Incorporación del segundo adjunto y aclaración expresa del responsable: stack por fase, SQLite en desarrollo, PostgreSQL al indicarlo, Kotlin/Flutter condicional y CI/CD solo a solicitud. Se amplían arquitectura, API, calidad, seguridad y gobernanza. |

**Version**: 1.1.0 | **Ratified**: TODO(RATIFICATION_DATE) | **Last Amended**: 2026-10-15
