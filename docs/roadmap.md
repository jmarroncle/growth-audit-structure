# Plan de construcción

## MVP — Motor de insights (la única fase)

Todo el alcance del MVP es esto: la capa de datos (los 3 niveles de confiabilidad — ver [`reference/capa-de-datos.md`](reference/capa-de-datos.md)), el agente generador de candidatos en las 6 familias, y el agente selector junto con el nodo de código que colapsa hallazgos y fuerza diversidad (ver [`reference/agentes.md`](reference/agentes.md)). Corre en n8n con un trigger manual — Cristopher carga la URL y el objetivo a mano.

Se valida corriéndolo contra 8-10 sitios reales hasta calibrar que el "molde" del insight (ver [`reference/insight-object.md`](reference/insight-object.md) y [`explanation/filosofia-del-insight.md`](explanation/filosofia-del-insight.md)) sale afilado en la práctica, no solo en la teoría.

**Criterio de validación:** ¿el insight que arma el motor está a la altura del ejemplo bueno del schema, o cae en genérico?

**Entregable:** una auditoría completa (4-5 insights con evidencia) por cada sitio que Cristopher cargue. Nada de mensajes de cold reach, nada de follow-ups automáticos, nada de web — eso es su propio proceso comercial, no software (ver la [nota de archivo](../archive/v1-con-instancias/NOTA-DE-ARCHIVO.md)).

## Fuera de alcance (por ahora)

- **Self-serve web para inbound** — un formulario público donde alguien pide su propia auditoría. La primera versión de este repo lo diseñó completo, incluyendo [un mockup de UI](../archive/v1-con-instancias/README.md). Quedó archivado, no descartado: si después de validar el motor Cristopher quiere retomarlo, es la referencia de partida.
- **Cualquier automatización de cold reach o follow-up** — no es un feature pendiente, es explícitamente trabajo manual de Cristopher con el resultado de la auditoría.
