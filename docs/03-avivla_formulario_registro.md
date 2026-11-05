## Perfil Básico
| AVIVLA — Formulario de Registro: Perfil Básico de la Persona | Unnamed: 1 | Unnamed: 2 | Unnamed: 3 | Unnamed: 4 | Unnamed: 5 | Unnamed: 6 |
| --- | --- | --- | --- | --- | --- | --- |
| Gestionado por el Conector · MVP v1.0 · Fuente: Lorena González Collado | NaN | NaN | NaN | NaN | NaN | NaN |
| 🟢 Obligatorio   🟡 Opcional   🔵 Automático (sistema) | NaN | NaN | NaN | NaN | NaN | NaN |
| # | Sección | Campo | Tipo de dato | Valores / Opciones | Obligatoriedad | Notas |
| 1.1 | 👤 Datos Personales | Nombre | Texto | — | Obligatorio | NaN |
| 1.2 | 👤 Datos Personales | Apellidos | Texto | — | Obligatorio | NaN |
| 1.3 | 👤 Datos Personales | Fecha de nacimiento | Fecha | DD/MM/AAAA | Obligatorio | NaN |
| 1.4 | 👤 Datos Personales | DNI / NIE / Pasaporte | Texto | — | Opcional | No requerido en fase inicial |
| 1.5 | 👤 Datos Personales | ¿Tiene documento nacional? | Selección | Sí / No / En trámite | Obligatorio | NaN |
| 1.6 | 👤 Datos Personales | Fotografía | Imagen | Archivo JPG / PNG | Opcional | NaN |
| 2.1 | 📱 Contacto | Teléfono | Número | +34 XXX XXX XXX | Obligatorio | Canal principal de contacto |
| 2.2 | 📱 Contacto | Email | Texto / Email | formato@dominio.com | Opcional | NaN |
| 3.1 | 📍 Ubicación | Municipio | Texto | — | Obligatorio | NaN |
| 3.2 | 📍 Ubicación | Código postal | Número | XXXXX | Obligatorio | NaN |
| 3.3 | 📍 Ubicación | Dirección exacta | — | — | — | No se solicita en esta fase · privacidad |
| 4.1 | 🌐 Idioma preferente | Idioma preferente | Selección | Español · Catalán · Inglés · Árabe · Francés · Otro | Obligatorio | NaN |
| 5.1 | 💬 Canal de comunicación | Canal preferido | Selección | WhatsApp · Teléfono · Email | Obligatorio | NaN |
| 6.1 | ⚖️ Consentimientos LOPD | Política de privacidad | Checkbox | Acepto / No acepto | Obligatorio | Bloqueante: sin este no se crea expediente |
| 6.2 | ⚖️ Consentimientos LOPD | Tratamiento de datos personales | Checkbox | Autorizo / No autorizo | Obligatorio | Bloqueante: sin este no se crea expediente |
| 6.3 | ⚖️ Consentimientos LOPD | Comunicación con entidades colaboradoras | Checkbox | Autorizo / No autorizo | Opcional | NaN |
| 6.4 | ⚖️ Consentimientos LOPD | Recibir comunicaciones del expediente | Checkbox | Deseo recibir / No deseo | Opcional | NaN |
| 7.1 | 🔵 Datos Automáticos (Sistema) | Número único AVIVLA | Auto | Generado por sistema | Automático | ID único del expediente |
| 7.2 | 🔵 Datos Automáticos (Sistema) | Fecha de alta | Auto / Fecha | DD/MM/AAAA HH:MM | Automático | NaN |
| 7.3 | 🔵 Datos Automáticos (Sistema) | Entidad que realiza el alta | Auto | Vinculada al conector | Automático | NaN |
| 7.4 | 🔵 Datos Automáticos (Sistema) | Conector asignado | Auto | Usuario activo en sesión | Automático | NaN |
| 7.5 | 🔵 Datos Automáticos (Sistema) | Estado del expediente | Auto | Abierto / En seguimiento / Cerrado | Automático | Estado inicial: Abierto |
| 7.6 | 🔵 Datos Automáticos (Sistema) | Notas internas | Texto libre | — | Opcional | Campo editable por el conector |

## Diagnóstico de Necesidades
| AVIVLA — Formulario de Diagnóstico: Mapa de Necesidades | Unnamed: 1 | Unnamed: 2 | Unnamed: 3 | Unnamed: 4 | Unnamed: 5 | Unnamed: 6 | Unnamed: 7 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Aplicado por el Conector durante la entrevista · Parte 2 del registro · MVP v1.0 | NaN | NaN | NaN | NaN | NaN | NaN | NaN |
| 🟢 Sin necesidad inmediata    🟡 Necesidad moderada / apoyo puntual    🔴 Necesidad urgente / intervención | NaN | NaN | NaN | NaN | NaN | NaN | NaN |
| # | Bloque | Dimensión | Pregunta al usuario | 🟢 Verde | 🟡 Amarillo | 🔴 Rojo | Categorías relacionadas |
| 1.1 | Bloque 1 · Necesidades Básicas | 🏠 Vivienda | ¿Cuál es tu situación actual de vivienda? | Tengo una vivienda estable | Mi situación es temporal o inestable | Necesito buscar vivienda inmediatamente | Vivienda |
| 1.2 | Bloque 1 · Necesidades Básicas | 💶 Ingresos | ¿Cuál es tu situación económica actual? | Tengo una fuente de ingresos estable | Mis ingresos son insuficientes o inestables | No tengo ninguna fuente de ingresos | Ingresos |
| 1.3 | Bloque 1 · Necesidades Básicas | 🍽 Alimentación | Respecto a tu alimentación… | Cubro mis necesidades alimentarias | Necesito apoyo en la cesta o banco de alimentos | Necesito un comedor social | Alimentación |
| 1.4 | Bloque 1 · Necesidades Básicas | ❤️ Salud y Bienestar | ¿Cómo te encuentras actualmente? | Me encuentro bien | Hay aspectos que me gustaría mejorar | Necesito apoyo sanitario o psicológico | Salud y Bienestar |
| 1.5 | Bloque 1 · Necesidades Básicas | 📄 Documentación | Respecto a tus documentos y gestiones… | Todo está al día | Tengo trámites administrativos pendientes | Necesito ayuda legal | Documentación y Trámites |
| 2.1 | Bloque 2 · Entorno Familiar | 🤝 Red de Apoyo | Cuando necesito ayuda… | Tengo una red de apoyo sólida | Tengo una red de apoyo inestable | Me ayudaría tener una red de apoyo estable | Red de Apoyo |
| 2.2 | Bloque 2 · Entorno Familiar | 🌱 Familia | ¿Cuál es tu situación familiar actual? | Vivo con familiares o personas cercanas | Tengo familia pero no convivimos | Me encuentro solo/a y sin apoyo familiar | Familia |
| 2.3 | Bloque 2 · Entorno Familiar | 👶 Infancia y Menores | ¿Tienes menores a cargo? | No tengo menores a cargo | Tengo menores y cubro adecuadamente sus necesidades | Tengo menores y necesito apoyo para atenderlos | Infancia y Menores |
| 2.4 | Bloque 2 · Entorno Familiar | 👩 Mujer y Cuidados (Opcional) | ¿Cuál de estas situaciones describe mejor tu realidad? | No tengo responsabilidades de cuidado que limiten mi autonomía | Soy madre o cuidadora principal y necesito más apoyo | Estoy viviendo una situación de violencia o riesgo familiar | Mujer y Cuidados |
| 3.1 | Bloque 3 · Autonomía | 💼 Empleo | ¿Cuál es tu situación laboral? | Tengo una situación laboral estable | Quiero orientación laboral | Quiero buscar empleo activamente | Empleo |
| 3.2 | Bloque 3 · Autonomía | 🎓 Formación | Respecto a tu formación… | Tengo la formación que necesito actualmente | Me gustaría adquirir nuevas habilidades | Necesito formación para acceder a oportunidades | Formación |
| 3.3 | Bloque 3 · Autonomía | 🚗 Movilidad | Respecto a tus desplazamientos… | Me desplazo sin dificultad | Tengo limitaciones económicas para desplazarme | Tengo limitaciones físicas para desplazarme | Movilidad |
| 3.4 | Bloque 3 · Autonomía | 💻 Competencias Digitales | Respecto al uso de tecnología… | Manejo internet y herramientas digitales con facilidad | Quiero mejorar mis habilidades digitales | Necesito ayuda para realizar gestiones digitales | Competencias Digitales |
| 3.5 | Bloque 3 · Autonomía | 🧍 Autonomía Personal (Opcional) | Respecto a tu autonomía en el día a día… | Soy autónomo/a para gestionar mi vida diaria | Algunas tareas me resultan difíciles, necesito apoyo puntual | Necesito ayuda frecuente para mi cuidado diario | Autonomía Personal y Cuidados |
| 4.1 | Bloque 4 · Participación | 🧭 Organización y Dirección | Respecto a tus próximos pasos… | Tengo objetivos claros y sé cómo avanzar | Tengo objetivos claros pero necesito apoyo para alcanzarlos | No sé cuál debería ser mi siguiente paso | Organización y Dirección |
| 4.2 | Bloque 4 · Participación | 🌱 Participación y Comunidad | Respecto a tu entorno social… | Participo activamente en alguna comunidad | Me gustaría conectar más con otras personas | Me siento aislado/a | Participación y Comunidad |

## Resumen Estructura
| AVIVLA — Estructura del Formulario de Registro | Unnamed: 1 | Unnamed: 2 | Unnamed: 3 | Unnamed: 4 |
| --- | --- | --- | --- | --- |
| Dos partes secuenciales en la misma sesión · Gestionado por el Conector | NaN | NaN | NaN | NaN |
| NaN | NaN | NaN | NaN | NaN |
| PARTE 1 — REGISTRO DE LA PERSONA | NaN | NaN | NaN | NaN |
| Paso | Sección | Campos | Obligatoriedad | Notas |
| 1 | Contacto con la persona | — | — | El conector explica el proceso y los datos a recopilar |
| 2 | ⚖️ Consentimientos LOPD | 4 | 2 oblig. / 2 opcionales | 2 obligatorios bloqueantes · sin ellos no se crea expediente |
| 3 | 👤 Datos personales | 6 | 4 oblig. / 2 opcionales | No se pide dirección exacta · solo municipio y CP |
| 4 | 📱 Contacto | 2 | 1 oblig. / 1 opcional | Teléfono obligatorio · email opcional |
| 5 | 📍 Ubicación | 2 | 2 obligatorios | Municipio y código postal únicamente |
| 6 | 🌐 Idioma y canal | 2 | 2 obligatorios | NaN |
| 7 | 🔵 Datos automáticos sistema | 6 | Automáticos | Generados por el sistema al crear el expediente |
| NaN | NaN | NaN | NaN | NaN |
| NaN | NaN | NaN | NaN | NaN |
| PARTE 2 — DIAGNÓSTICO DE NECESIDADES | NaN | NaN | NaN | NaN |
| Bloque | Dimensiones | Cant. | Semáforo | Categorías activadas |
| Bloque 1 · Necesidades Básicas | Vivienda · Ingresos · Alimentación · Salud · Documentación | 5 | 🟢🟡🔴 | Vivienda · Ingresos · Alimentación · Salud · Documentación |
| Bloque 2 · Entorno Familiar | Red de apoyo · Familia · Menores · Mujer y cuidados | 4 | 🟢🟡🔴 | Red de Apoyo · Familia · Infancia y Menores · Mujer y Cuidados |
| Bloque 3 · Autonomía | Empleo · Formación · Movilidad · Digital · Autonomía personal | 5 | 🟢🟡🔴 | Empleo · Formación · Movilidad · Competencias Digitales · Autonomía |
| Bloque 4 · Participación | Organización · Comunidad | 2 | 🟢🟡🔴 | Organización y Dirección · Participación y Comunidad |
| NaN | NaN | NaN | NaN | NaN |
| TOTAL DIMENSIONES DIAGNÓSTICO | NaN | 16 | NaN | NaN |
