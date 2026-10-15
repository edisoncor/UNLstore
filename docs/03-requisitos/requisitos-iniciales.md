# UNL Store — Requisitos iniciales del software

| Campo | Información |
|---|---|
| Proyecto | UNL Store |
| Institución | Universidad Nacional de Loja — Carrera de Computación |
| Código documental | UNLSTORE-REQ-001 |
| Versión | 1.0 |
| Fecha | 14 de octubre de 2026 |
| Estado | **Línea base preliminar; pendiente de clarificación y validación** |
| Alcance | Proyecto completo, priorizando la fase 1: backend |

> **Objetivo de este documento.** Consolidar las necesidades, los requisitos iniciales, las reglas de negocio y los criterios de aceptación de UNL Store. Se diferencia lo **confirmado por acuerdos (AC)** de lo **propuesto para validación (PV)** y lo **pendiente de clarificación (PC)**. No sustituye a los archivos `spec.md` generados posteriormente para funcionalidades concretas con GitHub Spec Kit.

## 1. Documentos de referencia

- [Descripción del proyecto](../01-proyecto/descripcion-proyecto.md): problema, objetivos, alcance y acuerdos.
- [Identificación de actores](../02-analisis/identificacion-actores.md): necesidades, interacciones y restricciones.
- [Mapa de actores](../02-analisis/mapa-actores.md): relaciones entre actores y sistema.
- [Fundamentos SDD](../02-analisis/fundamentos-sdd.md): enfoque de especificación, clarificación y trazabilidad.
- [Preguntas de clarificación](../02-analisis/preguntas-clarificacion.md): decisiones abiertas `PC-01` a `PC-18`.

Se aplicarán las guías didácticas de backend conservadas en `references/backend/` como **material técnico de consulta**, sin confundir recomendaciones arquitectónicas con necesidades del negocio.

## 2. Problema y propósito

**Problema:** los productos tecnológicos originados en proyectos académicos, de investigación y de vinculación de la Carrera de Computación se encuentran dispersos, lo que dificulta localizarlos, distribuirlos, reutilizarlos, mantener sus versiones y conocer su utilización.

**Propósito:** proporcionar un catálogo público y un proceso controlado para registrar, revisar, publicar, distribuir y dar seguimiento a dichos productos, mediante servicios reutilizables por clientes web y móvil.

## 3. Alcance y acuerdos confirmados

| Código | Acuerdo confirmado | Consecuencia inicial |
|---|---|---|
| AC-01 | Catálogo público | El visitante consulta productos publicados sin autenticarse. |
| AC-02 | Origen académico, investigación y vinculación | Los productos deben declarar su procedencia. |
| AC-03 | Distribución por archivos y enlaces externos | Se admiten ambos mecanismos, incluso combinados. |
| AC-04 | Aprobación por administrador | No hay publicación sin decisión administrativa autorizada. |
| AC-05 | Seis clases de productos | Metadatos y validaciones específicos por tipo. |
| AC-06 | Desarrollo en tres fases | F1 backend; F2 frontend web; F3 cliente móvil. |
| AC-07 | SDD con GitHub Spec Kit | Requisitos y aceptación preceden a planificación e implementación. |

### 3.1. Tipos de producto

| Código | Tipo |
|---|---|
| TP-01 | Aplicaciones web |
| TP-02 | Aplicaciones móviles |
| TP-03 | Aplicaciones de escritorio |
| TP-04 | Bibliotecas y componentes |
| TP-05 | Modelos y soluciones de inteligencia artificial |
| TP-06 | Recursos tecnológicos adicionales |

### 3.2. Exclusiones iniciales

No se contemplan en la primera versión pagos, comercio electrónico, ejecución o alojamiento automático de las aplicaciones catalogadas, instalación remota, actualización automática en dispositivos, entrenamiento de modelos de IA, recomendaciones inteligentes personalizadas ni redes sociales. Cualquier ampliación requiere cambio de alcance documentado.

## 4. Actores del negocio

| Código | Actor | Responsabilidad general | Estado |
|---|---|---|---|
| ACT-01 | Visitante | Consultar catálogo y acceder a recursos públicos | Confirmado |
| ACT-02 | Desarrollador | Registrar productos y proponer publicaciones | Confirmado |
| ACT-03 | Administrador | Revisar, aprobar y gestionar publicaciones | Confirmado |
| ACT-04 | Responsable de proyecto | Relacionar proyectos, participantes y productos | Propuesto; permisos por aclarar |
| ACT-05 | Interesados institucionales | Aportar antecedentes y consultar resultados cuando corresponda | Participación por validar |
| ACT-06 | Sistemas y servicios externos | Almacenamiento, distribución y eventualmente identidad | Integraciones por validar |

Un actor es un rol funcional; una persona podría asumir varios roles, sujeto a restricciones de autorización y conflicto de interés todavía por precisar.

## 5. Convenciones de requisitos

- `RF-###`: requisito funcional del negocio, independiente de tecnología.
- `RN-###`: regla de negocio o invariante propuesta.
- `RNF-###`: atributo de calidad o restricción no funcional.
- `CA-###`: criterio de aceptación verificable.
- `PC-XX`: pregunta abierta en el registro de clarificación.
- **Estado:** `AC` (derivado directamente de acuerdo confirmado), `PV` (propuesta por validar), `PC` (requiere resolver pregunta identificada).
- **Prioridad:** `P0` indispensable para la funcionalidad principal, `P1` necesario para primera versión, `P2` mejora futura o decisión de fase posterior. La prioridad es propuesta, no compromiso temporal.

Los códigos de este documento constituyen **identificadores iniciales**, no reemplazan automáticamente los identificadores de versiones previas de borradores. La correspondencia deberá verificarse al consolidar cada `spec.md`.

## 6. Requisitos funcionales iniciales

### 6.1. Identidad y permisos

| Código | Requisito | Prioridad | Estado / dependencia |
|---|---|---|---|
| RF-001 | El sistema deberá autenticar a los usuarios que realicen funciones de gestión. | P0 | PV · PC-16 |
| RF-002 | El sistema deberá limitar las operaciones de registro, revisión y administración a los roles autorizados. | P0 | AC/PV · PC-01, PC-03 |
| RF-003 | El administrador deberá poder gestionar cuentas y asignaciones de roles conforme al procedimiento autorizado. | P0 | PC · PC-01 |
| RF-004 | El sistema deberá permitir consultar los datos y permisos propios de la cuenta autenticada. | P1 | PV · PC-12 |

### 6.2. Proyectos, procedencia y responsables

| Código | Requisito | Prioridad | Estado / dependencia |
|---|---|---|---|
| RF-005 | El sistema deberá permitir registrar proyectos de procedencia de tipo académico, investigación o vinculación. | P0 | AC/PV · PC-18 |
| RF-006 | El sistema deberá permitir relacionar cada producto con sus proyectos y responsables autorizados. | P0 | PV · PC-02, PC-18 |
| RF-007 | El sistema deberá registrar la información de procedencia necesaria para acreditar la publicación. | P0 | PC · PC-02, PC-04 |

### 6.3. Productos y metadatos

| Código | Requisito | Prioridad | Estado / dependencia |
|---|---|---|---|
| RF-008 | El desarrollador autorizado deberá poder crear y modificar productos en preparación. | P0 | PV · PC-01, PC-02 |
| RF-009 | Cada producto deberá pertenecer a uno de los seis tipos admitidos. | P0 | AC |
| RF-010 | El sistema deberá registrar datos comunes del producto: nombre, descripción, tipo, responsable, procedencia y condiciones de uso. | P0 | PV · PC-04, PC-06 |
| RF-011 | El sistema deberá solicitar información específica según el tipo de producto antes de admitir su revisión. | P0 | PV · PC-06, PC-14 |
| RF-012 | El sistema deberá permitir adjuntar imágenes, documentación e información de compatibilidad pertinentes. | P1 | PV · PC-06, PC-07 |
| RF-013 | El sistema deberá permitir asociar categorías y etiquetas a los productos. | P1 | PV |
| RF-014 | El sistema deberá permitir relacionar productos vinculados a una misma solución o proyecto. | P1 | PV · PC-18 |

### 6.4. Versiones y recursos de distribución

| Código | Requisito | Prioridad | Estado / dependencia |
|---|---|---|---|
| RF-015 | El sistema deberá permitir registrar distintas versiones de un producto con su descripción de cambios. | P0 | PV · PC-08 |
| RF-016 | El sistema deberá permitir asociar archivos descargables a una versión. | P0 | AC/PV · PC-05, PC-07 |
| RF-017 | El sistema deberá permitir asociar enlaces externos a una versión. | P0 | AC/PV · PC-05, PC-10 |
| RF-018 | Una versión podrá combinar archivos alojados y enlaces externos. | P0 | AC |
| RF-019 | El sistema deberá validar los recursos de distribución antes de aceptar su publicación. | P0 | PV · PC-05, PC-07 |
| RF-020 | El sistema deberá identificar las versiones aprobadas y la versión recomendada, según la política definida. | P1 | PC · PC-08 |
| RF-021 | El sistema deberá conservar la trazabilidad de los recursos y versiones que fueron publicados o retirados. | P1 | PV · PC-08, PC-17 |

### 6.5. Revisión y publicación

| Código | Requisito | Prioridad | Estado / dependencia |
|---|---|---|---|
| RF-022 | El desarrollador autorizado deberá poder solicitar revisión de un producto o de una nueva versión. | P0 | PV · PC-02, PC-06 |
| RF-023 | El administrador deberá poder consultar las solicitudes pendientes y sus antecedentes. | P0 | AC/PV |
| RF-024 | El administrador deberá poder aprobar, observar o rechazar solicitudes dejando constancia de su decisión. | P0 | AC/PV · PC-17 |
| RF-025 | El sistema deberá impedir que una versión no aprobada se distribuya públicamente. | P0 | AC |
| RF-026 | El sistema deberá permitir corregir y reenviar solicitudes observadas, de acuerdo con el flujo aprobado. | P0 | PV · PC-17 |
| RF-027 | El sistema deberá permitir retirar una publicación, conservando la justificación y el historial. | P1 | PV · PC-17 |
| RF-028 | El sistema deberá aplicar la política definida para prevenir conflictos de interés en la aprobación. | P0 | PC · PC-03 |
| RF-029 | El sistema deberá distinguir el acto de aprobar de la disponibilidad pública cuando la política establezca pasos separados. | P0 | PC · PC-09 |

### 6.6. Catálogo público

| Código | Requisito | Prioridad | Estado / dependencia |
|---|---|---|---|
| RF-030 | El visitante deberá poder consultar el catálogo público sin iniciar sesión. | P0 | AC |
| RF-031 | El visitante deberá poder buscar productos publicados por nombre o palabras clave. | P0 | PV |
| RF-032 | El visitante deberá poder filtrar los productos por tipo y categoría. | P0 | PV |
| RF-033 | El visitante deberá poder consultar una ficha pública con descripción, procedencia, versiones y recursos autorizados. | P0 | PV · PC-12 |
| RF-034 | El visitante deberá poder descargar archivos publicados o acceder a enlaces externos autorizados. | P0 | AC/PV · PC-05, PC-10 |
| RF-035 | El sistema deberá excluir de los resultados públicos los contenidos en borrador, revisión o retirados. | P0 | AC/PV · PC-17 |

### 6.7. Seguimiento, administración y auditoría

| Código | Requisito | Prioridad | Estado / dependencia |
|---|---|---|---|
| RF-036 | El sistema deberá registrar eventos de consulta de fichas y utilización de recursos del catálogo. | P1 | PV · PC-13 |
| RF-037 | El sistema deberá diferenciar descargas internas y accesos a enlaces externos en las estadísticas. | P1 | PV · PC-13 |
| RF-038 | El administrador deberá poder consultar indicadores básicos de productos, versiones, publicaciones y utilización. | P1 | PV · PC-13 |
| RF-039 | El sistema deberá registrar las decisiones de publicación y las acciones administrativas relevantes para auditoría. | P0 | PV · PC-17 |
| RF-040 | El administrador deberá poder gestionar los catálogos de clasificación y los parámetros operativos autorizados. | P1 | PV · PC-06, PC-07 |

## 7. Información mínima por tipo de producto

La siguiente matriz es **propuesta sujeta a PC-06**. Los campos comunes se aplican a todos los tipos; se determinarán cuáles son obligatorios desde el borrador y cuáles solo antes de revisión.

| Tipo | Metadatos particulares propuestos | Preguntas |
|---|---|---|
| Web | URL HTTPS, requisitos de acceso y entorno compatible | PC-05, PC-06 |
| Móvil | Plataforma, requisitos mínimos, recurso de instalación o enlace externo | PC-05, PC-06, PC-07 |
| Escritorio | Sistema operativo, arquitectura si aplica, requisitos e instalador/enlace | PC-05, PC-06, PC-07 |
| Bibliotecas y componentes | Ecosistema/lenguaje, compatibilidad, dependencias, documentación y paquete/repositorio | PC-06 |
| IA | Finalidad, limitaciones, modalidad de uso, procedencia de datos cuando corresponda y riesgos conocidos | PC-04, PC-06, PC-14 |
| Recursos adicionales | Clase de recurso, formato, procedencia, documentación y condiciones de reutilización | PC-04, PC-06, PC-14 |

## 8. Reglas de negocio preliminares

| Código | Regla propuesta | Estado / preguntas |
|---|---|---|
| RN-001 | Un producto tiene un tipo principal entre los seis admitidos. | AC |
| RN-002 | Toda publicación requiere una aprobación administrativa autorizada. | AC |
| RN-003 | Solo pueden aparecer públicamente versiones y recursos con aprobación vigente. | AC/PV · PC-09, PC-17 |
| RN-004 | Cada producto debe tener al menos un responsable identificado. | PV · PC-02, PC-11 |
| RN-005 | La procedencia de cada producto debe corresponder al alcance académico, investigativo o de vinculación. | AC/PV · PC-18 |
| RN-006 | La solicitud de revisión exige los metadatos específicos y recursos necesarios del tipo correspondiente. | PV · PC-05, PC-06 |
| RN-007 | El solicitante no debe aprobar su propia solicitud; el procedimiento alternativo requiere definición. | PC · PC-03 |
| RN-008 | Una versión debe identificarse de forma unívoca dentro de su producto. | PV · PC-08 |
| RN-009 | No debe sustituirse silenciosamente el contenido de un recurso ya aprobado. | PV · PC-17 |
| RN-010 | La retirada de una publicación debe conservar decisiones y antecedentes para auditoría. | PV · PC-17 |
| RN-011 | Las descargas internas y los accesos externos se contabilizarán por separado. | PV · PC-13 |
| RN-012 | La disponibilidad de un enlace externo no equivale a una instalación o descarga confirmada por terceros. | PV · PC-13 |
| RN-013 | La publicación de software o datos exige condiciones de uso y autorizaciones correspondientes. | PV · PC-04, PC-14 |

**Nota:** las reglas sujetas a clarificación no deberán codificarse como decisiones definitivas antes de resolver sus respectivas preguntas.

## 9. Requisitos no funcionales iniciales

| Código | Atributo | Requisito / objetivo inicial | Estado |
|---|---|---|---|
| RNF-001 | Seguridad | El sistema deberá aplicar autenticación, autorización por operación/recurso y validación de entradas para funciones de gestión. | PV |
| RNF-002 | Protección de archivos | Los recursos no publicados no deberán ser accesibles por rutas públicas; se comprobarán tipos y riesgos según política pendiente. | PV · PC-05, PC-07 |
| RNF-003 | Integridad | Los archivos alojados deberán contar con un mecanismo para detectar cambios no autorizados. | PV |
| RNF-004 | Privacidad | El sistema deberá limitar la exposición de datos personales a lo autorizado y atender las obligaciones legales aplicables. | PV · PC-12 |
| RNF-005 | Accesibilidad | Los clientes web y móvil deberán adoptar criterios de accesibilidad apropiados; para la web se propone WCAG 2.2 AA. | PV · F2/F3 |
| RNF-006 | Interoperabilidad | El backend deberá ofrecer contratos documentados y estables para los consumidores web y móvil. | AC/PV |
| RNF-007 | Rendimiento | Las consultas deberán responder dentro de objetivos cuantificables que se definan con carga y volumen de prueba; como hipótesis: p95 inferior a 2 s para consultas ordinarias con 50 usuarios concurrentes y 1.000 productos. | PV; **no aprobado** |
| RNF-008 | Trazabilidad | Las operaciones sensibles registrarán actor, acción, recurso, fecha y resultado, sin almacenar secretos. | PV |
| RNF-009 | Mantenibilidad | La solución deberá separar responsabilidades para permitir cambios en tipos de producto, distribución y revisión sin alterar funcionalidades no relacionadas. | PV |
| RNF-010 | Recuperación | Los datos y archivos deberán contar con respaldo y restauración verificable; RPO/RTO pendientes. | PV |
| RNF-011 | Compatibilidad | La API deberá permitir consumo coherente desde frontend web y aplicación móvil. | AC/PV |

Los requisitos medibles de capacidad, disponibilidad, recuperación, almacenamiento y retención requieren una decisión posterior sustentada en condiciones reales del despliegue.

## 10. Criterios de aceptación iniciales

Los escenarios siguientes permitirán verificar la especificación. El detalle de entradas, errores y pruebas se desarrollará en los `spec.md` correspondientes.

### CA-001 — Consulta pública (RF-030, RF-035)

- **Dado** que existe un producto publicado y otro pendiente de revisión,
- **cuando** un visitante consulta el catálogo sin autenticarse,
- **entonces** puede visualizar el publicado y no recibe el pendiente.

### CA-002 — Clasificación (RF-009, RF-032)

- **Dado** que el catálogo contiene productos de diferentes tipos,
- **cuando** el visitante filtra por bibliotecas y componentes,
- **entonces** se muestran únicamente productos públicos clasificados en ese tipo.

### CA-003 — Registro de producto (RF-008, RF-010)

- **Dado** un desarrollador autorizado,
- **cuando** registra los datos mínimos válidos de un producto,
- **entonces** el sistema lo conserva sin publicarlo automáticamente.

### CA-004 — Distribución combinada (RF-016, RF-017, RF-018)

- **Dada** una versión que incluye un archivo y un enlace externo válidos,
- **cuando** se autoriza su publicación,
- **entonces** ambos recursos podrán ofrecerse públicamente según las restricciones aprobadas.

### CA-005 — Publicación restringida (RF-024, RF-025)

- **Dada** una versión pendiente de revisión,
- **cuando** un visitante intenta obtener un recurso no aprobado,
- **entonces** el sistema impide su distribución pública.

### CA-006 — Decisión de revisión (RF-023, RF-024, RF-039)

- **Dada** una solicitud presentada para revisión,
- **cuando** un administrador autorizado registra una decisión válida,
- **entonces** queda constancia del resultado, responsable y fecha, conforme al procedimiento definido.

### CA-007 — Nueva versión (RF-015, RF-020, RF-021)

- **Dado** un producto con una versión pública y otra nueva en revisión,
- **cuando** el visitante consulta el producto,
- **entonces** no se ofrece la versión aún no aprobada; la disponibilidad de versiones anteriores se ajustará a **PC-08**.

### CA-008 — Eventos diferenciados (RF-036, RF-037)

- **Dado** un producto con archivo interno y enlace externo,
- **cuando** se activan los respectivos recursos,
- **entonces** se registran eventos diferenciados, sin afirmar que una instalación externa se completó.

### CA-009 — Permisos (RF-002, RF-024)

- **Dado** un usuario sin permiso de aprobación,
- **cuando** intenta decidir sobre una solicitud,
- **entonces** el sistema deniega la operación y no cambia su estado.

### CA-010 — Tipos de producto (RF-011)

- **Dado** un producto clasificado como modelo o solución de IA,
- **cuando** su responsable solicita revisión,
- **entonces** se evalúan los datos particulares exigidos para ese tipo **una vez definidos en PC-06 y PC-14**.

## 11. Dependencias de clarificación

| Preguntas | Requisitos principalmente afectados | Consecuencia de mantenerlas abiertas |
|---|---|---|
| PC-01, PC-02, PC-16 | RF-001 a RF-008 | No fijar aún mecanismo de alta ni permisos definitivos. |
| PC-03, PC-09, PC-17 | RF-022 a RF-029, RF-039 | No cerrar estados ni política de aprobación. |
| PC-04, PC-05, PC-06, PC-14 | RF-007, RF-010 a RF-012, RF-019 | No cerrar metadatos y criterios de seguridad por tipo. |
| PC-07, PC-08, PC-10 | RF-015 a RF-021, RF-034 | No fijar restricciones de archivos y versiones. |
| PC-11, PC-12, PC-18 | RF-005 a RF-007, RF-033 | No cerrar procedencia, responsables ni datos públicos. |
| PC-13 | RF-036 a RF-038 | No asumir definiciones de métricas no acordadas. |
| PC-15 | Alcance funcional del cliente móvil | Resolver antes de especificar F3. |

## 12. Asignación de requisitos a las tres fases

| Fase | Alcance principal | Resultado verificable |
|---|---|---|
| **F1 — Backend** | RF-001 a RF-040 como capacidades de negocio y servicios; RN y RNF aplicables | API verificable sin depender de pantallas; pruebas de reglas, permisos, recursos y contratos |
| **F2 — Frontend web** | Presentar catálogo, fichas, búsqueda, descarga y área de gestión consumiendo F1 | Flujos web accesibles y probados, sin duplicar las reglas centrales de negocio |
| **F3 — Cliente móvil** | Explorar catálogo, buscar, consultar fichas y acceder a recursos compatibles | Cliente móvil integrado con API; autenticación y otras funciones por definir en PC-15 |

**Precisión:** el tipo de producto “aplicación móvil” está admitido en F1, mientras que la app móvil **cliente de UNL Store** se construirá en F3.

## 13. Matriz resumida de trazabilidad

| Necesidad | Requisitos | Actores | Escenarios | Fase inicial |
|---|---|---|---|---|
| Controlar acceso a gestión | RF-001 a RF-004 | Desarrollador, administrador | CA-009 | F1 |
| Identificar origen | RF-005 a RF-007 | Desarrollador, responsable de proyecto | CA-003 | F1 |
| Gestionar seis tipos de producto | RF-008 a RF-014 | Desarrollador | CA-002, CA-003, CA-010 | F1 |
| Distribuir versiones | RF-015 a RF-021 | Desarrollador, visitante | CA-004, CA-007 | F1 |
| Aprobar publicaciones | RF-022 a RF-029 | Desarrollador, administrador | CA-005, CA-006, CA-009 | F1 |
| Descubrir productos | RF-030 a RF-035 | Visitante | CA-001, CA-002 | F1 API / F2 y F3 UI |
| Evaluar uso y trazabilidad | RF-036 a RF-040 | Administrador, desarrollador | CA-006, CA-008 | F1 |

## 14. Preparación para GitHub Spec Kit

Este documento describe **el alcance global**. No debe copiarse indiscriminadamente como una sola especificación de implementación.

Secuencia recomendada:

1. Revisar acuerdos y resolver las preguntas P0 que afectan al primer módulo.
2. Definir principios generales de proyecto mediante `constitution`.
3. Seleccionar una funcionalidad acotada, por ejemplo **consulta del catálogo público**, y convertirla en una especificación con `specify`.
4. Ejecutar `clarify` para resolver vacíos de dicha funcionalidad.
5. Preparar su `plan` técnico y después las `tasks`.
6. Implementar y comprobar los criterios de aceptación, manteniendo trazabilidad.

Rutas orientativas:

```text
docs/03-requisitos/requisitos-iniciales.md   # visión global y línea base preliminar
.specify/memory/constitution.md              # principios de desarrollo
specs/001-catalogo-publico/spec.md           # especificación de funcionalidad
specs/001-catalogo-publico/plan.md           # plan técnico
specs/001-catalogo-publico/tasks.md          # tareas implementables
```

Los nombres exactos y la ubicación de los artefactos en `specs/` dependerán de la versión y configuración instalada de Spec Kit.

## 15. Control de calidad documental

Antes de aprobar esta línea base comprobar:

- [ ] Cada requisito utiliza lenguaje verificable y no adelanta tecnologías de implementación.
- [ ] Se mantiene la correspondencia con la descripción y actores del proyecto.
- [ ] Las siete decisiones `AC-01` a `AC-07` se respetan.
- [ ] Los seis tipos de producto están contemplados.
- [ ] Ninguna pregunta pendiente aparece disfrazada de decisión confirmada.
- [ ] Los criterios de aceptación distinguen escenarios positivos y restricciones críticas.
- [ ] Se han identificado los requisitos que corresponden a backend, frontend y móvil.
- [ ] Los códigos y enlaces se mantienen consistentes con los demás documentos.
- [ ] La revisión del equipo responsable queda registrada antes de declarar la versión aprobada.

## 16. Fuentes y declaración de uso de IA

**Fuentes del proyecto:** `descripcion-proyecto.md`, `identificacion-actores.md`, `mapa-actores.md`, `fundamentos-sdd.md` y `preguntas-clarificacion.md`. Como material complementario se utiliza la guía didáctica *Arquitectura de un backend profesional* conservada en `references/backend/`.

**Documentación de herramienta:** [GitHub Spec Kit — repositorio oficial](https://github.com/github/spec-kit) y [sitio de documentación](https://github.github.com/spec-kit/).

**Uso de inteligencia artificial:** se utilizó ChatGPT (OpenAI) como apoyo para ordenar los requisitos, proponer identificadores, escenarios y criterios de aceptación, y relacionarlos con las fases de UNL Store. Las formulaciones marcadas como `PV` o `PC` son propuestas o asuntos abiertos, no acuerdos institucionales. La revisión, aprobación y mantenimiento de la línea base corresponden al equipo responsable del proyecto.

## 17. Control de cambios

| Versión | Fecha | Cambios | Estado |
|---|---|---|---|
| 1.0 | 2026-10-14 | Consolidación inicial de requisitos y dependencias de clarificación | Borrador para validación |
