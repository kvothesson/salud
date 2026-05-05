# salud

Plugin de Claude Code — sistema de salud argentino navegable.

## Que hace

`/salud` te ayuda a entender que cubre tu obra social, como hacer tramites en PAMI, donde esta el hospital publico mas cercano y cuanto cuesta un medicamento. Siempre con fuente oficial y datos del momento.

## Instalacion

```bash
claude --plugin-dir /ruta/a/salud
```

## Comandos y ejemplos

### `/salud cobertura OSDE psicologia`

```
🏥 Cobertura — OSDE — Psicologia
   Dato al 4 may 2026

¿Lo cubre el PMO?
  Si. El PMO (Resolucion SSS 1991/2005 y actualizaciones) incluye cobertura
  de salud mental: sesiones de psicologo/psiquiatra con orden medica.

¿Como pedirla?
  1. Pedile una orden a tu medico de cabecera o pedila directamente en OSDE
  2. Busca un profesional en la cartilla de OSDE (osde.com.ar/cartilla)
  3. Presenta la orden en cada sesion — OSDE cubre un porcentaje segun el plan

¿Que hacer si te la niegan?
  → Reclamá ante la SSS: 0800-222-SALUD (0800-222-72583)
  → Denuncias online: https://www.argentina.gob.ar/salud/superintendencia-de-servicios-de-salud/denuncias
  → Procedimiento PROMESA (mediacion gratuita): para conflictos con obra social o prepaga

🔗 PMO y normativa: https://www.argentina.gob.ar/salud/superintendencia-de-servicios-de-salud
Fuente: SSS / argentina.gob.ar — 4 may 2026
```

---

### `/salud pami medicamentos`

```
💊 Medicamentos PAMI
   Dato al 4 may 2026

Cobertura general:
  • Afiliados con ingreso <= 1 haber minimo: 100% en medicamentos de alta frecuencia
  • Resto de afiliados: 40% de descuento en farmacias adheridas
  • Oncologicos y programa Remediar: cobertura especial

Como usarlo:
  1. Receta electronica del medico PAMI
  2. Presentala en farmacia adherida con DNI y credencial PAMI
  3. El sistema descuenta automaticamente

Buscar farmacias: https://www.pami.org.ar/farmacias
Receta electronica: https://www.pami.org.ar/receta-electronica

🔗 Mas info: https://www.pami.org.ar/medicamentos
Fuente: PAMI — pami.org.ar — 4 may 2026
```

---

### `/salud medicamento ibuprofeno`

```
💊 Ibuprofeno
   Dato al 4 may 2026

Principio activo: Ibuprofeno
Presentaciones: 400mg, 600mg — comprimidos / suspension

Precio aprox.: $2.800 — $6.500 (segun laboratorio y farmacia, may 2026)

Generico disponible: Si
  Ibuprofeno (marca generica) — hasta 50% mas barato que marcas comerciales como Ibupirac o Actron

Cobertura:
  Obras sociales (PMO): cubre con receta medica en muchos planes
  PAMI: descuento del 40% en farmacias adheridas (consultar lista de frecuentes)

Necesitas receta: No (venta libre hasta 400mg, con receta para dosis mayores)

🔗 Precios oficiales: https://www.argentina.gob.ar/buscador-de-precios-de-medicamentos
🔗 Kairos: https://arg.kairosweb.com
Fuente: argentina.gob.ar / kairosweb.com — may 2026
```

---

### `/salud hospital CABA`

```
🏥 Hospitales Publicos — CABA
   Dato al 4 may 2026

Principales hospitales:
  Hospital Ramos Mejia — Urquiza 609, CABA — Guardia general, cirugia, maternidad
  Hospital Italiano (publico de referencia) — Gascon 450 — Polivalente
  Hospital Garrahan — Combate de los Pozos 1881 — Pediatria de alta complejidad
  Hospital de Clinicas (UBA) — Av. Cordoba 2351 — Polivalente, docente

Como sacar turno:
  Sistema de turnos online CABA: https://turnos.buenosaires.gob.ar
  Tambien por el 147 (atencion ciudadana CABA)

Urgencias (gratuitas, sin turno):
  SAME (CABA): 107

🔗 Red de hospitales CABA: https://www.buenosaires.gob.ar/salud/hospitales
Fuente: Ministerio de Salud CABA — may 2026
```

## Fuentes

- **Superintendencia de Servicios de Salud (SSS):** [argentina.gob.ar/salud/superintendencia-de-servicios-de-salud](https://www.argentina.gob.ar/salud/superintendencia-de-servicios-de-salud)
- **PAMI:** [pami.org.ar](https://www.pami.org.ar)
- **Precios de medicamentos:** [argentina.gob.ar/buscador-de-precios-de-medicamentos](https://www.argentina.gob.ar/buscador-de-precios-de-medicamentos)
- **Kairos:** [arg.kairosweb.com](https://arg.kairosweb.com)
- **Alfabeta:** [alfabeta.net](https://www.alfabeta.net/precio/)

Los datos son de fuentes publicas y oficiales. Este plugin no almacena ni transmite informacion del usuario. Precios y coberturas se consultan en tiempo real.
