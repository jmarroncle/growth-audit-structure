# Plan de construcción

El proyecto se valida de adentro hacia afuera: primero el motor de insights (lo más difícil de acertar), después cada instancia de uso sobre ese motor ya probado.

## Fase 1 — Motor de insights

El core del sistema: capa de datos (los 3 niveles de confiabilidad), generación de candidatos en las 6 familias, función de selección/ranking. Se corre manualmente contra 8-10 sitios reales hasta calibrar que el "molde" del insight (ver [`reference/insight-object.md`](reference/insight-object.md) y [`explanation/filosofia-del-insight.md`](explanation/filosofia-del-insight.md)) sale afilado en la práctica, no solo en la teoría.

**Criterio de validación de esta fase:** ¿el insight que arma el motor está a la altura del ejemplo bueno del schema, o cae en genérico?

Sin frontend todavía — se corre a mano contra una URL + objetivo.

## Fase 2 — Instancia Cold Reach

Lógica de inferencia de objetivo desde contexto (ej: empresa que levantó ronda y contrata un growth lead → objetivo de escalar pipeline) + renderer de 1 solo hook.

## Fase 3 — Instancia Follow-up post-call

Captura del objetivo "locked" de la conversación + renderer más profundo, referenciado a lo hablado (mini pre-SOW).

## Fase 4 — Instancia Inbound + Web self-serve

Formulario de onboarding que captura el objetivo, gateado con mail · landing donde el prospecto ingresa su URL · workflow de n8n que conecta el webhook del formulario → motor → output → envío por mail y registro en Sheets/CRM (ver [`explanation/arquitectura.md`](explanation/arquitectura.md)) · diseño del output final.

Esta es la fase más cara de construir y la que menos tolera un insight flojo — por eso va después de validar el motor, no antes.

## Fase 5 — QA, documentación y entrega

Testing end-to-end de las 3 instancias, documentación de uso, handoff.
