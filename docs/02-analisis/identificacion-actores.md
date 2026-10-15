# UNL Store — Identificación y caracterización de actores

> **Documento:** ANA-UNLSTORE-001  
> **Versión:** 1.0 (borrador de análisis)  
> **Fecha:** 14 de octubre de 2026  
> **Institución:** Universidad Nacional de Loja (UNL)  
> **Unidad académica:** Carrera de Computación  
> **Estado:** Pendiente de revisión y validación  
> **Fase de referencia:** Fase 1 — Backend; considerado también para los clientes web y móvil

## 1. Propósito

Identificar a las personas, colectivos y sistemas que intervienen directa o indirectamente en **UNL Store**, describir sus intereses y las interacciones esperadas, y reconocer restricciones y dudas que deben aclararse antes de especificar comportamientos o diseñar la solución técnica.

Este documento desarrolla el análisis de actores de la actividad inicial del proyecto. La descripción general, el problema, el alcance y los acuerdos aprobados se encuentran en [Descripción del proyecto](../01-proyecto/descripcion-proyecto.md). El mapa gráfico detallado se conserva en [`mapa-actores.md`](mapa-actores.md) y las decisiones pendientes en [`preguntas-clarificacion.md`](preguntas-clarificacion.md), cuando se elaboren.

## 2. Contexto y acuerdos considerados

UNL Store será un catálogo **público** de productos tecnológicos de la Carrera de Computación, provenientes de proyectos **académicos, de investigación y de vinculación con la sociedad**. Admitirá aplicaciones web, móviles, de escritorio, bibliotecas y componentes, modelos y soluciones de IA y recursos tecnológicos adicionales. La distribución podrá realizarse mediante archivos y enlaces externos. La **aprobación de publicaciones corresponderá al administrador**.

El desarrollo se organizará en tres fases: **(1) backend**, **(2) frontend web** y **(3) aplicación móvil**. Identificar un actor no implica que deba contar con una pantalla o una cuenta propia en todas las fases.

## 3. Criterios para identificar y clasificar actores

Se considera **actor** a una persona, rol organizacional, colectivo o sistema externo que tiene un interés en UNL Store o intercambia información con él. Un actor no equivale automáticamente a una tabla de base de datos ni a un rol de autorización.

| Clasificación | Criterio aplicado |
|---|---|
| **Usuario principal** | Utiliza directamente capacidades que resuelven la necesidad central del sistema. |
| **Usuario secundario** | Participa en procesos de apoyo, seguimiento o coordinación, sin ser necesariamente el consumidor principal. |
| **Responsable o administrador** | Gestiona permisos, decisiones de publicación y operación autorizada. |
| **Actor externo** | Persona, equipo u órgano interesado cuya relación puede darse fuera de una cuenta operativa. |
| **Sistema o servicio relacionado** | Plataforma independiente con la que UNL Store intercambia o podría intercambiar información o recursos. |

**Estados del análisis:** **Confirmado** = surge de acuerdos previos; **Definido con detalle pendiente** = su función general está prevista pero faltan atribuciones o permisos; **Propuesto/condicional** = actor o integración por validar, no un requisito aprobado.

## 4. Inventario y clasificación de actores

| ID | Actor | Clasificación principal | Estado | Justificación |
|---|---|---|---|---|
| ACT-01 | Visitante del catálogo | Usuario principal | Confirmado | Explora productos y accede a recursos públicos sin autenticación. |
| ACT-02 | Desarrollador | Usuario principal | Confirmado | Registra productos y versiones y solicita publicación. |
| ACT-03 | Responsable de proyecto | Usuario secundario | Definido con detalle pendiente | Identifica procedencia y participantes; puede compartir permisos con el desarrollador. |
| ACT-04 | Administrador de UNL Store | Responsable o administrador | Confirmado | Revisa solicitudes, decide publicaciones y gestiona parámetros autorizados. |
| ACT-05 | Docente responsable | Actor externo institucional | Propuesto/condicional | Podría avalar procedencia o responsabilidad de proyectos académicos. |
| ACT-06 | Equipo de investigación o vinculación | Actor externo institucional | Propuesto/condicional | Origina productos y aporta antecedentes, titulares o autorizaciones. |
| ACT-07 | Autoridad de la Carrera | Actor externo institucional | Propuesto/condicional | Tiene interés en indicadores y visibilidad de resultados. |
| ACT-08 | Servicio de almacenamiento de archivos | Sistema o servicio relacionado | Función necesaria; proveedor pendiente | Conserva archivos distribuidos internamente, aunque puede formar parte de la infraestructura propia. |
| ACT-09 | Plataforma externa de distribución | Sistema o servicio relacionado | Confirmado como modalidad; proveedor variable | Aloja aplicaciones, repositorios o recursos referenciados por enlaces. |
| ACT-10 | Servicio externo/institucional de identidad | Sistema o servicio relacionado | Propuesto/condicional | Podría autenticar gestores si se adopta integración; no se ha aprobado proveedor. |

**Nota sobre el administrador:** la decisión de que aprueba las publicaciones está confirmada; la asignación de administradores, suplencias y tratamiento de solicitudes propias aún no están resueltos.

## 5. Caracterización detallada

### ACT-01 — Visitante del catálogo

- **Necesidad/interés:** descubrir y utilizar productos tecnológicos relevantes y confiablemente descritos.
- **Interacción esperada:** explorar, buscar, filtrar, consultar fichas y versiones, descargar archivos públicos y abrir enlaces externos autorizados.
- **Información consultada:** nombre, descripción, tipo, origen, responsables públicos, licencia/condiciones, compatibilidad, versiones y recursos de distribución.
- **Información proporcionada:** criterios de búsqueda y eventos de navegación o acceso que el sistema contabilice; no requiere identidad personal para el uso público.
- **Condiciones:** solo visualizar contenido publicado; no acceder a borradores ni recursos no aprobados; respetar condiciones de uso y advertencias del producto.
- **Fases:** F1, servicios de catálogo; F2, interfaz web; F3, experiencia móvil de consulta.

### ACT-02 — Desarrollador

- **Necesidad/interés:** presentar, difundir y mantener los productos de software de su responsabilidad.
- **Interacción esperada:** autenticarse; registrar y editar borradores; asociar proyectos; agregar versiones, archivos, enlaces y documentación; enviar solicitudes; consultar decisiones y observaciones.
- **Información proporcionada:** metadatos técnicos, materiales de difusión, procedencia, responsables, versiones, licencias, recursos y declaraciones requeridas para la publicación.
- **Información consultada:** estado de sus productos y solicitudes, observaciones del administrador, historial de versiones y estadísticas permitidas.
- **Condiciones:** cuenta y permisos autorizados; solo actuar sobre productos propios o asignados; completar datos obligatorios; no publicar directamente sin aprobación.
- **Fases:** F1, API y reglas de autorización; F2, interfaz de gestión; gestión móvil no incluida inicialmente.

### ACT-03 — Responsable de proyecto

- **Necesidad/interés:** mantener la correspondencia entre iniciativas, participantes y productos generados.
- **Interacción esperada:** registrar o validar la información de procedencia y asociar productos con proyectos, según las atribuciones que se confirmen.
- **Información proporcionada:** código/nombre del proyecto, categoría de origen (académico, investigación, vinculación), equipo y referencias de respaldo.
- **Información consultada:** productos relacionados y sus estados de publicación.
- **Condiciones:** debe verificarse si es un rol independiente, una responsabilidad del desarrollador o un perfil institucional; sus permisos están pendientes.
- **Fases:** F1 define las asociaciones; F2 ofrece operaciones autorizadas si se aprueban.

### ACT-04 — Administrador de UNL Store

- **Necesidad/interés:** garantizar que el catálogo contenga productos autorizados y mantener control y trazabilidad operativa.
- **Interacción esperada:** administrar usuarios y catálogos; revisar solicitudes; aprobar, observar o rechazar; publicar y retirar productos/versiones; consultar auditorías e indicadores.
- **Información proporcionada:** decisiones, motivos, observaciones, configuraciones y registros de administración.
- **Información consultada:** solicitudes, metadatos, archivos, enlaces, procedencia, historial y estadísticas.
- **Condiciones:** privilegios explícitos y acciones auditables; separación entre quien solicita y quien aprueba según la regla preliminar; procedimiento de sustitución o suplencia pendiente.
- **Fases:** F1 implementa permisos y procesos; F2 proporciona la interfaz administrativa; F3 no contempla administración completa inicialmente.

### ACT-05 — Docente responsable (potencial)

- **Necesidad/interés:** reconocer los resultados de actividades o proyectos académicos y, si se establece, respaldar su procedencia.
- **Interacción esperada:** validar información o avales por un procedimiento aún no determinado; no se presupone un módulo o rol propio.
- **Información proporcionada/consultada:** datos de asignatura o proyecto, vinculación de participantes, evidencias de procedencia y productos asociados.
- **Condiciones:** responsabilidad, necesidad de aval y permisos todavía por confirmar; no tiene atribución automática para aprobar publicaciones.

### ACT-06 — Equipo de investigación o vinculación (potencial)

- **Necesidad/interés:** visibilizar resultados y gestionar adecuadamente sus condiciones de difusión y reutilización.
- **Interacción esperada:** aportar datos por medio de un desarrollador o responsable autorizado; eventualmente validar derechos y procedencia.
- **Información proporcionada/consultada:** nombre del proyecto, integrantes, resultados, autorizaciones, licencias, restricciones y productos relacionados.
- **Condiciones:** titularidad y autorizaciones deben verificarse conforme a la normativa aplicable; no se presume integración automática con sistemas de proyectos.

### ACT-07 — Autoridad de la Carrera (potencial)

- **Necesidad/interés:** conocer la oferta tecnológica y sus resultados de difusión y uso.
- **Interacción esperada:** consultar reportes autorizados o recibir informes generados por administración.
- **Información consultada:** cantidad de productos, procedencia, estado de publicaciones y métricas diferenciadas de consultas, descargas y accesos externos.
- **Condiciones:** no se ha confirmado un rol específico ni permisos de acceso directo al sistema; datos personales e informes restringidos requieren autorización.

### ACT-08 — Servicio de almacenamiento de archivos

- **Necesidad/interés:** conservar de forma íntegra y disponible los archivos distribuidos por UNL Store.
- **Interacción esperada:** recibir cargas autorizadas, almacenar objetos, recuperar archivos y permitir su entrega conforme al estado de publicación.
- **Información intercambiada:** archivo, ubicación o identificador, tamaño, tipo y comprobación de integridad.
- **Condiciones:** controles contra acceso no autorizado, límites de tamaño/tipo, respaldo y disponibilidad; por ahora no se ha escogido tecnología ni proveedor.
- **Observación:** es una dependencia de la solución, no necesariamente un sistema institucional independiente.

### ACT-09 — Plataforma externa de distribución

- **Necesidad/interés:** ofrecer recursos alojados fuera de UNL Store.
- **Interacción esperada:** el catálogo presenta enlaces aprobados que llevan al usuario a la plataforma externa; la integración automática no es un requisito aprobado.
- **Información intercambiada:** URL, tipo de recurso, plataforma de destino y metadatos públicos disponibles.
- **Condiciones:** disponibilidad y condiciones del tercero; un clic en un enlace no equivale a una descarga ni instalación confirmada.

### ACT-10 — Servicio externo o institucional de identidad (potencial)

- **Necesidad/interés:** identificar de manera confiable a usuarios de gestión, en caso de adoptarse autenticación delegada.
- **Interacción esperada:** validar identidad y proporcionar atributos autorizados al sistema, según un contrato todavía no definido.
- **Información intercambiada:** identificadores y atributos mínimos, sin asumir un protocolo o proveedor específico.
- **Condiciones:** opción no aprobada; deben aclararse el mecanismo de alta, la gestión de permisos y la protección de datos personales.

## 6. Relaciones significativas entre actores y el sistema

| Origen | Destino | Relación expresada como acción | Naturaleza |
|---|---|---|---|
| Visitante | UNL Store | Consulta catálogo y accede a recursos públicos | Confirmada |
| Desarrollador | UNL Store | Registra productos, versiones y solicita revisión | Confirmada |
| Administrador | UNL Store | Examina solicitudes y registra decisiones de publicación | Confirmada |
| Administrador | Desarrollador | Comunica aprobación, rechazo u observaciones mediante el sistema | Prevista; canal por especificar |
| Responsable de proyecto | UNL Store | Asocia iniciativas, participantes y productos | Detalle de permisos pendiente |
| Docente responsable | Responsable de proyecto | Aporta o valida procedencia académica | Propuesta |
| Equipo de investigación/vinculación | Responsable de proyecto | Aporta origen y documentación de resultados | Propuesta |
| UNL Store | Servicio de almacenamiento | Guarda y entrega archivos sujetos a autorización | Función necesaria; solución técnica pendiente |
| UNL Store | Plataforma externa | Presenta enlace a recurso alojado fuera del catálogo | Confirmada como modalidad |
| UNL Store | Autoridad de la Carrera | Presenta o facilita indicadores autorizados | Propuesta |
| UNL Store | Servicio de identidad | Solicita verificación de identidad | Condicional |

> Para visualizar estas relaciones gráficamente, utilizar el documento [`mapa-actores.md`](mapa-actores.md). Evitar duplicar aquí el mismo diagrama como segunda fuente independiente.

## 7. Necesidades identificadas y trazabilidad preliminar

| Necesidad | Actor originador | Comportamiento esperado | Estado |
|---|---|---|---|
| Encontrar productos relevantes | Visitante | Explorar, buscar y filtrar catálogo | Acordado |
| Obtener recursos autorizados | Visitante | Descargar archivos u obtener enlaces publicados | Acordado |
| Difundir productos | Desarrollador | Registrar productos y versiones | Acordado |
| Solicitar autorización | Desarrollador | Enviar contenido a revisión | Acordado |
| Controlar publicaciones | Administrador | Aprobar, observar, rechazar y retirar | Acordado |
| Identificar procedencia | Responsable de proyecto | Relacionar productos con proyectos y responsables | Previsto; permisos por aclarar |
| Consultar resultados | Autoridad de la Carrera | Obtener indicadores e informes | Pendiente de definición del acceso |
| Verificar aval académico | Docente responsable | Aportar/validar antecedentes | Pendiente |
| Mantener integridad del recurso | Administrador y visitantes | Distribuir únicamente archivos aprobados e íntegros | Requisito propuesto para precisar |

Esta tabla expresa **necesidades**; las obligaciones detalladas y medibles se documentarán en `docs/03-requisitos/` y en las especificaciones de funcionalidades que genere Spec Kit bajo `specs/`.

## 8. Preguntas de clarificación derivadas del análisis

| Código | Pregunta | Actores afectados | Impacto principal |
|---|---|---|---|
| PC-01 | ¿Quién autoriza el alta de desarrolladores y administradores? | Desarrollador, administrador | Autenticación y permisos |
| PC-02 | ¿Necesita un estudiante el aval de un docente o responsable para publicar? | Desarrollador, docente, responsable | Flujo de registro y requisitos de procedencia |
| PC-03 | ¿Qué ocurre si el administrador es también solicitante de una publicación? | Administrador, desarrollador | Independencia de aprobación |
| PC-04 | ¿Quién verifica titularidad, licencia y autorización de difusión? | Responsable, equipos, administrador | Validación previa a publicación |
| PC-05 | ¿Qué operaciones puede ejecutar un responsable de proyecto frente a un desarrollador común? | Responsable, desarrollador | Roles y autorización por objeto |
| PC-06 | ¿Qué categorías de usuarios deben disponer de cuenta y cuáles solo de acceso público? | Todos los usuarios humanos | Modelo de identidad |
| PC-07 | ¿Qué información de autores y proyectos se mostrará públicamente? | Visitante, desarrollador, equipos | Privacidad y ficha pública |
| PC-08 | ¿Cómo se verificará la disponibilidad de enlaces externos? | Visitante, administrador, plataformas | Integridad funcional del catálogo |
| PC-09 | ¿Quién podrá consultar estadísticas desagregadas y datos administrativos? | Administrador, responsable, autoridad | Confidencialidad de indicadores |
| PC-10 | ¿El inicio de sesión se resolverá localmente o mediante un sistema de identidad institucional? | Desarrollador, administrador, identidad externa | Dependencias y arquitectura futura |

Todas las preguntas están **pendientes**. Sus resoluciones deben consignarse en el registro de clarificación e incorporarse a los requisitos afectados. No deben inferirse respuestas del diagrama ni de la clasificación de actores.

## 9. Implicaciones para las tres fases de desarrollo

| Fase | Uso del análisis de actores | Exclusiones o cautelas |
|---|---|---|
| **F1 — Backend** | Definir permisos, casos de uso, reglas de publicación, accesos al catálogo y límites de integración mediante API. | No confundir actores con tablas o módulos; no seleccionar proveedores aún. |
| **F2 — Frontend web** | Diseñar recorridos de visitantes, desarrolladores y administradores a partir de las capacidades aprobadas. | No trasladar al cliente la lógica de negocio de aprobación. |
| **F3 — Móvil** | Atender a visitantes que exploran el catálogo y acceden a productos desde sus dispositivos. | No asumir funciones completas de gestión móvil sin cambio de alcance. |

## 10. Verificación del documento

- [x] Identifica actores humanos, colectivos institucionales y sistemas relacionados.
- [x] Clasifica actores según las categorías de la actividad.
- [x] Explica necesidad, interacción, información y condiciones por actor.
- [x] Distingue decisiones confirmadas de roles y servicios posibles.
- [x] Registra relaciones expresadas mediante acciones verificables.
- [x] Genera preguntas de clarificación antes de la implementación.
- [ ] Validar actores propuestos con representantes de la Carrera y responsables de proyectos.
- [ ] Confirmar permisos y excepciones del flujo de aprobación.
- [ ] Revisar y aprobar el mapa de actores derivado.

## 11. Fuentes y trazabilidad

1. Carrera de Computación — UNL. **UNL Store: Descripción del proyecto**, documento interno `DP-UNLSTORE-001`, versión 1.0, archivo [`docs/01-proyecto/descripcion-proyecto.md`](../01-proyecto/descripcion-proyecto.md). Fuente principal de alcance y acuerdos.
2. **Guía Didáctica: Arquitectura de un backend profesional** y materiales asociados, octubre de 2026, archivo de referencia `references/backend/Guia_Didactica_Arquitectura_Backend_SOLID.pdf`. Referencia metodológica para distinguir actores, sistema, límites y responsabilidades; la estructura concreta de actores proviene del análisis de UNL Store.
3. **Acuerdos de análisis del proyecto UNL Store**, establecidos durante la definición de requisitos y las tres fases de desarrollo. Fuente de las decisiones consignadas como confirmadas.

## 12. Declaración de uso de inteligencia artificial

Para la elaboración inicial de este documento se utilizó **ChatGPT (OpenAI)** como herramienta de apoyo en la organización, redacción, clasificación y análisis preliminar de actores, a partir de la descripción de UNL Store y los acuerdos suministrados. La información de actores potenciales, restricciones e interacciones debe ser validada por las personas responsables del proyecto antes de considerarse especificación aprobada.

---

**Control de cambios**

| Versión | Fecha | Descripción | Estado |
|---|---|---|---|
| 1.0 | 2026-10-14 | Identificación, clasificación, caracterización y trazabilidad inicial de actores | Borrador para validación |
