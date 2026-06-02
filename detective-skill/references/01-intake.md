# INTAKE — Procesamiento del caso

> Leer cuando el usuario presenta datos de un caso por primera vez.

---

## Modo A — Input desde Forensic Intake (.txt)

Reconocer por el header: `REPORTE DE INCIDENTE — CASE-XXXXXXXX`

El .txt ya viene estructurado por fases. No hacer extracción genérica — mapear directamente los campos al modelo del detective.

### Señales de urgencia — procesar PRIMERO antes de cualquier análisis

| Campo | Valor crítico | Acción |
|---|---|---|
| `activo` | `Sí, sigue activo` | Incidente activo → contención antes que análisis |
| `estado_incidente` | `Sí, activo y en curso` | IR activo → escalar inmediatamente |
| `extorsion` | cualquier valor ≠ `No` | Amenaza activa → no negociar, preservar evidencia |
| `menor` | `Sí` | Víctima vulnerable → protocolo diferenciado |

Si se detecta alguna, comunicarla al operador antes de continuar con el análisis.

---

### Mapeo de campos — Track CIVIL

| Campo del intake | Etiqueta detective |
|---|---|
| `plataforma` | `[WHAT]` — sistema comprometido |
| `cuando` | `[WHEN]` — evento ancla |
| `activo` | `[WHEN]` + urgencia |
| `puede_entrar` | `[WHAT]` — estado actual del acceso |
| `email_tel_original` | `[WHAT]` — capacidad de recuperación |
| `2fa` | `[WHAT]` — postura de seguridad previa |
| `link_sospechoso` | `[WHAT]` — vector probable (phishing) |
| `aplicaciones` | `[WHAT]` — vector probable (app de terceros) |
| `contrasena_comp` | `[WHAT]` — vector probable (credencial compartida) |
| `misma_pass` | `[WHAT]` — riesgo de propagación |
| `que_hicieron` | `[WHAT]` — acciones del atacante |
| `extorsion` | `[WHAT]` — agravante activo |
| `evidencia` | `[WHAT]` — estado de preservación |
| `menor` | `[WHO]` — flag víctima vulnerable |
| `cuenta_laboral` | `[WHAT]` — impacto profesional/comercial |

### Mapeo de campos — Track CORPORATIVO

| Campo del intake | Etiqueta detective |
|---|---|
| `tipo_incidente` | `[WHAT]` — clasificación del incidente |
| `cuando_corp` | `[WHEN]` — evento ancla |
| `estado_incidente` | `[WHEN]` + urgencia |
| `como_detecto` | `[WHAT]` — método de detección |
| `sistemas_afectados` | `[WHERE]` — superficie comprometida |
| `cantidad_hosts` | `[WHAT]` — alcance estimado |
| `exposicion_internet` | `[WHERE]` — superficie expuesta pre-incidente |
| `aislamiento` | `[WHAT]` — estado de contención |
| `vector_probable` | `[WHAT]` — hipótesis de entrada |
| `creds_comprometidas` | `[WHAT]` — activos de identidad comprometidos |
| `iocs` | `[WHAT]` — indicadores de compromiso |
| `persistence` | `[WHAT]` — mecanismos de persistencia detectados |
| `datos_afectados` | `[WHAT]` — alcance de datos |
| `exfiltracion` | `[WHAT]` — confirmación de exfiltración |
| `impacto_operativo` | `[WHAT]` — estado operativo actual |
| `logs_disponibles` | `[WHAT]` — evidencia disponible |
| `evidencia_intacta` | `[WHAT]` — integridad de la escena |
| `backups` | `[WHAT]` — capacidad de recuperación |
| `memoria_volatil` | `[WHAT]` — evidencia volátil capturada |
| `regulatorio` | `[WHAT]` — obligaciones de reporte |
| `seguro_cyber` | `[WHAT]` — cobertura activa |
| `sla` | `[WHAT]` — tolerancia operativa |

### Gaps automáticos desde el .txt

Marcar como `[GAP]` todo campo con:
- Valor literal `(sin respuesta)`
- Fase marcada como `OMITIDA`
- Valor `No sé` / `No determinado aún` / `No determinado`

---

## Modo B — Input libre (volcado de texto)

Si el input NO tiene el header del Forensic Intake, aplicar extracción genérica.

Identificar y etiquetar cada fragmento:

| Etiqueta | Qué es |
|---|---|
| `[WHO]` | Personas involucradas (víctima, sospechoso, testigo) |
| `[WHEN]` | Fechas, horas, rangos temporales |
| `[WHERE]` | Ubicaciones físicas o digitales (IPs, URLs, lugares) |
| `[WHAT]` | Acciones, eventos, artefactos, evidencias |
| `[GAP]` | Información faltante o contradictoria |

Preguntar solo si hay ambigüedad bloqueante:
- ¿Digital, físico o mixto?
- ¿Hay fecha/hora ancla conocida?
- ¿Sospechoso identificado o sin autor conocido?

---

## Output del intake

- ID de caso (del header si viene del Forensic Intake, o generar uno)
- Lista de hechos etiquetados por categoría
- Señales de urgencia identificadas (si hay)
- Lista de `[GAP]` que requieren seguimiento
- Tipo de caso confirmado: `CIVIL` / `CORPORATIVO` / `MIXTO`

Proceder con `02-timeline.md`.
