# DETECTIVE — Índice

## Pipeline con Forensic Intake

El flujo estándar combina dos herramientas:

```
Víctima / cliente
      ↓
Forensic Intake (HTML)          ← recolección estructurada con la víctima
      ↓ export .txt
DETECTIVE skill (Claude)        ← análisis, deducciones, reporte
      ↓
Reporte HTML final
```

El .txt del Forensic Intake es el input principal de este skill.
Si no hay .txt disponible, el intake acepta volcado libre de texto (Modo B).

---

## Módulos de referencia

| Archivo | Cuándo leer |
|---|---|
| `01-intake.md` | Al recibir el .txt del Forensic Intake o un volcado de datos nuevo |
| `02-timeline.md` | Para construir o actualizar la línea de tiempo del caso |
| `03-procedures.md` | Para definir próximos pasos del operador/investigador |
| `04-deductions.md` | Para formular hipótesis y perfil del actor |
| `05-report.md` | Para generar el reporte HTML final del caso |

---

## Instrucción de carga

Leer SOLO el módulo necesario para la tarea actual.
No cargar todos los archivos de una vez.
