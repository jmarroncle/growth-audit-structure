# Growth Audit Structure

> Motor de growth insights sobre el sitio web de una empresa — evidencia observable, no un checklist genérico.

Repo de arranque del proyecto para **Cristopher Echevarría**. Documenta la interpretación del brief, la arquitectura propuesta, el stack técnico evaluado y el plan de construcción, antes de empezar a programar.

## Qué es esto

No es un checklist de sitio, como lo ejecutan la mayoría de las agencias. Es una tesis de growth: identifica hasta 5 growth opportunities y gaps frente a los competidores, respaldadas por evidencia observable, usando el sitio web propio y el de la competencia como lever. No ofrece una solución directa — abre una primera conversación, una oportunidad para salir del típico cold reach genérico.

## Las 3 formas en que se usa

1. **Cold Reach** — un solo hook: el insight más verificable e interesante, y menos insultante, para abrir una conversación fría. El objetivo se infiere del contexto.
2. **Follow-up post-call** — versión más profunda, referenciada a lo hablado en la llamada. Funciona como un mini pre-SOW (statement of work).
3. **Inbound self-serve** — el audit completo (4-5 insights), gateado detrás de un mail. El onboarding captura el objetivo; tiene que generar deseo de agendar la call.

## Cómo está armado

Ver [`docs/architecture.md`](docs/architecture.md) para el diagrama completo. En resumen:

```
URL + objetivo → Capa de datos (3 niveles de confiabilidad) → Generación de candidatos (6 familias) → Selección/Ranking → Render según instancia
```

## Documentación

- [`docs/architecture.md`](docs/architecture.md) — arquitectura del motor y diagrama de flujo
- [`docs/insight-schema.md`](docs/insight-schema.md) — el objeto "insight": campos, niveles de evidencia, ejemplo genérico vs. bueno
- [`docs/stack.md`](docs/stack.md) — herramientas evaluadas por función (cuentas y suscripciones a cargo del cliente)
- [`docs/roadmap.md`](docs/roadmap.md) — fases de construcción y criterios de validación

## Estado del proyecto

📋 **Etapa de planificación.** Este repo documenta el diseño del sistema antes de empezar a programar. El primer hito es validar el motor de insights (Fase 1) corriéndolo manualmente contra sitios reales, antes de invertir en la versión web self-serve.
