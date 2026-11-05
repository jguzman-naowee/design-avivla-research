**AVIVLA**

*Aceleradora de Dignidad*

**Documento de Requerimientos Técnicos — MVP v1.0**

|  |  |
| --- | --- |
| **Proyecto** | AVIVLA — Plataforma de coordinación de recursos sociales para inmigrantes en España |
| **Empresa** | Naowee SAS |
| **Versión** | MVP v1.0 |
| **Fecha** | Junio 2026 |
| **Preparado por** | Danna Marcela Arrieta Aguilar |

# **1. Contexto y Propósito del Proyecto**

AVIVLA es una plataforma de coordinación social diseñada para conectar organizaciones, recursos y beneficiarios dentro del ecosistema de atención a inmigrantes en España. El sistema busca eliminar la fragmentación institucional que impide que las personas en situación de vulnerabilidad accedan de forma eficiente a los recursos disponibles.

El problema central no es la falta de recursos, sino su desconexión. Diferentes entidades gestionan los mismos casos sin saberlo, los recursos existen pero no están comunicados entre sí, y ningún actor tiene una visión global del usuario y sus necesidades. AVIVLA es la infraestructura que hace posible que el puzzle social funcione.

## **1.1 Base tecnológica**

La plataforma AVIVLA se desarrolla sobre la base tecnológica de Naowee (referenciada internamente como LBR), adaptando y parametrizando su lógica de grupos, membresías y gestión de usuarios para el contexto específico del proyecto. El objetivo del MVP es duplicar y parametrizar esta lógica bajo el nombre Bibla.

## **1.2 Alcance del MVP**

El Producto Mínimo Viable se centra en un modelo de registro gestionado por el personal, evitando el autoservicio para controlar mejor las rutas de usuario en esta primera etapa. Las funcionalidades de autoservicio para beneficiarios se consideran para fases posteriores.

# **2. Actores del Sistema y Terminología Unificada**

La reunión del 19 de junio de 2026 estableció la terminología oficial del proyecto para evitar confusiones en el desarrollo. Los siguientes términos deben utilizarse de forma consistente en todo el equipo.

|  |  |  |
| --- | --- | --- |
| **Término** | **Antes se llamaba** | **Definición oficial** |
| **Administrador** | Admin / Gestor | Responsable de configurar la plataforma: registra entidades, define categorías de recursos y habilita conectores. No aparece en el flujo de cara al beneficiario. |
| **Conector** | Líder / Trabajador social | Profesional o voluntario que guía al beneficiario. Realiza la entrevista del Mapa de Vida, registra al beneficiario en el sistema y gestiona su itinerario. |
| **Beneficiario** | Persona / Usuario final | Persona inmigrante con necesidades específicas (vivienda, empleo, salud, documentación, formación, apoyo legal). Es el destinatario final de los recursos del ecosistema. |
| **Entidad** | Sede / Alianza | Organización participante (ONG, administración pública, servicio social). Actúa como contenedor que agrupa grupos, eventos y elementos de la librería con sus categorías. |
| **Recurso** | Servicio / Ayuda | Servicio específico ofrecido por una entidad: comedor social, asesoría jurídica, charla de extranjería, curso de formación. El sistema prioriza el recurso sobre la entidad para conectar directamente necesidad con solución. |

## **2.1 Relaciones entre actores**

Una entidad puede tener múltiples conectores asociados. Un conector puede gestionar múltiples beneficiarios. Un beneficiario puede pertenecer a múltiples grupos y recibir recursos de distintas entidades simultáneamente, según las diferentes necesidades que presente (vivienda, empleo, alimentación, etc.).

# **3. Estructura de Datos y Módulos**

## **3.1 Modelo centrado en el recurso**

La arquitectura de datos prioriza los recursos sobre las entidades. El beneficiario y el conector ven primero el recurso específico (comedor, charla, grupo de apoyo) y se indica secundariamente a qué entidad pertenece. Este modelo rompe con el esquema tradicional centrado en la organización.

## **3.2 Tipos de contenido**

La plataforma organiza todos los recursos disponibles en tres tipos de contenido:

|  |  |  |
| --- | --- | --- |
| **Tipo** | **Descripción** | **Ejemplos** |
| **Grupos** | Espacios de participación continuada a los que el beneficiario se inscribe y asiste regularmente. | Comedor social, grupo de apoyo emocional, curso de finanzas, taller de motivación. |
| **Eventos** | Actividades puntuales con fecha y lugar definidos, de participación no recurrente. | Charla de extranjería, jornada de empleo, sesión informativa sobre vivienda. |
| **Librería** | Contenido informativo de consumo libre: no requiere inscripción. Tiene fines informativos y de orientación. | Podcasts, videos explicativos, guías de trámites, contactos de profesionales, recursos legales. |

## **3.3 Categorías de recursos**

Cada recurso (grupo, evento o elemento de librería) debe clasificarse dentro de una categoría principal y una subcategoría. La lista oficial de categorías y subcategorías se encuentra pendiente de entrega por parte del cliente (Lorena González Collado). Las categorías identificadas en la reunión como referencia inicial son:

* Económica — ingresos, ayudas, gestión financiera
* Social — alimentación, vivienda, integración comunitaria
* Legal — extranjería, documentación, defensa de derechos
* Salud — atención médica, salud mental, derivaciones sanitarias
* Empleo — orientación laboral, inserción, formación profesional
* Formación — educación, capacitación continua, idiomas

*PENDIENTE: El cliente entregará la lista oficial de categorías, subcategorías y atributos correspondientes para su estandarización e implementación.*

# **4. Módulos del MVP**

La primera fase del producto replica y parametriza la lógica de la plataforma LBR de Naowee, adaptándola a las necesidades específicas de AVIVLA. A continuación se describen los módulos que componen el MVP.

## **4.1 Módulo de Gestión de Entidades**

Permite al administrador registrar y gestionar las organizaciones participantes del ecosistema.

* Registro de nueva entidad con datos institucionales básicos
* Definición de áreas de intervención y cobertura geográfica
* Asociación de conectores a la entidad
* Gestión del catálogo de recursos por entidad (grupos, eventos, librería)
* Vista de administración: entidades activas, recursos publicados, conectores habilitados

## **4.2 Módulo de Gestión de Conectores**

Permite al administrador crear y gestionar los perfiles de los conectores, quienes son el actor central de la operación en el MVP.

* Creación de perfil de conector con credenciales de acceso
* Vinculación del conector a una o más entidades
* Panel de gestión de beneficiarios asignados
* Visualización de recursos disponibles en el catálogo
* Registro y actualización de expedientes de beneficiarios

## **4.3 Módulo de Registro de Beneficiarios (Mapa de Vida)**

Módulo central del MVP. El conector gestiona el registro completo del beneficiario. En esta fase, el beneficiario no interactúa directamente con la plataforma.

* Formulario de registro de datos personales del beneficiario
* Captura de consentimiento LOPD (obligatorio antes del registro)
* Entrevista estructurada del Mapa de Vida: diagnóstico multidimensional
* Dimensiones del diagnóstico: ingresos, vivienda, salud, documentación, empleo, formación
* Registro del núcleo familiar y posibilidad de asociar miembros de una misma familia
* Generación del expediente del beneficiario vinculado al conector y la entidad

## **4.4 Módulo de Asignación de Rutas**

Con base en el diagnóstico del Mapa de Vida, el conector construye el itinerario personalizado del beneficiario.

* Visualización de recursos disponibles filtrados por necesidad detectada
* Asignación del beneficiario a grupos, eventos y contenido de librería
* Un beneficiario puede pertenecer a múltiples grupos simultáneamente
* Registro del itinerario en el expediente del beneficiario
* Posibilidad de derivar al beneficiario a recursos de otras entidades dentro del ecosistema

## **4.5 Módulo de Seguimiento y Acompañamiento**

Permite al conector hacer seguimiento activo del progreso del beneficiario y actualizar su ruta.

* Actualización del estado del beneficiario en cada dimensión del Mapa de Vida
* Registro de novedades y cambios en el itinerario
* Sistema de notificaciones: eventos próximos, cambios en recursos, inactividad
* Trazabilidad de derivaciones entre entidades
* Cierre de expediente al alcanzar la autonomía definida

## **4.6 Módulo de Administración y Reportes**

Visión global del ecosistema para el administrador, orientada a la medición de impacto.

* Dashboard de métricas agregadas: beneficiarios activos, recursos más utilizados
* Detección de duplicidades entre entidades
* Reportes de impacto: tiempo medio de permanencia, itinerarios completados
* Exportación de datos para rendición de cuentas ante administraciones

# **5. Flujo Operativo del Sistema**

El flujo completo de la plataforma se organiza en cinco fases secuenciales. El diagrama detallado de cada fase se encuentra en el documento visual adjunto (avivla-flujo-completo-plataforma.html).

|  |  |  |  |
| --- | --- | --- | --- |
| **#** | **Fase** | **Actor principal** | **Resultado** |
| 1 | **Configuración del ecosistema** | Administrador | Entidades registradas, recursos publicados, conectores habilitados. |
| 2 | **Mapa de Vida** | Conector | Beneficiario registrado con diagnóstico multidimensional completo. |
| 3 | **Asignación de ruta** | Conector + Sistema | Itinerario personalizado creado y activado en la plataforma. |
| 4 | **Acompañamiento** | Conector | Seguimiento activo, derivaciones documentadas, progreso registrado. |
| 5 | **Medición de impacto** | Administrador | Expediente cerrado, métricas de autonomía registradas, reporte generado. |

# **6. Requerimientos Técnicos**

## **6.1 Requerimientos funcionales**

### **RF-01 — Gestión de entidades**

* El sistema debe permitir al administrador crear, editar y desactivar entidades.
* Cada entidad debe tener: nombre, tipo de organización, cobertura geográfica, áreas de intervención y estado (activa/inactiva).
* Una entidad puede tener múltiples conectores asociados.

### **RF-02 — Gestión de conectores**

* El sistema debe permitir al administrador crear cuentas de conector con credenciales únicas.
* El conector debe poder acceder a un panel con la lista de beneficiarios a su cargo.
* El conector debe poder consultar el catálogo completo de recursos disponibles.

### **RF-03 — Registro de beneficiarios**

* El registro de beneficiarios lo realiza exclusivamente el conector en el MVP.
* El sistema debe capturar consentimiento LOPD antes de iniciar el registro.
* El perfil del beneficiario debe incluir: datos personales, situación documental, núcleo familiar y diagnóstico del Mapa de Vida.
* El sistema debe permitir asociar miembros de una misma familia entre sí.

### **RF-04 — Mapa de Vida**

* El sistema debe incluir un formulario estructurado de entrevista con las dimensiones: ingresos, vivienda, salud, documentación, empleo y formación.
* El resultado del diagnóstico debe quedar registrado en el expediente del beneficiario.
* El formulario debe ser configurable para incorporar las preguntas específicas del cliente.

### **RF-05 — Gestión de recursos y catálogo**

* El catálogo debe organizarse en tres tipos: Grupos, Eventos y Librería.
* Cada recurso debe asociarse a una categoría, subcategoría y entidad.
* La interfaz debe mostrar primero el recurso y secundariamente la entidad a la que pertenece.
* El sistema debe permitir parametrizar la disponibilidad, capacidad y requisitos de cada recurso.

### **RF-06 — Asignación de itinerarios**

* El conector debe poder asignar al beneficiario a uno o más grupos, eventos y contenidos de librería.
* El sistema debe sugerir recursos relevantes con base en el diagnóstico registrado.
* Las derivaciones a recursos de otras entidades deben quedar documentadas con trazabilidad.

### **RF-07 — Notificaciones**

* El sistema debe enviar notificaciones al conector sobre eventos próximos de sus beneficiarios.
* Las notificaciones deben configurarse según el tipo de membresía o grupo del beneficiario.
* Lorena González Collado sugirió usar notificaciones para enviar ofertas de empleo a colectivos específicos.

## **6.2 Requerimientos no funcionales**

* RNF-01 — Cumplimiento LOPD: El sistema debe gestionar el consentimiento de datos conforme a la normativa española de protección de datos. El equipo legal del cliente está asesorando sobre los requerimientos específicos.
* RNF-02 — Seguridad: Autenticación segura para administradores y conectores. Los datos de beneficiarios deben estar cifrados en reposo y en tránsito.
* RNF-03 — Usabilidad: La interfaz del conector debe ser simple y operativa en contextos de atención directa (poco tiempo, posibles interrupciones).
* RNF-04 — Escalabilidad: La arquitectura debe permitir incorporar nuevos módulos y nuevas entidades sin rediseño estructural.
* RNF-05 — Parametrización: Las categorías, subcategorías y tipos de recursos deben ser configurables por el administrador sin intervención del equipo técnico.

# **7. Pendientes y Próximos Pasos**

Los siguientes ítems están pendientes de resolución para avanzar en el desarrollo del MVP. Se indican los responsables según lo acordado en la reunión del 19 de junio de 2026.

|  |  |  |  |
| --- | --- | --- | --- |
| **Pendiente** | **Descripción** | **Responsable** | **Estado** |
| Formulario de entrevista (Mapa de Vida) | Compartir el formato actual de preguntas utilizadas en las entrevistas con usuarios. | Lorena González Collado | **Pendiente** |
| Lista oficial de categorías y subcategorías | Listado completo con categorías, subcategorías y atributos de cada recurso. | Lorena González Collado | **Pendiente** |
| Demo de membresía (video) | Verificar estado del formulario de registro y preparar video demostrativo de la experiencia de usuario. | Danna Arrieta | **En curso** |
| Socialización con equipo técnico | Compartir estructura del proyecto con el equipo técnico para delimitar tareas y definir cronograma. | Danna Arrieta | **Este doc.** |
| Proyecto Francia (iglesia / centro cultural) | Analizar requerimientos del proyecto externo para posible integración al sistema base. | Lorena González Collado | **Post-agosto** |

## **7.1 Nota para el equipo técnico**

Este documento consolida la información levantada en la reunión del 19 de junio de 2026 y el análisis funcional previo. El alcance del MVP está definido; los únicos insumos pendientes para iniciar el desarrollo son la lista de categorías y subcategorías y el formulario del Mapa de Vida, ambos a cargo del cliente. Cualquier duda sobre el alcance o la terminología debe consultarse antes de iniciar la implementación para evitar retrabajo.

**Documentos complementarios entregados junto a este requerimiento:**

* avivla-flujo-completo-plataforma.html — Diagrama visual de todos los actores y fases
* avivla-flujo-registro-entidades.html — Flujo detallado de registro de entidades
