# Instalación — Detective Skill para Claude Code

Este skill está diseñado para [Claude Code](https://claude.ai/code), el CLI oficial de Anthropic.

## Requisitos

- Claude Code instalado
- Proyecto o directorio de trabajo abierto en Claude Code

## Instalación

### Opción A — Skill de proyecto (recomendada)

1. Copiar la carpeta `detective-skill/` dentro de tu proyecto, en `.claude/commands/detective/`
2. Renombrar `index.md` a `detective.md` dentro de esa carpeta
3. El skill quedará disponible como `/detective` en tu sesión de Claude Code

```
tu-proyecto/
└── .claude/
    └── commands/
        └── detective/
            ├── detective.md        ← renombrado desde index.md
            └── references/
                ├── 01-intake.md
                ├── 02-timeline.md
                ├── 03-procedures.md
                ├── 04-deductions.md
                └── 05-report.md
```

### Opción B — Uso manual sin instalación

Sin instalar, podés usar el skill directamente:

1. Abrí Claude Code en la carpeta `detective-skill/`
2. Pegá el contenido de `index.md` como primer mensaje de contexto
3. Claude cargará los módulos que necesite según la tarea

## Uso

Una vez instalado, invocar con:

```
/detective
```

Luego pegá el .txt generado por el **Forensic Intake** o describí el caso libremente.
El skill detecta automáticamente el formato y elige el modo de análisis correspondiente.

## Flujo recomendado

```
1. Completar Forensic Intake con la víctima
2. Exportar el .txt desde el botón "Generar reporte"
3. Invocar /detective en Claude Code
4. Pegar el .txt
5. Claude guía el análisis: timeline → procedimientos → deducciones → reporte HTML
```

## Módulos

El skill carga los módulos de `references/` bajo demanda — solo los necesarios para cada fase.
No carga todo al inicio para conservar contexto.

| Módulo | Función |
|---|---|
| `01-intake.md` | Parsea el .txt del Forensic Intake o texto libre |
| `02-timeline.md` | Construye línea de tiempo con puntos de interés |
| `03-procedures.md` | Define pasos de investigación para el operador |
| `04-deductions.md` | Formula hipótesis estructuradas con nivel de confianza |
| `05-report.md` | Genera reporte HTML autocontenido del caso |
