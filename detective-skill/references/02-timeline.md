# TIMELINE — Línea de tiempo y puntos de interés

> Solo leer cuando haya que construir o actualizar la línea de tiempo del caso.

## Formato de la línea de tiempo

```
[FECHA/HORA]  — [EVENTO]  — [FUENTE: víctima / log / testigo]
     ↓
[FECHA/HORA]  — [EVENTO]  — [FUENTE]
```

- Ordenar cronológicamente. Si la hora es incierta, usar rango: `[~14:00–15:30]`.
- Marcar eventos sin fecha confirmada al final con etiqueta `[SIN FECHA — estimado]`.

## Puntos de interés (POI)

Marcar con ★ los eventos que cumplan al menos uno:
- Cambio de comportamiento del sospechoso o sistema
- Primer contacto / primer evento anómalo
- Acceso a recurso sensible
- Inconsistencia entre relatos o logs
- Ventana temporal sin explicación (gap)

## Output esperado

1. Tabla o lista cronológica con fuente por evento
2. Lista de ★ POIs con una línea explicando por qué es de interés
3. Lista de `[GAP]` temporales que requieren investigación
