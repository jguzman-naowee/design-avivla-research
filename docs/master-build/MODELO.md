# Software base: modelo

> **Estado:** 🚧 borrador para validar. Nombre del producto por definir (ver "Nombre"). AVIVLA es la **primera capa de cliente** montada sobre este software, no el producto.

## Qué es

Un software para que **cualquier organización comparta programas, beneficios o subsidios** con personas identificadas, y para que **la persona sepa en qué programas está, qué puede recibir y por dónde empezar**.

**El problema:** cada organización atiende un trozo y la persona va de ventanilla en ventanilla, o directamente no sabe qué tiene, a dónde ir ni por dónde empezar.

**A quién se vende:** organizaciones que comparten programas y administraciones públicas.

## Principios

1. **Un núcleo, muchas capas.** Lo común vive en el software base. Lo propio de cada cliente (vocabulario, formularios, reglas, programas) vive en una capa de configuración, nunca en el código.
2. **La persona primero.** Se identifica una vez. Todo lo que se sabe de ella (perfil, evaluación, consentimientos) forma una sola base de conocimiento, y el registro la usa completa.
3. **Consentimiento por finalidad y acceso registrado.** Ninguna organización ve más de lo necesario. Todo acceso queda anotado y la persona puede verlo.
4. **Idiomas desde el diseño.** Español neutro por defecto; todo texto visible sale de catálogos de traducción, no del código.
5. **Nada hardcodeado a un cliente.** Si hay que tocar código para cambiar un nombre, un campo o una regla, está mal modelado.
6. **Sin registro no hay beneficios.** Toda persona se registra: la idea es centralizar a quienes necesitan. La cuenta la crea la propia persona o un gestor que la acompaña, siempre con su consentimiento.

## El núcleo

| Concepto | Qué es |
|---|---|
| **Persona** | Quien recibe. Identidad única, independiente de cualquier programa |
| **Perfil** | Lo que se sabe de la persona: datos básicos, contacto, situación. Campos definidos por la capa |
| **Evaluación** | Diagnóstico estructurado con dimensiones y semáforo. Definido por la capa (en AVIVLA, el Mapa de Vida) |
| **Caso** | La relación de una persona con un cliente o programa: estado, gestor, itinerario. Una persona puede tener varios |
| **Gestor** *(opcional)* | Quien acompaña a la persona. Un rol, no un requisito |
| **Organización** | Quien ofrece programas |
| **Programa** | Lo que se ofrece. Ver atributos abajo |
| **Solicitud** | Una persona pide acceso a un programa |
| **Decisión** | La respuesta de la organización: aprobada, rechazada con motivo, lista de espera |
| **Participación** | Uso del programa: activa, completada, abandonada, suspendida; con asistencia y avance |
| **Consentimiento** | Autorización de la persona para una finalidad concreta, con fecha y revocable |
| **Registro de acceso** | Quién vio qué dato de quién, cuándo y para qué |

### Atributos de un programa

| Atributo | Valores |
|---|---|
| **Categoría** | Un derecho o área definida por la capa (en AVIVLA: vivienda, ingresos, alimentación, salud, educación…) |
| **Tipo** | Grupo, evento o contenido (en AVIVLA: grupo, evento, librería) |
| **Vigencia** | Fijo (permanente) u oferta (temporal) |
| **Modo de acceso** | Libre · inscripción · solicitud con decisión · externo (lo decide alguien fuera de la red; el gestor registra el resultado) |
| **Urgencia** | Urgente (respuesta en 24 h) o normal (5 días hábiles) |
| **Límites** | Cupo, requisitos de elegibilidad, territorio, máximo por persona (fijos), fechas y plazo para solicitar (ofertas) |

### Flujo común

```
Persona identificada ─► Evaluación ─► Programas sugeridos ─► Solicitud ─► Decisión ─► Participación ─► Cierre
                              ▲                                   │
                       (gestor opcional acompaña y registra)      └─► Rechazada / lista de espera ─► reasignar o derivar
```

### Registro único y no duplicidad

Toda entrega o participación **se acredita** en el registro único de la persona. Antes de entregar, la organización consulta si la persona ya recibió ese beneficio en el periodo y, si sí, el sistema responde **«no disponible»**.

- **Topes por derecho y periodo**, definidos por la capa: p. ej. una comida al día, una ayuda de alquiler al mes.
- **Sin solapes de horario:** nunca dos eventos a la misma hora.
- **Mínima revelación:** la organización que consulta solo ve «no disponible hoy»; no dónde recibió ni qué más tiene.
- **Se registran también los intentos bloqueados**, para auditoría.
- Los topes se aplican entre **todas** las organizaciones del cliente, no solo dentro de una.

*Propuesta nueva: los insumos solo piden «detección de duplicidades entre entidades» (05 §4.6). Requiere validación legal, porque exige compartir entre organizaciones que hubo una entrega.*

### Estados de la solicitud

`Pendiente` → `Aprobada` · `Rechazada (motivo obligatorio)` · `En lista de espera` · `Falta información` (vuelve a Pendiente). Después: `Retirada`, `Vencida`.

### Visibilidad (regla base, configurable por capa)

| Quién | Ve de la persona |
|---|---|
| Gestor | Su caso completo |
| Organización que recibe una solicitud | Lo mínimo para decidir |
| Organización donde la persona participa | Lo anterior y su propio historial |
| Otras organizaciones | Nada, salvo consentimiento específico |
| Administrador | Métricas agregadas |

Datos sensibles solo con autorización expresa, campo por campo. **Caso protegido:** marca que restringe avisos y asociaciones para quien podría correr riesgo (p. ej. violencia).

## La persona: una sola base de conocimiento

El registro no es un formulario suelto. Alimenta **toda la capa de conocimiento de la persona**:

1. **Identidad y contacto**, con el canal preferido.
2. **Perfil** según la capa.
3. **Evaluación** por dimensiones, con semáforo, que se repite en el tiempo.
4. **Consentimientos** vigentes, por finalidad.
5. **Casos y programas**, con su estado.
6. **Historial de accesos:** quién vio sus datos.

Con esa base, la persona (o su gestor) ve **«Mis programas»**: quién soy, en qué programas estoy, qué puedo recibir y por qué, próximos pasos, quién vio mis datos.

## Capas de cliente

Cada cliente se monta como **un archivo JSON** con su organización y sus reglas. El software lo lee y se reconfigura sin tocar código.

```json
{
  "cliente": { "id": "avivla", "nombre": "AVIVLA", "idiomas": ["es", "en"], "idiomaPorDefecto": "es" },
  "vocabulario": {
    "persona": "Beneficiario", "gestor": "Conector", "caso": "Expediente",
    "organizacion": "Entidad", "programa": "Recurso", "evaluacion": "Mapa de Vida"
  },
  "roles": [
    { "id": "admin", "ve": "agregado", "crea": ["organizacion", "gestor", "usuarioOrganizacion"] },
    { "id": "gestor", "opcional": false, "ve": "casoCompleto" },
    { "id": "organizacion", "ve": "minimoParaDecidir", "tieneBandeja": true }
  ],
  "perfil": { "campos": [
    { "id": "municipio", "tipo": "texto", "obligatorio": true },
    { "id": "codigoPostal", "tipo": "texto", "obligatorio": true },
    { "id": "idioma", "tipo": "lista", "obligatorio": true },
    { "id": "documentacion", "tipo": "lista", "sensible": true }
  ]},
  "evaluacion": {
    "nombre": "Mapa de Vida",
    "bloques": [{ "id": "b1", "dimensiones": ["vivienda", "ingresos", "salud", "documentacion"] }],
    "semaforo": ["estable", "enProceso", "necesitaApoyo"],
    "vistaAgrupada": ["economico", "social", "relacional", "legal"]
  },
  "categorias": ["vivienda", "ingresos", "alimentacion", "salud", "educacion"],
  "tiposPrograma": ["grupo", "evento", "contenido"],
  "reglas": {
    "modosAcceso": ["libre", "inscripcion", "solicitud", "externo"],
    "plazosRespuesta": { "urgente": "24h", "normal": "5dHabiles" },
    "estadosSolicitud": ["pendiente", "aprobada", "rechazada", "listaEspera", "faltaInformacion"],
    "visibilidad": { "otrasOrganizaciones": "nadaSalvoConsentimiento" },
    "casoProtegido": true,
    "topes": [{ "derecho": "alimentacion", "max": 1, "por": "dia" }, { "derecho": "vivienda", "max": 1, "por": "mes" }],
    "sinSolapeHorario": true
  },
  "consentimientos": [
    { "id": "tratamiento", "obligatorio": true },
    { "id": "comunicacionEntidades", "obligatorio": false }
  ],
  "organizaciones": [],
  "programas": []
}
```

Esto es un esbozo para fijar la forma, no el esquema final. Un cliente distinto (artistas, deportistas) cambia vocabulario, evaluación, categorías y reglas; el núcleo no se toca.

## Idiomas

Español neutro por defecto. Cada texto visible tiene una clave y una traducción por idioma; la capa declara los idiomas que habilita. Sumar un idioma es agregar un catálogo, no cambiar pantallas.

## Nombre

Elegido: **Brújula Ciudadana**. Las propuestas descartadas quedan abajo como referencia.

Propuestas (sin revisar disponibilidad ni marcas):

| Nombre | Por qué |
|---|---|
| **Brújula** | Responde al «no sabe a dónde ir ni por dónde empezar» |
| **Umbral** | El primer paso: la puerta de entrada |
| **Trama** | Une organizaciones, programas y personas en un tejido |
| **Cauce** | Da un camino a la persona y a los recursos |
| **Nexo** | Conecta; corto y fácil en otros idiomas |
| **Ruta** | Directo: la persona sabe su camino |

## Fuera de alcance por ahora

Convocatorias competitivas (se decide comparando a todos), pagos y justificación de ayudas, y menores (consiente el tutor).

## Por resolver

- [ ] Nombre del producto.
- [ ] Qué ve la bandeja de la organización (propuesta: ficha mínima, asistencia, su historial).
- [ ] Validación legal: consentimiento por finalidad, categorías especiales, qué ve una organización sin consentimiento.
- [ ] Esquema final del JSON de capa y dónde vive (repositorio, base de datos o ambos).
- [ ] Cómo ejerce sus derechos una persona sin cuenta.
