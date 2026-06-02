# REPORT — Generación de reporte final HTML

> Solo leer cuando el usuario pida generar el reporte del caso.

## Estructura del HTML

Generar un archivo `.html` autocontenido (sin dependencias externas) con este esquema:

```
<encabezado del caso>
├── Sección 1: Línea de tiempo
├── Sección 2: Puntos de interés
├── Sección 3: Procedimientos recomendados
└── Sección 4: Deducciones
```

## Estilos

Usar CSS inline en `<style>` dentro del `<head>`. Paleta oscura profesional:

```css
--bg:       #0f1117
--surface:  #1a1d27
--border:   #2e3347
--accent:   #4f8ef7
--warn:     #f7c94f
--danger:   #f75f5f
--text:     #e2e8f0
--muted:    #6b7280
font-family: 'Segoe UI', system-ui, sans-serif
```

## Componentes visuales obligatorios

**Timeline:** tabla con columnas `Hora | Evento | Fuente` — filas alternas en `--surface`.

**POIs:** cards con borde izquierdo `--accent` (★ normal) o `--danger` (★ crítico), fondo `--surface`.

**Procedimientos:** lista con badge de urgencia coloreado:
- `INMEDIATA` → pill rojo (`--danger`)
- `24H` → pill amarillo (`--warn`)  
- `72H` → pill azul (`--accent`)

**Deducciones:** cards con indicador de confianza:
- `Alta` → barra verde `#22c55e`
- `Media` → barra amarilla `--warn`
- `Baja` → barra gris `--muted`

**Header del caso:** fondo degradado `--surface → --bg`, muestra nombre del caso, fecha de reporte y badge de tipo (DIGITAL / FÍSICO / MIXTO).

## Instrucciones de generación

1. Consolidar todo el análisis previo del caso (intake + timeline + procedures + deductions).
2. Generar el HTML completo en un solo bloque de código.
3. Guardar con Write en la ruta que indique el usuario, o por defecto: `reporte_<nombre-caso>_<fecha>.html`.
4. Confirmar la ruta donde quedó guardado.

## Output esperado

Archivo HTML listo para abrir en browser, sin dependencias externas, con todos los datos del caso volcados.
