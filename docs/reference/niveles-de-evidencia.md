# Referencia: niveles de evidencia

Cada dato que respalda un insight lleva una de tres etiquetas de origen, y eso define cómo se afirma:

| Origen | Cómo se afirma | Ejemplos | Costo de obtenerlo |
|---|---|---|---|
| **Medido** | Directo, como hecho | Lighthouse (performance), stack tecnológico detectado, ranking real, presencia en respuesta de un LLM corriendo la query en vivo (test de AEO) | Barato y confiable |
| **Recuperado** | Con fuente y fecha chequeada | Ronda de inversión, post de un founder, headcount | Recuperable, pero sensible a la fecha — requiere búsqueda web con fuente, nunca memoria del modelo |
| **Inferido** | Como hipótesis, nunca como hecho ("Las señales sugieren que…") | Runway, "el producto funciona", "el equipo no puede shippear" | Difícil o riesgoso — confianza baja |

## Por qué importa esta clasificación

El campo `confianza` del objeto insight (ver [`insight-object.md`](insight-object.md)) se deriva directamente de qué tan alto en esta escala está el dato más débil que sostiene el claim. Un insight que mezcla evidencia medida con una inferencia no puede afirmarse con la misma seguridad que uno que solo usa datos medidos.
