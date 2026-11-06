# AVIVLA: índice de la investigación

> **Estado:** 🚧 en desarrollo. Mapa de los documentos de `docs/`. Los originales (PDF, xlsx, docx, html)
> están en [`insumos/`](insumos/); los `.md` son su conversión, numerada en orden alfabético, no cronológico.
> El **01** es la excepción: es el sketch del 3-nov y está escrito con el vocabulario de los demás.

## Qué es AVIVLA

Plataforma que conecta entidades, recursos y personas inmigrantes en España: en lugar de que cada
organización gestione su parte del puzzle por separado, una infraestructura común coordina el
itinerario de la persona (identificar, diagnosticar, conectar, activar, medir). MVP: registro
gestionado por personal, sin autoservicio.

## Glosario (el vocabulario que manda)

| Término | Significado |
|---|---|
| **Administrador** | Gestiona entidades, recursos y conectores |
| **Entidad** | Organización aliada; contenedor de recursos |
| **Recurso** | Lo que el beneficiario ve y recibe. El modelo está centrado en el recurso, no en la entidad |
| **Conector** | Profesional o voluntario; puerta de entrada: recibe al beneficiario y opera todo su proceso. En el MVP el beneficiario no usa la plataforma |
| **Beneficiario** | Persona inmigrante con necesidades |
| **Mapa de Vida** | Entrevista de diagnóstico que aplica el Conector. Tiene 3 versiones en los docs (6 dimensiones, 16 en 4 bloques, 4 sistemas): vigente por confirmar |
| **Grupos / Eventos / Librería** | Organización de los datos acordada el 19-jun |

## Por dónde empezar

| Si quieres… | Lee |
|---|---|
| Entender la idea en 5 minutos | 02, luego 01 |
| Saber qué se decidió y por qué | 12 |
| Ver cómo funciona la plataforma de punta a punta | 07 |
| Diseñar el registro y el diagnóstico | 08, 03, 04 |
| Trabajar el catálogo de recursos | 11 |
| Estimar o construir | 05 |

## Documentos

### Visión y contexto
| # | Documento | Qué contiene |
|---|---|---|
| 01 | [Sketch del 3-nov](01-avivla-sketch-3-nov.md) | Idea de la plataforma, actores y flujo, con términos nivelados y pendientes |
| 02 | [Aceleradora de Dignidad](02-aceleradora-de-dignidad.md) | Presentación de la visión: del sistema centrado en entidades al centrado en la persona |
| 10 | [AVIVLA](10-avivla.md) | Perfil básico, consentimientos y formulario del Mapa de Vida por bloques |

### Decisiones
| # | Documento | Qué contiene |
|---|---|---|
| 12 | [Reunión 19-jun-2026](12-reunion-avivla-2026-06-19-notas-gemini.md) | Alcance del MVP, terminología, estructura operativa y próximos pasos por responsable |

### Flujos
| # | Documento | Qué contiene |
|---|---|---|
| 07 | [Flujo completo de la plataforma](07-avivla-flujo-completo-plataforma.md) | Los 4 actores y todas las fases del ecosistema |
| 08 | [Flujo MVP: registro y diagnóstico](08-avivla-flujo-mvp-registro-diagnostico.md) | El tramo de registro y diagnóstico del beneficiario |
| 09 | [Flujo: registro de entidades](09-avivla-flujo-registro-entidades.md) | Autorregistro de la entidad desde la landing (el 05 y el 12 dicen que la da de alta el Administrador; anexo del 05, posible fase futura) |
| 06 | [BPMN: entrevista y asignación](06-avivla-bpmn-entrevista-asignacion.md) | Proceso de entrevista y asignación de recursos |

### Datos y formularios
| # | Documento | Qué contiene |
|---|---|---|
| 03 | [Formulario de registro](03-avivla_formulario_registro.md) | Perfil básico y diagnóstico de necesidades |
| 04 | [Mapa de vida (herramienta)](04-avivla_mapa_vida.md) | Sistemas, subáreas, cuestionario, recursos, puentes y cursos |
| 11 | [Categorías, subcategorías y recursos](11-definicion-categorias-subcategorias-recursos.md) | Catálogo completo y resumen por categoría |

### Técnico
| # | Documento | Qué contiene |
|---|---|---|
| 05 | [Requerimientos técnicos MVP v1](05-avivla_requerimientos_tecnicos_mvp_v1.md) | Requerimientos del MVP |

## Advertencias

- **Contradicciones entre documentos** (auditoría del 6-nov): la versión vigente del diagnóstico, si la entidad debe existir antes del alta y quién da de alta a la entidad no están resueltas. Ver "Por resolver" en el 01.

- **El 12 son notas generadas por Gemini**: pueden tener errores de transcripción; contrastar con el 05.
- **Los flujos HTML (04, 06 a 09) perdieron el diagrama** al convertirse: solo conservan el texto. La fuente visual sigue en `insumos/`.
- `10` tiene aproximadamente un 11% menos de palabras que su PDF, probablemente encabezados y pies repetidos; no se verificó.
- Puede haber solapes entre `03`, `04`, `10` y `11` (todos tocan el diagnóstico y las categorías); está por reconciliarse cuál es la versión vigente.
