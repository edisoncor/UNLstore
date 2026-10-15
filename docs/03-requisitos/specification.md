# UNL Store — Especificación funcional del incremento 001

> **Código:** UNLSTORE-APE002-INC001 · **Versión:** 0.1 · **Estado:** Borrador para revisión docente  
> **Documento de trabajo:** `docs/03-requisitos/specification.md`  
> **Proyecto:** Carrera de Computación, Universidad Nacional de Loja  
> **Fase del producto:** 1 — Backend  
> **Incremento de la práctica:** Consulta del catálogo público y fichas de productos  
> **Metodología:** Spec-Driven Development (SDD)

## 1. Propósito e insumos

Este documento desarrolla la práctica **APE-002: Elaboración y refinamiento de `specification.md` con historias de usuario, requisitos, criterios de aceptación y contratos preliminares**. Usa como insumos los acuerdos del proyecto y los documentos de análisis del repositorio:

- `docs/01-proyecto/descripcion-proyecto.md`.
- `docs/02-analisis/identificacion-actores.md`.
- `docs/02-analisis/mapa-actores.md`.
- `docs/02-analisis/fundamentos-sdd.md`.
- `docs/02-analisis/preguntas-clarificacion.md`.
- `docs/03-requisitos/requisitos-iniciales.md`.

Los documentos mencionados son referencias de trabajo y sus versiones deben contrastarse con los archivos reales del repositorio. Las observaciones de ACD 2 y la retroalimentación docente aún no constan aquí: **están pendientes de incorporar**.

## 2. Problema, objetivo y alcance

### 2.1. Problema

Los productos tecnológicos desarrollados en los proyectos académicos, de investigación y de vinculación de la Carrera de Computación se encuentran dispersos, dificultando su localización, consulta, reutilización y distribución.

### 2.2. Objetivo del incremento

Permitir que cualquier visitante **descubra, busque, filtre y consulte información de productos tecnológicos públicamente aprobados**, así como los recursos autorizados para su distribución, mediante capacidades del backend consumibles posteriormente por el frontend web y la aplicación móvil.

### 2.3. Alcance incluido

- Consultar un listado público de productos publicados.
- Buscar por nombre y términos descriptivos.
- Filtrar por tipo de producto, categoría y procedencia.
- Consultar la ficha pública de un producto.
- Consultar sus versiones públicas y recursos autorizados de distribución.
- Distinguir archivos internos y enlaces externos en la información expuesta.
- Paginar y ordenar resultados de manera estable.
- Impedir que productos y versiones no publicados aparezcan en consultas públicas.

### 2.4. Alcance excluido de este incremento

- Registro y autenticación de desarrolladores o administradores.
- Alta/edición de productos, versiones, archivos o proyectos.
- Flujo de solicitud, observación, aprobación o retirada desde interfaces administrativas.
- Carga física de archivos y su análisis de seguridad.
- Gestión y descarga efectiva de binarios: se especifica su **descubrimiento** pero no el flujo final de entrega.
- Analítica, valoraciones, comentarios y recomendaciones personalizadas.
- Pantallas de frontend web o de aplicación móvil.

> **Dependencia importante:** el incremento presupone un conjunto de productos, versiones y recursos **ya marcados como públicos** mediante datos de demostración. El proceso real de aprobación pertenece a otro incremento y deberá respetar las mismas reglas de visibilidad.

### 2.5. Acuerdos generales que se preservan

- La audiencia del catálogo es pública y no requiere iniciar sesión.
- Los productos provienen de iniciativas académicas, investigativas o de vinculación.
- Los tipos admitidos son aplicaciones web, móviles, de escritorio, bibliotecas y componentes, modelos y soluciones de IA, y recursos tecnológicos adicionales.
- La distribución general de UNL Store admite archivos internos y enlaces externos.
- La aprobación de publicaciones corresponde a un administrador autorizado.
- El sistema se desarrolla por fases: backend, frontend web y aplicación móvil.

## 3. Actores y necesidades del incremento

| Actor | Necesidad | Participación en este incremento |
|---|---|---|
| Visitante público (principal) | Descubrir soluciones y consultar cómo acceder a ellas | Consulta catálogo, filtra, busca, visualiza fichas y versiones |
| Desarrollador (interesado) | Dar visibilidad a sus productos autorizados | Aparece como responsable público según las reglas de privacidad |
| Administrador (responsable) | Evitar la difusión de productos no autorizados | Su decisión previa determina la visibilidad; en este incremento no se implementa su interfaz |
| Responsable de proyecto (secundario) | Acreditar la procedencia de un producto | Sus datos aprobados pueden figurar en la ficha pública |
| Plataforma externa (sistema relacionado) | Alojar recursos a los que se accede desde UNL Store | Se registran enlaces públicos; su funcionamiento queda fuera de garantía |

## 4. Requisitos funcionales del incremento

Se utilizan identificadores exclusivos del incremento para evitar colisiones con el catálogo general `RF-...`.

| ID | Requisito verificable | Estado |
|---|---|---|
| RF-I01-01 | El sistema deberá permitir consultar, sin autenticación, un listado de productos publicados. | Derivado de acuerdo |
| RF-I01-02 | El sistema deberá excluir del listado público los productos no publicados, suspendidos o retirados. | Derivado de regla de publicación |
| RF-I01-03 | El sistema deberá permitir buscar los productos públicos por nombre y contenido descriptivo. | Propuesta del incremento |
| RF-I01-04 | El sistema deberá permitir filtrar los resultados por uno o más de estos criterios: tipo, categoría y origen del proyecto. | Propuesta del incremento |
| RF-I01-05 | El sistema deberá permitir consultar la ficha pública de un producto mediante un identificador estable. | Derivado de acuerdo |
| RF-I01-06 | La ficha deberá presentar nombre, resumen, descripción, tipo, categorías, procedencia y datos públicos autorizados del responsable. | Condicionado: privacidad y metadatos |
| RF-I01-07 | El sistema deberá mostrar únicamente las versiones publicadas de un producto consultable. | Derivado de regla de publicación |
| RF-I01-08 | El sistema deberá identificar, cuando exista, la versión vigente recomendada de cada producto. | Propuesta del incremento |
| RF-I01-09 | Las versiones públicas deberán mostrar sus recursos autorizados, indicando modalidad (archivo alojado o enlace externo) y compatibilidad, cuando corresponda. | Derivado de distribución mixta |
| RF-I01-10 | El listado deberá admitir paginación, con ordenamiento estable y una política explícita de límite de resultados. | Propuesta del incremento |
| RF-I01-11 | La consulta por un identificador inexistente o no visible deberá producir una respuesta de no encontrado, sin revelar información privada. | Derivado de seguridad |
| RF-I01-12 | El sistema deberá ofrecer un mecanismo para consultar los tipos y categorías disponibles para el filtrado, restringido a valores publicables. | Propuesta del incremento |

### 4.1. Reglas de negocio aplicables

| ID | Regla |
|---|---|
| RN-I01-01 | Ningún producto sin una publicación vigente y aprobada será visible en el catálogo público. |
| RN-I01-02 | Ninguna versión no publicada se mostrará al visitante. |
| RN-I01-03 | Solo se mostrarán recursos expresamente autorizados para distribución pública. |
| RN-I01-04 | El catálogo identificará un tipo principal entre los seis tipos admitidos. |
| RN-I01-05 | La ausencia de resultados debe producir una colección vacía válida, no un error de servidor. |
| RN-I01-06 | La información privada o restringida de responsables y proyectos no se incluirá en las respuestas públicas. |

## 5. Requisitos no funcionales

| ID | Atributo | Condición verificable y alcance | Estado |
|---|---|---|---|
| RNF-I01-01 | Seguridad | Las consultas públicas no deberán exponer recursos sin aprobación ni atributos marcados como privados; se verificará mediante pruebas positivas y negativas. | Base del proyecto |
| RNF-I01-02 | Rendimiento | Objetivo provisional: con 1.000 productos y 50 usuarios concurrentes, el 95 % de las consultas ordinarias de catálogo deberá responder en menos de 2 segundos, excluyendo transferencias de archivos. | Objetivo por validar |
| RNF-I01-03 | Interoperabilidad | Las operaciones de consulta deberán tener entradas, salidas, errores y criterios de compatibilidad documentados para clientes web y móviles. | Base del proyecto |
| RNF-I01-04 | Confiabilidad | Una búsqueda sin coincidencias deberá responder correctamente y no provocar fallos de la aplicación. | Propuesta |
| RNF-I01-05 | Mantenibilidad | Los seis tipos de producto deberán poder consultarse mediante reglas comunes sin exigir seis contratos públicos incompatibles. | Propuesta |
| RNF-I01-06 | Privacidad | Los datos personales se limitarán a los atributos autorizados para su publicación; queda pendiente definir el conjunto concreto. | Condicionado |
| RNF-I01-07 | Auditabilidad técnica | Los errores de consulta deberán permitir correlación operativa sin revelar secretos o datos privados en la respuesta pública. | Propuesta |

## 6. Historias de usuario

### HU-I01-01 — Explorar catálogo (P1)

**Como** visitante público, **quiero** consultar el catálogo de productos disponibles, **para** descubrir soluciones tecnológicas de la Carrera de Computación.

- **Vinculación:** RF-I01-01, RF-I01-02, RF-I01-10; RN-I01-01.
- **Aceptación — éxito:** Dado que existen productos publicados y otros en borrador, cuando consulto el catálogo, entonces recibo únicamente los publicados.
- **Aceptación — vacío:** Dado que no existen productos publicados, cuando consulto el catálogo, entonces recibo una lista vacía válida.
- **Aceptación — paginación:** Dado que hay más productos que el tamaño de página permitido, cuando consulto páginas sucesivas, entonces obtengo resultados paginados con orden estable.

### HU-I01-02 — Buscar y filtrar (P1)

**Como** visitante público, **quiero** buscar y filtrar productos, **para** encontrar aquellos que correspondan a mi necesidad y plataforma.

- **Vinculación:** RF-I01-03, RF-I01-04, RF-I01-12.
- **Aceptación — búsqueda:** Dado un conjunto de productos publicados, cuando ingreso un término de búsqueda, entonces solo se devuelven las coincidencias conforme a las reglas de búsqueda definidas.
- **Aceptación — filtros:** Dado que existen productos publicados de distintos tipos, cuando filtro por `biblioteca-componente`, entonces solo recibo productos de ese tipo.
- **Aceptación — filtros combinados:** Cuando combino tipo y procedencia, entonces el resultado cumple ambas condiciones.
- **Aceptación — parámetro inválido:** Cuando envío un valor de filtro no permitido, entonces obtengo un error de validación documentado, sin resultados ambiguos.

### HU-I01-03 — Consultar ficha (P1)

**Como** visitante público, **quiero** consultar la ficha de un producto, **para** conocer su propósito, procedencia, requisitos y opciones de acceso.

- **Vinculación:** RF-I01-05, RF-I01-06, RF-I01-11.
- **Aceptación — éxito:** Dado un producto publicado, cuando consulto su identificador, entonces recibo los metadatos públicos autorizados.
- **Aceptación — privacidad:** Si existen campos reservados del responsable, entonces no aparecen en la ficha pública.
- **Aceptación — recurso no disponible:** Si el identificador no existe o el producto no es público, entonces recibo «no encontrado», sin información restringida.

### HU-I01-04 — Consultar versiones y recursos (P1)

**Como** visitante público, **quiero** conocer las versiones y los recursos aprobados, **para** seleccionar el acceso o artefacto compatible que necesito.

- **Vinculación:** RF-I01-07, RF-I01-08, RF-I01-09.
- **Aceptación — versiones:** Dado que la versión 1.0 está publicada y la 2.0 está en revisión, cuando consulto las versiones, entonces se muestra 1.0 y no se expone 2.0.
- **Aceptación — modalidades:** Si una versión tiene un recurso de archivo y un enlace externo aprobados, entonces la respuesta diferencia correctamente ambas modalidades.
- **Aceptación — ausencia de recursos públicos:** No se deben devolver direcciones privadas ni rutas internas de almacenamiento.

## 7. Escenarios de calidad y excepciones

| ID | Situación | Comportamiento esperado |
|---|---|---|
| ESC-01 | Catálogo sin publicaciones | Lista vacía y metadatos de paginación coherentes |
| ESC-02 | Producto suspendido consultado directamente | Recurso no encontrado públicamente |
| ESC-03 | Versión pendiente de revisión | No aparece en la respuesta pública |
| ESC-04 | Filtro inexistente o inválido | Error de validación documentado |
| ESC-05 | Página más allá del último resultado | Comportamiento consistente que se fijará en el contrato |
| ESC-06 | Enlace externo publicado pero caído | El catálogo no garantiza la disponibilidad externa; política de aviso pendiente |
| ESC-07 | Producto con versiones de varias plataformas | La respuesta conserva las asociaciones producto-versión-recurso |
| ESC-08 | Solicitud masiva o parámetros abusivos | Aplicación de límites de consulta y respuesta segura, según política a definir |

## 8. Contratos preliminares del backend

> **IMPORTANTE:** se trata de **operaciones candidatas**, no de endpoints implementados ni de un contrato OpenAPI definitivo. Los nombres de recursos, parámetros, estructuras y errores se confirmarán durante la planificación.

| CP | Recurso / operación candidata | Entrada esperada | Resultado esperado | Relación |
|---|---|---|---|---|
| CP-I01-01 | Consultar colección de productos (`GET /api/v1/productos`) | Página, tamaño, orden opcionales | Colección pública paginada | HU-01; RF-01, RF-02, RF-10 |
| CP-I01-02 | Buscar y filtrar productos (`GET /api/v1/productos?...`) | Término, tipo, categoría, procedencia | Coincidencias públicas y paginación | HU-02; RF-03, RF-04 |
| CP-I01-03 | Consultar producto (`GET /api/v1/productos/{id}`) | Identificador de producto | Ficha pública o no encontrado | HU-03; RF-05, RF-06, RF-11 |
| CP-I01-04 | Consultar versiones (`GET /api/v1/productos/{id}/versiones`) | Identificador de producto | Versiones públicas y recomendada | HU-04; RF-07, RF-08 |
| CP-I01-05 | Consultar recursos (`GET /api/v1/versiones/{id}/recursos`) | Identificador de versión pública | Recursos públicos aprobados | HU-04; RF-09 |
| CP-I01-06 | Consultar tipos (`GET /api/v1/tipos-producto`) | Ninguna | Tipos disponibles para filtrar | HU-02; RF-12 |

### 8.1. Ejemplo ilustrativo de solicitud

```http
GET /api/v1/productos?tipo=biblioteca-componente&origen=investigacion&page=1
Accept: application/json
```

### 8.2. Resultado de ejemplo, sujeto a definición de contrato

```json
{
  "success": true,
  "message": "Productos públicos consultados.",
  "data": [
    {
      "id": "prd-demo-001",
      "nombre": "Biblioteca de análisis de datos",
      "tipo": "biblioteca-componente",
      "procedencia": "investigacion"
    }
  ],
  "errors": null,
  "meta": {
    "pagination": {"page": 1, "page_size": 20, "total": 1}
  }
}
```

**Nota:** el envoltorio JSON mostrado es una **propuesta arquitectónica previa del proyecto**, no una imposición de HTTP ni una decisión aprobada por esta práctica. En la etapa de diseño se decidirán nombres finales, códigos de error, compatibilidad y excepciones para descargas.

## 9. Clarificaciones y decisiones

### 9.1. Decisiones ya acordadas (no reabrir sin cambio explícito)

| ID | Decisión |
|---|---|
| DEC-001 | El catálogo de UNL Store es público. |
| DEC-002 | Se admiten seis tipos principales de productos. |
| DEC-003 | El origen de productos es académico, investigación o vinculación. |
| DEC-004 | La distribución general admite archivos y enlaces externos. |
| DEC-005 | La aprobación de publicación corresponde al administrador autorizado. |
| DEC-006 | El proyecto se desarrolla en backend, frontend web y móvil, en ese orden. |

### 9.2. Preguntas pendientes relevantes para este incremento

| ID | Pregunta | Prioridad | Afecta |
|---|---|---|---|
| PC-I01-01 | ¿Qué datos de desarrolladores y proyectos se pueden mostrar públicamente? | P0 | RF-I01-06, RNF-I01-06 |
| PC-I01-02 | ¿Qué estados exactos habilitan visibilidad pública y cómo se comporta la suspensión? | P0 | RF-I01-02, RF-I01-07, RN-I01-01 |
| PC-I01-03 | ¿Qué metadatos deben ser obligatorios en la ficha pública de cada uno de los seis tipos? | P0 | RF-I01-06 |
| PC-I01-04 | ¿Se admitirán versiones históricas visibles o únicamente una versión recomendada? | P1 | RF-I01-07, RF-I01-08 |
| PC-I01-05 | ¿Cómo se determinará la disponibilidad de enlaces externos rotos? | P1 | RF-I01-09, ESC-06 |
| PC-I01-06 | ¿Qué semántica tendrá la búsqueda (palabras completas, fragmentos, acentos, mayúsculas)? | P1 | RF-I01-03 |
| PC-I01-07 | ¿Qué tamaños de página y ordenamientos se permitirán? | P1 | RF-I01-10 |
| PC-I01-08 | ¿Qué criterios definen los datos de demostración usados antes del módulo de aprobación? | P1 | Pruebas y demo |

**Registro de respuesta:** para cada pregunta, agregar *decisión, responsable, fecha, justificación y requisitos modificados*. Hasta entonces su estado es **pendiente**. No se presupone una respuesta docente.

### 9.3. Registro de observaciones y retroalimentación

| Fecha | Origen | Observación | Cambio aplicado | Requisito afectado | Evidencia |
|---|---|---|---|---|---|
| Pendiente | Docente / equipo | Pendiente de la sesión de revisión | No aplicado | — | — |

## 10. Matriz de trazabilidad inicial

| Necesidad | Actor | Historia | Requisitos | Aceptación | Contrato preliminar |
|---|---|---|---|---|---|
| Descubrir soluciones | Visitante | HU-I01-01 | RF-I01-01, 02, 10 | Catálogo visible, vacío, paginado | CP-I01-01 |
| Encontrar soluciones pertinentes | Visitante | HU-I01-02 | RF-I01-03, 04, 12 | Búsqueda, filtros, validación | CP-I01-02, 06 |
| Comprender un producto | Visitante | HU-I01-03 | RF-I01-05, 06, 11 | Ficha válida, privacidad, no encontrado | CP-I01-03 |
| Identificar versión y acceso | Visitante | HU-I01-04 | RF-I01-07, 08, 09 | Solo versiones y recursos públicos | CP-I01-04, 05 |



