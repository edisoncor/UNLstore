# UNL Store — Descripción del proyecto

> **Documento:** DP-UNLSTORE-001  
> **Versión:** 1.0 (borrador de análisis)  
> **Fecha:** 14 de octubre de 2026  
> **Institución:** Universidad Nacional de Loja (UNL)  
> **Unidad académica:** Carrera de Computación  
> **Estado:** Propuesta para revisión y validación  
> **Enfoque de desarrollo:** Spec-Driven Development (SDD), con GitHub Spec Kit

## 1. Identificación del proyecto

**Nombre:** UNL Store  
**Denominación descriptiva:** Plataforma de publicación, distribución y seguimiento de productos tecnológicos de la Carrera de Computación.  
**Naturaleza:** Plataforma de software institucional con catálogo público de productos tecnológicos.  
**Población destinataria:** Comunidad universitaria y público en general, sin exigir autenticación para consultar el catálogo público.  
**Ámbito de origen de los productos:** Proyectos académicos, de investigación y de vinculación con la sociedad vinculados con la Carrera de Computación.

## 2. Contexto y antecedentes

En la Carrera de Computación de la Universidad Nacional de Loja se generan productos tecnológicos como resultado de actividades formativas, proyectos académicos, iniciativas de investigación y proyectos de vinculación con la sociedad. Estos resultados pueden comprender aplicaciones informáticas, componentes reutilizables, modelos de inteligencia artificial y otros recursos digitales.

En ausencia de un punto de acceso unificado, estos productos pueden encontrarse dispersos entre repositorios de código, sitios web, plataformas externas de distribución, servidores y espacios administrados por sus responsables. Esta dispersión dificulta su localización, conocimiento público, acceso, reutilización, mantenimiento y seguimiento a lo largo del tiempo.

UNL Store se propone como un espacio común para **visibilizar, organizar y distribuir productos tecnológicos**, preservando información sobre su origen, responsables, versiones, condiciones de uso y recursos disponibles. La plataforma no sustituye los repositorios de desarrollo ni los servicios externos que alojan aplicaciones; se integra conceptualmente con ellos como catálogo y canal de acceso.

## 3. Planteamiento del problema

La Carrera de Computación no dispone, como parte del problema que se busca atender, de una plataforma unificada y específica para **registrar, revisar, publicar, distribuir y dar seguimiento** a los productos tecnológicos generados en sus actividades académicas, investigativas y de vinculación con la sociedad.

Esta situación puede provocar:

- **Dispersión de resultados:** dificultad para conocer los productos desarrollados y localizar sus versiones o recursos de acceso.
- **Visibilidad limitada:** menor difusión de los resultados ante la comunidad universitaria y la sociedad.
- **Reutilización reducida:** dificultad para identificar soluciones y componentes aprovechables por otros proyectos.
- **Seguimiento insuficiente:** ausencia de criterios y registros comunes sobre versiones, disponibilidad y uso.
- **Publicación heterogénea:** falta de un flujo centralizado para revisar y autorizar la aparición de productos en el catálogo.
- **Continuidad limitada:** dependencia del conocimiento o almacenamiento de personas y equipos individuales.

### 3.1. Problema central

**Ausencia de una plataforma centralizada de la Carrera de Computación para registrar, evaluar administrativamente, publicar, distribuir y monitorear los productos tecnológicos desarrollados en proyectos académicos, de investigación y de vinculación con la sociedad.**

### 3.2. Necesidad identificada

Contar con un sistema que ofrezca un catálogo público confiable, un proceso controlado de publicación y mecanismos de distribución y seguimiento de productos tecnológicos, sin restringirlos a un único formato o plataforma de ejecución.

## 4. Justificación

UNL Store permitirá disponer de un punto de consulta único para acceder a resultados tecnológicos de la Carrera de Computación. Su aporte previsto comprende:

1. **Difusión:** dar visibilidad a las soluciones producidas por estudiantes, docentes y equipos de proyectos.
2. **Acceso:** facilitar el descubrimiento y la obtención de productos mediante archivos o enlaces autorizados.
3. **Reutilización:** promover el aprovechamiento de aplicaciones, bibliotecas, componentes y otros recursos digitales.
4. **Trazabilidad:** identificar responsables, procedencia, versiones y decisiones de publicación.
5. **Calidad del catálogo:** establecer un proceso administrativo de revisión previo a la publicación.
6. **Seguimiento:** disponer de indicadores diferenciados de consultas, descargas y accesos externos, para apoyar la evaluación de utilización y difusión.
7. **Evolución:** construir una base común de servicios para ofrecer posteriormente experiencias de uso web y móvil.

La plataforma constituye además un caso de desarrollo integral mediante SDD, en el que los requisitos, reglas de negocio y criterios de aceptación preceden a las decisiones de implementación.

## 5. Objetivos

### 5.1. Objetivo general

**Desarrollar UNL Store, una plataforma de distribución y gestión de productos tecnológicos de la Carrera de Computación de la Universidad Nacional de Loja, que permita centralizar su registro, revisión, publicación, acceso y seguimiento, promoviendo la visibilidad, reutilización y continuidad de los resultados de proyectos académicos, de investigación y de vinculación con la sociedad.**

### 5.2. Objetivos específicos

1. Definir un catálogo público que permita explorar, buscar, filtrar y consultar productos tecnológicos.
2. Establecer mecanismos para registrar productos, documentar su procedencia y asociarlos con sus responsables y proyectos.
3. Gestionar versiones, metadatos, documentación y recursos de distribución de acuerdo con las características de cada tipo de producto.
4. Implementar un proceso de revisión y aprobación administrativa previo a la publicación pública de productos y versiones.
5. Facilitar la obtención de archivos autorizados y el acceso a recursos alojados externamente.
6. Registrar información de uso y eventos de distribución que permita elaborar indicadores básicos de seguimiento.
7. Desarrollar de manera progresiva un backend de servicios, un frontend web y una aplicación móvil, preservando contratos y reglas de negocio comunes.

## 6. Descripción general de la solución propuesta

UNL Store será una plataforma web de catálogo público y un conjunto de servicios que respalden la gestión de productos tecnológicos. Los visitantes podrán consultar información de los productos sin iniciar sesión, encontrar recursos compatibles y acceder a archivos descargables o enlaces externos autorizados.

Los desarrolladores autorizados podrán registrar productos, documentar sus características, asociarlos con proyectos, incorporar versiones y solicitar su publicación. El administrador de la plataforma podrá revisar las solicitudes, aprobarlas, formular observaciones, rechazarlas y retirar publicaciones cuando exista una justificación.

Para evitar confusiones, se distinguen cuatro conceptos de negocio:

| Concepto | Descripción |
|---|---|
| **Producto** | Solución o recurso tecnológico con identidad propia y ficha descriptiva. |
| **Versión** | Edición identificable de un producto, con información de cambios. |
| **Recurso de distribución** | Archivo o enlace asociado con una versión. |
| **Publicación** | Disponibilidad pública autorizada del producto y sus recursos aprobados. |

El sistema diferenciará los **eventos de descarga de archivos internos** de los **accesos a enlaces externos**; estos últimos no deben interpretarse automáticamente como descargas o instalaciones completadas en terceros.

## 7. Tipos de productos admitidos

UNL Store admitirá las siguientes seis clases principales:

| Código | Tipo de producto | Ejemplos orientativos |
|---|---|---|
| TP-01 | **Aplicaciones web** | Portales, sistemas de información, aplicaciones SaaS y herramientas accesibles desde navegadores. |
| TP-02 | **Aplicaciones móviles** | Aplicaciones Android, iOS y multiplataforma. |
| TP-03 | **Aplicaciones de escritorio** | Programas para Windows, Linux y macOS. |
| TP-04 | **Bibliotecas y componentes** | Bibliotecas, paquetes, SDK, componentes y recursos reutilizables para desarrollo. |
| TP-05 | **Modelos y soluciones de IA** | Modelos, agentes, asistentes y soluciones que incorporan inteligencia artificial. |
| TP-06 | **Recursos tecnológicos adicionales** | Conjuntos de datos, plantillas, herramientas y otros artefactos digitales autorizados. |

Los productos tendrán metadatos comunes (nombre, descripción, tipo, responsable, procedencia, versión y licencia o condiciones de uso) y datos particulares según su naturaleza. La clasificación no implica que UNL Store ejecute, aloje o mantenga operativamente todas las aplicaciones catalogadas.

## 8. Actores principales

Se reconocen inicialmente los siguientes actores funcionales:

| Actor | Participación principal |
|---|---|
| **Visitante** | Explorar el catálogo, consultar fichas y obtener recursos públicos. |
| **Desarrollador** | Registrar y gestionar productos, versiones y solicitudes de publicación. |
| **Responsable de proyecto** | Asociar iniciativas, participantes y productos de su ámbito de responsabilidad; su representación exacta en permisos está por confirmar. |
| **Administrador** | Gestionar las publicaciones, resolver solicitudes y administrar los catálogos y las cuentas autorizadas. |

Se consideran además interesados institucionales y servicios relacionados —por ejemplo, docentes responsables, equipos de investigación y vinculación, autoridades, almacenamiento y plataformas externas— cuya participación específica se precisará en el análisis de actores.

> **Nota:** La caracterización detallada y el mapa de relaciones se mantendrán en `docs/02-analisis/`, para evitar duplicar aquí el documento de análisis.

## 9. Alcance funcional inicial

### 9.1. Incluido

- Catálogo público sin autenticación para exploración y consulta.
- Búsqueda, clasificación, filtros y ficha de cada producto.
- Gestión de cuentas y permisos para funciones administrativas y de desarrollo.
- Registro de proyectos de procedencia y responsables de los productos.
- Registro y modificación controlada de productos tecnológicos.
- Gestión de versiones y descripción de cambios.
- Asociación de archivos descargables y enlaces a recursos externos.
- Revisión administrativa, aprobación, observación, rechazo y retiro de publicaciones.
- Protección de recursos que aún no han sido aprobados para distribución.
- Registro de eventos de consulta y distribución e indicadores básicos.
- Auditoría de acciones críticas relacionadas con publicaciones y administración.
- Servicios compartidos que puedan utilizar los clientes web y móvil.

### 9.2. Excluido de la primera versión

- Venta de productos, pagos o facturación.
- Instalación remota y actualización automática de software en equipos de visitantes.
- Ejecución o alojamiento operativo automático de aplicaciones de terceros dentro de UNL Store.
- Entrenamiento de modelos de IA ofrecidos en el catálogo.
- Redes sociales, foros y sistemas complejos de recomendación personalizada.
- Publicación de productos sin aprobación administrativa.
- Gestión avanzada de aplicaciones privadas con distintos niveles de acceso para consumidores.

Estas exclusiones delimitan la primera versión y pueden revisarse mediante un cambio formal de alcance.

## 10. Acuerdos establecidos

| Aspecto | Acuerdo confirmado |
|---|---|
| **Audiencia** | Catálogo público para consulta de productos. |
| **Origen de productos** | Proyectos académicos, de investigación y de vinculación con la sociedad. |
| **Distribución** | Archivos internos y enlaces externos, incluso combinados. |
| **Aprobación** | A cargo del administrador de UNL Store. |
| **Tipos de productos** | Las seis clases definidas en la sección 7. |
| **Metodología** | Spec-Driven Development (SDD) apoyado por GitHub Spec Kit. |
| **Ejecución** | Tres fases sucesivas: backend, frontend web y aplicación móvil. |

## 11. Fases de desarrollo

La construcción del proyecto se organizará en tres fases. Las fases corresponden a componentes de **UNL Store**, no a los tipos de productos que estarán disponibles en el catálogo.

### Fase 1. Backend

**Propósito:** construir los servicios y las reglas de negocio que sustentan UNL Store, independientemente de una interfaz gráfica definitiva.

**Alcance:** identidad y permisos, gestión de proyectos y productos, clasificación de seis tipos, versiones, recursos de distribución, revisión de publicaciones, catálogo consultable, estadísticas, auditoría y contratos API.

**Resultado esperado:** servicios documentados y verificables mediante pruebas automatizadas y herramientas de consulta de API, preparados para servir a los dos clientes posteriores.

### Fase 2. Frontend web

**Propósito:** desarrollar la interfaz web pública y los espacios de gestión para desarrolladores y administradores.

**Alcance:** inicio, catálogo, búsqueda, filtros, fichas de productos, descarga y acceso a recursos, formularios de gestión, revisión de solicitudes e indicadores según permisos.

**Resultado esperado:** aplicación web adaptable a distintos dispositivos e integrada con la API de la Fase 1.

### Fase 3. Aplicación móvil

**Propósito:** proporcionar una experiencia móvil de consulta y acceso al catálogo de UNL Store.

**Alcance inicial:** exploración, búsqueda, filtros, consulta de productos y versiones, y acceso a recursos compatibles. Las funciones completas de administración permanecerán inicialmente en la interfaz web, salvo nueva decisión.

**Resultado esperado:** cliente móvil integrado con los servicios comunes del backend.

**Dependencia entre fases:** el frontend web y el cliente móvil utilizarán las reglas y contratos del backend. Una nueva versión del backend deberá considerar la compatibilidad con los clientes existentes.

## 12. Enfoque metodológico y documentación

El proyecto seguirá un enfoque de **desarrollo guiado por especificaciones (SDD)**. Antes de programar una funcionalidad se deberán comprender el problema y los actores, describir los comportamientos esperados, resolver las ambigüedades relevantes y definir criterios de aceptación verificables.

El flujo de trabajo con GitHub Spec Kit considerará:

1. **Constitution:** principios y reglas generales del proyecto.
2. **Specify:** definición funcional de cada característica.
3. **Clarify:** resolución y registro de ambigüedades.
4. **Plan:** decisiones arquitectónicas y planificación técnica.
5. **Tasks:** desglose de trabajo implementable y verificable.

La implementación y las pruebas se realizarán después de contar con especificaciones y planes suficientemente claros. Los artefactos de Spec Kit se mantendrán en sus ubicaciones correspondientes dentro de `.specify/` y `specs/`.

### 12.1. Organización documental

| Ubicación | Contenido |
|---|---|
| `README.md` | Presentación breve y acceso a documentos clave. |
| `docs/01-proyecto/` | Descripción, propósito, alcance y acuerdos generales. |
| `docs/02-analisis/` | Actores, mapa de actores, fundamentos SDD y preguntas de clarificación. |
| `docs/03-requisitos/` | Requisitos iniciales y reglas de negocio transversales. |
| `specs/` | Especificaciones, planes y tareas de funcionalidades gestionadas con Spec Kit. |
| `references/` | Material de consulta y documentos originales de referencia. |

Este documento constituye **la descripción general del proyecto**, no reemplaza la especificación de requisitos ni los contratos técnicos.

## 13. Restricciones y principios de alcance

- El catálogo público no exigirá iniciar sesión para consultar información publicada.
- Registrar, editar y aprobar publicaciones requerirá permisos autorizados.
- Los productos y versiones deberán superar el proceso de revisión establecido antes de hacerse públicos.
- La información distribuida deberá corresponder al contenido aprobado.
- Se deberá identificar responsable, procedencia y condiciones de uso de cada producto.
- Se deberán aplicar medidas de seguridad apropiadas a archivos, enlaces y datos personales.
- Se preservará la trazabilidad de decisiones administrativas y cambios de publicación.
- Las interfaces web y móvil deberán reutilizar los servicios del backend; las reglas de negocio no deberán duplicarse en los clientes.
- Las decisiones de frameworks, bases de datos, proveedores de infraestructura y arquitectura concreta se definirán y justificarán durante la planificación técnica, salvo que posteriormente se aprueben como restricciones explícitas.

## 14. Aspectos pendientes de clarificación

Las siguientes preguntas permanecen abiertas y no deben tratarse como acuerdos aprobados:

1. ¿Quién autoriza y crea las cuentas de desarrolladores?
2. ¿Qué aval institucional o académico se requerirá para publicar productos de estudiantes o proyectos?
3. ¿Cómo se resolverá una solicitud cuando el administrador también sea su autor?
4. ¿Quién verifica la titularidad, licencias y autorizaciones para distribuir productos?
5. ¿Qué formatos y tamaños de archivo estarán permitidos?
6. ¿Qué revisiones mínimas de seguridad y calidad se exigirán antes de publicar?
7. ¿Qué política regirá la conservación o retirada de versiones anteriores?
8. ¿Cómo se comprobará y notificará la indisponibilidad de enlaces externos?
9. ¿Qué datos de los autores, proyectos y participantes serán públicos?
10. ¿Qué mecanismo de identidad o autenticación se utilizará para los usuarios de gestión?

Las respuestas y decisiones correspondientes se documentarán en `docs/02-analisis/preguntas-clarificacion.md` y, una vez confirmadas, se incorporarán a los requisitos o especificaciones afectados.

## 15. Resultados esperados del proyecto

Al completar las tres fases se espera contar con:

- Una plataforma de acceso público que reúna productos tecnológicos de la Carrera de Computación.
- Un proceso institucionalmente definido y trazable de registro y autorización de publicaciones.
- Un catálogo capaz de representar los seis tipos de productos admitidos.
- Gestión de versiones, documentación y medios de distribución.
- Un backend con servicios reutilizables por aplicaciones web y móviles.
- Indicadores básicos que permitan analizar la difusión y utilización del catálogo.
- Documentación de requisitos, decisiones y pruebas que facilite el mantenimiento y evolución de UNL Store.

## 16. Estado y control del documento

| Versión | Fecha | Descripción | Estado |
|---|---|---|---|
| 1.0 | 2026-10-14 | Consolidación del contexto, problema, objetivos, alcance, acuerdos y fases del proyecto. | Borrador para validación |

**Criterio de actualización:** cualquier cambio que altere la finalidad, los tipos de productos admitidos, el modelo de aprobación, la modalidad de distribución o las fases deberá registrarse explícitamente antes de modificar las especificaciones derivadas.

---

**Nota de elaboración:** Documento preparado con asistencia de inteligencia artificial a partir de los acuerdos de definición de UNL Store. Requiere revisión y validación por los responsables del proyecto antes de considerarse una línea base aprobada.
