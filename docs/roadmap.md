# Plan de construcción

## MVP — Motor + entrega web self-serve

El alcance del MVP tiene dos piezas que se construyen en paralelo (ver [`explanation/arquitectura.md`](explanation/arquitectura.md) para el detalle de cómo se conectan):

- **El motor de insights** — la capa de datos (los 3 niveles de confiabilidad, ver [`reference/capa-de-datos.md`](reference/capa-de-datos.md)), el agente generador de candidatos en las 6 familias, y el agente selector junto con el nodo de código que colapsa hallazgos y fuerza diversidad (ver [`reference/agentes.md`](reference/agentes.md)).
- **El frontend estático** (landing, formulario, pantalla de resultados e insight expandido — ver el mockup navegable en la sección "🖼️ UI del producto" del [README](../README.md)), hosteado en Vercel Hobby. Sin lógica propia: postea al webhook de n8n al enviar el formulario, y consulta otro webhook por token para traer el resultado.

El motor se valida primero, corriéndolo contra 8-10 sitios reales hasta calibrar que el "molde" del insight (ver [`reference/insight-object.md`](reference/insight-object.md) y [`explanation/filosofia-del-insight.md`](explanation/filosofia-del-insight.md)) sale afilado en la práctica, no solo en la teoría — recién con eso confirmado tiene sentido conectar el frontend, porque es la parte más cara de construir y la que menos tolera un insight flojo.

**Criterio de validación del motor:** ¿el insight que arma el motor está a la altura del ejemplo bueno del schema, o cae en genérico?

**Entregable:** un visitante entra a la web, pide su auditoría, y el sistema se la manda por mail solo — sin que Cristopher intervenga en la generación. Nada de mensajes de cold reach ni de follow-ups automáticos: eso es el proceso comercial de Cristopher con el resultado, no software (ver la [nota de archivo](../archive/v1-con-instancias/NOTA-DE-ARCHIVO.md)).

## Fuera de alcance

**Cualquier automatización de cold reach o follow-up post-call** — no es un feature pendiente ni una fase futura. Es explícitamente trabajo manual de Cristopher con el resultado de una auditoría ya generada.
