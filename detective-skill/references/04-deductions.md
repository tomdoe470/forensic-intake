# DEDUCTIONS — Deducciones generales del caso

> Solo leer cuando haya que formular inferencias o hipótesis sobre el caso.

## Estructura de una deducción

Cada deducción sigue este formato:
```
[D-N] HIPÓTESIS: <qué se infiere>
      BASADO EN: <qué hechos concretos la sostienen>
      CONFIANZA: Alta / Media / Baja
      FALSIFICABLE SI: <qué evidencia la descartaría>
```

## Tipos de deducciones a formular

1. **Perfil del actor** — ¿Quién pudo hacer esto? (interno/externo, técnico/no técnico, oportunista/dirigido)
2. **Motivación probable** — ¿Por qué? (financiero, venganza, espionaje, accidente, oportunismo)
3. **Vector de entrada** — ¿Cómo accedió? (phishing, acceso físico, credenciales robadas, vulnerabilidad técnica)
4. **Alcance del daño** — ¿Qué información/activos fueron comprometidos o están en riesgo?
5. **Próximo movimiento probable** — Si el actor sigue activo, ¿qué haría después?

## Reglas de razonamiento

- No afirmar como hecho lo que es inferencia. Usar "probablemente", "sugiere que", "es consistente con".
- Priorizar hipótesis que expliquen MÁS hechos con MENOS suposiciones (navaja de Occam).
- Siempre incluir al menos una hipótesis alternativa si la principal tiene confianza Media o Baja.
- Marcar explícitamente los `[GAP]` que cambiarían las conclusiones si se resolvieran.

## Output esperado

Lista numerada de deducciones en el formato [D-N], ordenadas de mayor a menor confianza.
