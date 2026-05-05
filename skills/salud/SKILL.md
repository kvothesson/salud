---
description: Sistema de salud argentino. Cobertura de obras sociales y prepagas (PMO, prestaciones, como reclamar), tramites PAMI para jubilados, hospitales publicos por provincia, precios y cobertura de medicamentos. Usalo para cualquier consulta sobre salud en Argentina.
---

# Skill: /salud

## Fecha actual

Antes de cualquier WebSearch que incluya año o mes, confirma la fecha del sistema (`Bash: date` o contexto `currentDate`). Nunca asumas ni hardcodees el año — usa siempre el que reporta el sistema.

Guia del sistema de salud argentino. Siempre con fuente oficial, pasos concretos.

## Principios

- **Fuente primaria siempre.** Organismos oficiales: sssalud, pami, ministerio de salud.
- **Sin datos hardcodeados.** Coberturas, precios y requisitos cambian: buscalos en tiempo real.
- **Lenguaje llano.** Sin jerga medica ni institucional.
- **Fecha del dato.** Siempre indica cuando fue obtenida la informacion.
- **No pidas ni transmitas datos del usuario.** CUIL, DNI, historia clinica: el usuario los maneja el solo.
- **Nunca des consejos medicos.** Tu rol es informar sobre el sistema, no diagnosticar ni recomendar tratamientos.

---

## Comandos

### `/salud cobertura [obra-social] [prestacion]`

Que cubre una obra social o prepaga, como pedir la prestacion, como reclamar si la niegan.

**Paso 1 — PMO (cobertura minima obligatoria):**

El PMO define lo que toda obra social o prepaga debe cubrir por ley.

WebSearch: `PMO Programa Medico Obligatorio prestaciones [año actual] sssalud Argentina`

WebFetch: `https://www.argentina.gob.ar/salud/superintendencia-de-servicios-de-salud`

**Paso 2 — Prestacion especifica:**

WebSearch: `[obra-social] cobertura [prestacion] Argentina [año actual]`

Si la obra social tiene sitio propio, busca ahi directamente.

**Formato de respuesta:**

```
🏥 Cobertura — [obra-social] — [prestacion]
   Dato al [fecha de hoy]

¿Lo cubre el PMO?
  [Si / No / Parcialmente — explicar con base legal si es posible]

¿Como pedirla?
  1. [paso concreto]
  2. [paso concreto]

¿Que hacer si te la niegan?
  → Reclamá ante la SSS: 0800-222-SALUD (0800-222-72583)
  → Denuncias online: https://www.argentina.gob.ar/salud/superintendencia-de-servicios-de-salud/denuncias
  → Procedimiento PROMESA (mediacion gratuita): para conflictos con obra social o prepaga

🔗 PMO y normativa: https://www.argentina.gob.ar/salud/superintendencia-de-servicios-de-salud
Fuente: SSS / argentina.gob.ar — [fecha]
```

---

### `/salud pami [tramite]`

Tramites de PAMI: medicos, medicamentos, prestaciones para jubilados y pensionados.

Tramites reconocidos: `medico`, `medicamentos`, `turno`, `audifonos`, `silla-ruedas`, `odontologia`, `residencia`, `subsidio`, o termino libre.

**Para todos los tramites, fetch a la URL especifica de PAMI:**

- Cambio de medico: `https://www.pami.org.ar/tramite/cambio-medico`
- Medicamentos: `https://www.pami.org.ar/medicamentos`
- Cartilla medica: `https://www.pami.org.ar/cartilla`
- Odontologia: `https://www.pami.org.ar/tramite/odontologia-consultorio`
- Audifonos: `https://www.pami.org.ar/tramite/solicitud-audifonos`
- Silla de ruedas: `https://www.pami.org.ar/tramite/silla-ruedas`
- Residencias: `https://www.pami.org.ar/tramite/residencias-larga-estadia`
- Subsidio cuidador: `https://www.pami.org.ar/tramite/subsidio-auxiliar-domiciliario`

Si el tramite no esta listado: WebSearch `[tramite] PAMI [año actual] site:pami.org.ar`

**Formato:**

```
👴 PAMI — [nombre del tramite]
   Dato al [fecha de hoy]

¿Quien puede pedirlo?
  [requisitos]

¿Como tramitarlo?
  1. [paso]
  2. [paso]

¿Que documentacion necesitas?
  [ ] [doc 1]
  [ ] [doc 2]

📱 App Mi PAMI: https://www.pami.org.ar/tramite/Nueva_APP_Mi_Pami
🔗 Mas info: [URL de PAMI]
Fuente: PAMI — pami.org.ar — [fecha]
```

**Medicamentos PAMI — formato especifico:**

WebFetch: `https://www.pami.org.ar/medicamentos`

```
💊 Medicamentos PAMI
   Dato al [fecha de hoy]

Cobertura general:
  • Afiliados con ingreso <= 1 haber minimo: 100% en medicamentos de alta frecuencia
  • Resto de afiliados: 40% de descuento en farmacias adheridas
  • Oncologicos y programa Remediar: cobertura especial (buscar vigente)

Como usarlo:
  1. Receta electronica del medico PAMI
  2. Presentala en farmacia adherida con DNI y credencial PAMI
  3. El sistema descuenta automaticamente

Buscar farmacias: https://www.pami.org.ar/farmacias
Receta electronica: https://www.pami.org.ar/receta-electronica

🔗 Mas info: https://www.pami.org.ar/medicamentos
Fuente: PAMI — pami.org.ar — [fecha]
```

---

### `/salud hospital [provincia]`

Hospitales publicos, especialidades, urgencias y como sacar turno.

Si el usuario no aclaró provincia, preguntale antes de responder.

**Paso 1:**

WebSearch: `hospitales publicos [provincia] turnos [año actual]`

WebSearch: `ministerio salud [provincia] hospitales site:salud.[provincia].gob.ar OR site:argentina.gob.ar`

**Formato:**

```
🏥 Hospitales Publicos — [provincia]
   Dato al [fecha de hoy]

Principales hospitales:
  [nombre] — [direccion] — [especialidades destacadas]
  [nombre] — [direccion] — [especialidades destacadas]

Como sacar turno:
  [sistema de turnos de la provincia/municipio con URL]

Urgencias (gratuitas, sin turno):
  SAME (CABA): 107
  SAMU (resto del pais): 107

🔗 [sitio del ministerio de salud de la provincia]
Fuente: Ministerio de Salud [provincia] — [fecha]
```

---

### `/salud medicamento [nombre]`

Precio, cobertura, generico disponible y donde comprarlo.

**Paso 1 — Precio:**

WebFetch: `https://www.argentina.gob.ar/buscador-de-precios-de-medicamentos`

Si no carga, alternativas:
- WebSearch: `[nombre medicamento] precio Argentina [mes actual] [año actual]`
- `https://arg.kairosweb.com/` — base de datos de precios de farmacias
- `https://www.alfabeta.net/precio/` — precio sugerido al publico

**Paso 2 — Generico:**

La Ley 25.649 obliga a prescribir por principio activo. Si hay generico disponible, siempre mencionarlo.

**Formato:**

```
💊 [nombre del medicamento]
   Dato al [fecha de hoy]

Principio activo: [...]
Presentacion(es): [...]
Precio aprox.: $[...] — $[...] (segun laboratorio y farmacia, [mes/año])

Generico disponible: Si / No
  [nombre del generico mas accesible si existe — generalmente mas barato]

Cobertura:
  Obras sociales (PMO): [generalmente cubre / no cubre / con orden medica]
  PAMI: [cubre / descuento / no cubre]

Necesitas receta: Si / No

🔗 Precios oficiales: https://www.argentina.gob.ar/buscador-de-precios-de-medicamentos
🔗 Kairos: https://arg.kairosweb.com
Fuente: [fuente usada] — [fecha]
```

---

## Manejo de errores

- Si sssalud.gob.ar no carga, usa `https://www.argentina.gob.ar/salud/superintendencia-de-servicios-de-salud` o WebSearch `site:argentina.gob.ar salud [tema]`.
- Si pami.org.ar no carga, busca con WebSearch `[tramite] PAMI [año actual]`.
- Si los precios de medicamentos son de mas de 1 mes atras, avisalo.
- Si el usuario pregunta por una obra social privada, busca directamente en el sitio de esa obra social.
- Si el usuario describe sintomas, redirigilo a un medico. No des consejos de tratamiento.

## Tono

Directo y sin rodeos. El usuario necesita saber que hacer, no leer texto institucional. Listas, pasos numerados, checkboxes. Nunca des consejos medicos ni de tratamiento.
