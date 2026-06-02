# PROCEDURES — Procedimientos de investigación

> Leer cuando hay que definir próximos pasos para el operador/investigador.
> Este módulo cubre los pasos de INVESTIGACIÓN — no los de atención a la víctima.
> Las recomendaciones inmediatas para la víctima ya fueron generadas por el Forensic Intake.

---

## Foco del módulo

El Forensic Intake ya generó en su .txt las recomendaciones de recuperación de acceso, seguridad inmediata y pasos legales para la víctima. No duplicar eso aquí.

Este módulo define qué hace el **operador/analista** a partir del material recolectado.

---

## Por tipo de incidente

### CIVIL — Cuenta comprometida

**Preservación (antes de cualquier acción):**
- Capturar el .txt del Forensic Intake y guardarlo con hash (SHA-256) como evidencia base
- Si la víctima tiene acceso a la cuenta: exportar historial de inicio de sesión antes de hacer cambios
- Si hay mensajes del atacante: screenshot con metadatos visibles (fecha, hora, plataforma)

**Investigación del vector:**
- Si `link_sospechoso ≠ No creo`: solicitar la URL y analizarla en sandbox (urlscan.io, VirusTotal)
- Si `aplicaciones ≠ No`: verificar qué permisos tenía la app comprometida
- Si `misma_pass = Sí`: estimar qué otras cuentas están en riesgo (buscar el email en HaveIBeenPwned)
- Si `contrasena_comp` incluye personas conocidas: considerar insider como hipótesis principal

**Correlación:**
- ¿El `cuando` del incidente coincide con algún breach público reciente de la plataforma?
- ¿El comportamiento del atacante (`que_hicieron`) sugiere oportunismo o target específico?

---

### CORPORATIVO — Incidente en infraestructura

**Preservación (crítica — hacer antes de cualquier remediación):**
- Si `evidencia_intacta` incluye sistemas no modificados: imagen forense inmediata
- Si `memoria_volatil = No`: evaluar captura de RAM en sistemas críticos aún vivos
- Si `logs_disponibles` tiene huecos: identificar si la ausencia fue intencional (log tampering)
- Hash + timestamp de todos los artefactos antes de moverlos

**Investigación del vector:**
- Si `vector_probable = Phishing`: buscar el email original en quarantine, analizar headers
- Si `vector_probable = Credenciales comprometidas`: revisar logs de autenticación ±48h del evento ancla
- Si `vector_probable = Vulnerabilidad pública`: correlacionar con CVEs del stack (`exposicion_internet`)
- Si `vector_probable = Supply chain`: mapear accesos de terceros en el período previo

**Correlación de IOCs:**
- Si hay `iocs`: buscar en feeds de threat intel (MISP, VirusTotal, Shodan)
- Si hay `persistence`: mapear técnicas a MITRE ATT&CK para entender el playbook del actor
- Correlacionar timestamps de los logs disponibles con el evento ancla del intake

**Regulatorio (si aplica):**
- Si `regulatorio` incluye GDPR / Ley 25326 / BCRA: calcular ventana de notificación obligatoria desde el momento de detección
- Si `seguro_cyber = Sí, pendiente de notificar`: notificar a la aseguradora antes de iniciar remediación (requisito contractual frecuente)

---

## Checklist universal post-intake

- [ ] ¿La escena está preservada o fue modificada desde el incidente?
- [ ] ¿Hay riesgo activo en este momento? (`activo` / `estado_incidente`)
- [ ] ¿Se documentaron todos los accesos al sistema/cuenta desde el incidente?
- [ ] ¿Los `[GAP]` críticos tienen plan de cierre?
- [ ] ¿Hay obligaciones regulatorias con ventana de tiempo activa?

---

## Output esperado

Lista priorizada de acciones con urgencia:
- `INMEDIATA` — no puede esperar (preservación, contención activa)
- `24H` — alta prioridad (correlación de IOCs, notificaciones legales)
- `72H` — importante pero no bloqueante (análisis profundo, reportes)
