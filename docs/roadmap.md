# Plan de construcción

El proyecto se valida de adentro hacia afuera: primero el motor de insights (lo más difícil de acertar), después cada instancia de uso sobre ese motor ya probado.

## Fase 1 — Motor de insights

El core del sistema: la capa de datos (los 3 niveles de confiabilidad — ver [`reference/capa-de-datos.md`](reference/capa-de-datos.md)), el agente generador de candidatos en las 6 familias, y el agente selector junto con el nodo de código que colapsa hallazgos y fuerza diversidad (ver [`reference/agentes.md`](reference/agentes.md)). Se corre manualmente contra 8-10 sitios reales hasta calibrar que el "molde" del insight (ver [`reference/insight-object.md`](reference/insight-object.md) y [`explanation/filosofia-del-insight.md`](explanation/filosofia-del-insight.md)) sale afilado en la práctica, no solo en la teoría.

**Criterio de validación de esta fase:** ¿el insight que arma el motor está a la altura del ejemplo bueno del schema, o cae en genérico?

Sin frontend todavía — se corre a mano contra una URL + objetivo.

## Fase 2 — Instancia Cold Reach

El agente `OBJ` que infiere el objetivo desde contexto (ej: empresa que levantó ronda y contrata un growth lead → objetivo de escalar pipeline — ver [`reference/agentes.md`](reference/agentes.md)) + renderer de 1 solo hook.

## Fase 3 — Instancia Follow-up post-call

Captura del objetivo "locked" de la conversación + renderer más profundo, referenciado a lo hablado (mini pre-SOW).

## Fase 4 — Instancia Inbound + Web self-serve

Dos piezas que se construyen en paralelo (ver [`explanation/arquitectura.md`](explanation/arquitectura.md#dónde-vive-la-interfaz-el-frontend) para el detalle de cómo se conectan):

- **Frontend estático** (landing, formulario, pantalla de resultados e insight expandido — ver el mockup navegable en la sección "🖼️ UI del producto" del [README](../README.md)), hosteado en Vercel Hobby. Sin lógica propia: postea al webhook de n8n al enviar el formulario, y consulta otro webhook por token para traer el resultado.
- **Workflow de n8n** que recibe el POST del formulario, corre el motor, envía el mail con el link a resultados, registra en Sheets/CRM, y expone el webhook GET que el frontend consulta para renderizar las tarjetas.

Esta es la fase más cara de construir y la que menos tolera un insight flojo — por eso va después de validar el motor, no antes.

## Fase 5 — QA, documentación y entrega

Testing end-to-end de las 3 instancias, documentación de uso, handoff.
