# AVIVLA: sketch del 3 de noviembre (contrastado con los insumos)

> **Estado:** 🚧 en desarrollo. Transcripción del sketch a mano alzada, reescrita con el vocabulario
> oficial de los insumos ([07](07-avivla-flujo-completo-plataforma.md), [12](12-reunion-avivla-2026-06-19-notas-gemini.md),
> [02](02-aceleradora-de-dignidad.md)). **Fecha clave anotada:** 15 de noviembre.

## Qué es

AVIVLA es una **plataforma de gestión de programas nacionales**: la infraestructura de coordinación
que conecta entidades, recursos y personas (identificar, diagnosticar, conectar, activar, medir).

## Contexto del problema

Personas inmigrantes en España. El sketch anota situaciones distintas según el origen y el oficio
(unos con situación difícil, otros con menos ayudas, otros explotados pese a estar bien). Se omite el
detalle por nacionalidad: en una plataforma de derechos humanos se lee como estereotipo y roza datos
de origen étnico, categoría especial.

## Actores

| Actor | Qué hace | ¿Usa la plataforma en el MVP? |
|---|---|---|
| **Administrador** | Registra entidades, define el catálogo de recursos y crea conectores. Ve métricas | Sí |
| **Conector** | **Puerta de entrada.** Recibe al beneficiario y opera todo su proceso | Sí |
| **Beneficiario** | Persona inmigrante. Responde, no opera | **No** (el autoservicio es fase posterior) |
| **Sistema** | Abre expediente, sugiere recursos, registra y alerta | n/a |
| **Entidad** | Aportante que ofrece recursos. **Propuesta (etapa 2):** decide las solicitudes a sus recursos desde una bandeja en la plataforma | No en el MVP según los docs; la bandeja es propuesta |

## Flujo (lo respaldado por los docs)

**Antes de todo (Administrador):** registra entidades, define el catálogo (grupos, eventos, librería) y crea los conectores.

1. El **beneficiario llega**: derivado por una entidad, contactando al Conector o por la landing.
2. El **Conector** recoge el consentimiento LOPD. Sin consentimiento, el proceso termina y no se registra nada.
3. El **Sistema** abre el expediente. El **Conector** registra el perfil básico.
4. El **Conector** aplica el **Mapa de Vida**; el beneficiario responde.
5. El **Sistema** sugiere recursos según el diagnóstico; el **Conector** los revisa y **asigna el itinerario**.
6. El beneficiario conoce su ruta. Si hace falta, el Conector gestiona la **derivación** a otra entidad.
7. El Sistema activa el itinerario (estado *En seguimiento*). Seguimiento por el Conector y cierre cuando el beneficiario alcanza su autonomía.

Fuentes: [06](06-avivla-bpmn-entrevista-asignacion.md), [07](07-avivla-flujo-completo-plataforma.md),
[08](08-avivla-flujo-mvp-registro-diagnostico.md), [12](12-reunion-avivla-2026-06-19-notas-gemini.md).

## Propuesta de producto: solicitud a un recurso (R/A)

El sketch solo dice «aplicar a servicios» y «R/A». Los docs no definen el proceso, así que todo esto es **propuesta para validar**
(revisada tras una auditoría contra los docs).

**Decisiones:**
- Decide la **entidad dueña del recurso**, dentro de la plataforma.
- En el MVP quien postula es el **Conector** (la persona no usa la plataforma). La **bandeja de la entidad** es etapa 2: al inicio el conector registra la solicitud y su resultado.
- Una **derivación** es una solicitud a un recurso de otra entidad y sigue los mismos estados.
- **El modo de acceso se define por recurso**, no por tipo:

| Modo | Ejemplo | ¿Hay decisión? |
|---|---|---|
| Libre | Librería, comedor sin reserva | No |
| Inscripción | Evento con cupo | No, solo cupo |
| Solicitud con decisión | Grupo con requisitos | Sí: la entidad aprueba o rechaza |
| Externo | Ingreso Mínimo Vital, SEPE, juzgado | La decide alguien fuera de la red; el conector acompaña y registra el resultado |

**Estados:**

```
Pendiente ──► Aprobada            → el conector activa el itinerario
   │      ──► Rechazada (motivo)  → se avisa al conector, que reasigna o deriva
   │      ──► En lista de espera  → cumple requisitos, sin cupo; pasa a Aprobada al liberarse
   └──► Falta información         → la entidad pide un dato; vuelve a Pendiente
```

| Estado | Fase | Qué dispara |
|---|---|---|
| Pendiente | MVP | El conector postula a la persona |
| Aprobada | MVP | La entidad acepta; hay cupo |
| Rechazada | MVP | La entidad rechaza; **motivo obligatorio** |
| En lista de espera | MVP | Cumple requisitos, no hay cupo |
| Falta información | MVP | La entidad pide un dato o documento (sin este estado se rechaza por defecto) |
| Retirada | Después | La persona desiste |
| Vencida | Después | La entidad no respondió en el plazo |

**Plazo de respuesta según urgencia:** no un único plazo. Un alojamiento o un acceso directo no pueden esperar 5 días hábiles; un curso sí.

**Notificaciones:** al conector. La persona sin cuenta no recibe nada, lo que le impide ejercer su derecho de acceso: como mínimo,
un resumen de su ruta por su canal preferido.

**Se apoya en lo que ya existe:** requisitos de acceso y capacidad (05, 08, 09), lista de espera y envío de documentación (04).
La herramienta del 04 ya trae una solicitud a la entidad, pero fuera de la plataforma.

## Propuesta de producto: uso del recurso

Después de **Aprobada**. Los docs solo dicen que la asistencia y el progreso «quedan registrados» (07 · 4.1), sin decir quién.

- **La entidad dueña del recurso registra** la asistencia y el avance (etapa 2, desde su bandeja; antes lo registra el conector).
- **Estados de participación:** Activa → **Completada** · **Abandonada** · **Suspendida** (por inasistencia).
- Se guarda fecha de inicio y fin, asistencia y una nota breve de cierre.
- **Lo que alimenta:** el conector ajusta la ruta; el sistema alerta por inactividad; al completarse un recurso avanza el cierre del itinerario; el Administrador ve métricas agregadas.

## Propuesta de producto: qué ve cada entidad de la persona

Parte del consentimiento **opcional** «comunicación con entidades colaboradoras» (03 · 6.3, 08) y de que una persona puede estar en varias entidades (12).
**Requiere validación del equipo legal** (05 · RNF-01): salud, violencia y origen son categorías especiales y un único check no es consentimiento específico por finalidad.

| Quién | Qué ve de la persona |
|---|---|
| **Conector** | Su expediente completo |
| **Entidad que recibe una postulación** | Lo mínimo para decidir: contacto básico, necesidades relevantes para ese recurso y documentos aportados. **No** el diagnóstico completo |
| **Entidad donde la persona participa** | Lo anterior, más su propio historial con ella (asistencia y notas) |
| **Otras entidades** | **Nada**, salvo consentimiento de comunicación: entonces, su itinerario y el estado de sus recursos, sin el detalle del diagnóstico |
| **Administrador** | Métricas agregadas (propuesta; el 05 pide detectar duplicidades entre entidades, y eso exige datos personales) |

**Reglas:**
- **Datos sensibles** (documentación, violencia, salud) solo con autorización expresa, campo por campo.
- **Notas internas** de cada entidad: privadas para esa entidad.
- **Todo acceso queda registrado:** quién vio qué y cuándo.
- **Caso protegido:** marca para víctimas de violencia. Asociar familiares y avisar por WhatsApp a un teléfono compartido puede exponerlas; ningún doc lo contempla.
- Qué puede ver la entidad que recibe **sin** consentimiento de comunicación queda **abierto**: es una decisión legal, no de producto.

## Propuesta: modelo genérico

Para que sirva a cualquier entidad que comparta programas, beneficios o subsidios (ciudadanos, artistas, deportistas),
se separa un **núcleo genérico** de la **configuración por vertical**. Mapa de Vida, Principios de DH y situación documental son configuración de la vertical migrante.

| Genérico | En AVIVLA hoy |
|---|---|
| Persona | Beneficiario |
| Caso (una persona, varios casos) | Expediente |
| Gestor (opcional) | Conector |
| Organización | Entidad |
| Programa / oferta + reglas de elegibilidad | Recurso + requisitos de acceso |
| Evaluación | Mapa de Vida |
| Solicitud → Decisión → Participación → Cierre | R/A y seguimiento |
| Consentimiento por finalidad | LOPD + comunicación con entidades |
| Registro de acceso | Trazabilidad |

**Vista «Mis programas»** para la persona: quién soy, mis programas por estado, qué puedo recibir y por qué, próximos pasos, quién vio mis datos y mis consentimientos.

**Camino por etapas:**
1. **Dentro del MVP:** registro asistido, Persona separada del Caso en el modelo de datos, modo de acceso por recurso, solicitud registrada por el conector. Sin panel de entidad.
2. **Después:** bandeja de la entidad y consentimiento por finalidad.
3. **Luego:** portal de la persona («Mis programas»).
4. **Al final:** convocatorias competitivas y pagos.

**Dónde se rompe:** convocatorias competitivas, ayudas económicas (pago y justificación) y menores (consiente el tutor). Se pueden aplazar.

## Decisiones tomadas (6-nov)

- **Diagnóstico:** base de **16 dimensiones** en 4 bloques; los 4 sistemas del 04 solo agrupan al mostrarlas.
- **Entidad:** se registra **siempre antes** de dar de alta a una persona, y tiene **bandeja propia desde el MVP** (decidir solicitudes, registrar asistencia, ver la ficha mínima). Los docs 05 y 07 no la contemplan: cambia el alcance.
- **Principios de DH:** son los derechos (vivienda, ingresos, alimentación, salud, educación…) que ordenan lo que ofrecen las entidades. Coinciden con las categorías del catálogo ([11](11-definicion-categorias-subcategorias-recursos.md)).
- **Fijos y ofertas:** un eje aparte del tipo de recurso. **Fijo** = permanente; **oferta** = temporal. Ambos pueden tener límites.
- **15 de noviembre:** se ignora.
- **Modo de acceso:** lo define la **entidad al crear el recurso**; el Administrador lo revisa al publicar el catálogo.
- **Plazos de respuesta:** por urgencia. **Urgente: 24 h; normal: 5 días hábiles.** El recurso trae su nivel de urgencia.
- **Usuarios de la entidad:** los crea el **Administrador**, igual que los conectores (RF-02).

| Límite | Fijo | Oferta |
|---|---|---|
| Cupo | Sí | Sí |
| Requisitos de elegibilidad | Sí | Sí |
| Territorio (distrito) | Sí | Sí |
| Máximo por persona | Sí | No |
| Fechas de inicio y fin | No | Sí |
| Plazo para solicitar | No | Sí |

## Superficies (APP | WEB | DB)

Los docs mencionan landing, panel del conector, panel de entidad y base de datos; ninguna app móvil. **Propuesta de asignación** por validar:

| Actor | Superficie |
|---|---|
| Conector | Web (panel), usable desde el móvil |
| Entidad | Web (bandeja) |
| Administrador | Web |
| Persona | Landing en el MVP; app o portal «Mis programas» en etapa 3 |
| Base de datos | Única y común, con registro de accesos |

## Por resolver

- [ ] **Validar con legal** la visibilidad entre entidades y el consentimiento por finalidad. Bloquea el MVP porque la entidad ya ve datos.
- [ ] Qué ve la bandeja de la entidad.
- [ ] Confirmar los límites de fijos y ofertas y la asignación de superficies.
- [ ] **Caso protegido** y cómo ejerce sus derechos una persona sin cuenta.
