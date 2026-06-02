# Forensic Intake - Incident Toolkit

Toolkit de respuesta a incidentes digitales para las primeras horas. Dos herramientas que funcionan solas o en conjunto:

- **Forensic Intake** — formulario de triage para entrevistar a la víctima
- **Detective Skill** — skill para Claude Code que analiza el output del intake y genera un reporte

---

## El problema que resuelve

Todos los que trabajamos en seguridad tenemos ese contacto. El amigo que te llama un domingo porque "le hackearon el WhatsApp". El familiar con movimientos raros en el homebanking. El conocido de un conocido que alguien les dijo que vos "sabés de estas cosas".

Siempre hay algo que puede hacerse. Pero lo primero es tener la información correcta — y sin un proceso estructurado, la entrevista inicial se convierte en un caos.

Este toolkit ordena ese caos.

---

## Forensic Intake

Un formulario HTML que podés enviarle a la víctima para que complete sola, o llenar junto a ella durante la entrevista. Sin instalación, sin dependencias. Abrís el archivo en el browser y arrancás.

### Dos modos

**Usuario civil** — para los casos de todos los días:
- Cuenta de Instagram, Gmail o WhatsApp comprometida
- Homebanking con movimientos no reconocidos
- Extorsión o sextorsión

**Incidente corporativo** — para cuando el llamado viene de una empresa:
- Ransomware o cifrado de archivos
- Intrusión activa
- Exfiltración de datos
- Compromiso de credenciales

### Cómo funciona

Cada modo guía por las preguntas críticas en el orden correcto, con campos marcados por prioridad (CRÍTICO / IMPORTANTE / OPCIONAL). Al finalizar, genera un resumen exportable en `.txt` listo para analizar o procesar en otras herramientas.

El track civil incluye lógica de recomendaciones integrada: detecta si el incidente sigue activo, identifica el vector probable, y genera pasos específicos según la plataforma y el tipo de víctima.

### Uso

```
1. Abrir forensic-intake.html en cualquier browser
2. Seleccionar el tipo de caso (civil o corporativo)
3. Completar las fases junto a la víctima o enviarle el archivo
4. Exportar el .txt al finalizar
```

---

## Detective Skill

Skill para Claude Code que toma el `.txt` exportado por el Forensic Intake y guía el análisis completo del caso.

### Pipeline completo

```
Víctima
   ↓
Forensic Intake (HTML)     ← entrevista estructurada
   ↓ export .txt
Detective Skill (Claude)   ← análisis, deducciones, reporte
   ↓
Reporte HTML final
```

### Módulos

| Módulo | Función |
|---|---|
| `01-intake` | Parsea el .txt del Forensic Intake o texto libre |
| `02-timeline` | Construye línea de tiempo con puntos de interés |
| `03-procedures` | Define pasos de investigación para el operador |
| `04-deductions` | Formula hipótesis estructuradas con nivel de confianza |
| `05-report` | Genera reporte HTML autocontenido del caso |

Ver [`detective-skill/INSTALL.md`](detective-skill/INSTALL.md) para instrucciones de instalación en Claude Code.

---

## Estructura del repositorio

```
forensic-intake.html          ← herramienta principal, abrir en browser
intake-victima.html           ← versión simplificada para enviar a la víctima
detective-skill/
├── index.md                  ← índice del skill
├── INSTALL.md                ← instrucciones de instalación
└── references/
    ├── 01-intake.md
    ├── 02-timeline.md
    ├── 03-procedures.md
    ├── 04-deductions.md
    └── 05-report.md
```

---

## Licencia

Uso libre. Si lo usás o lo adaptás, se agradece la mención.
