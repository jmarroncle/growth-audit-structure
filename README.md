# Growth Audit Structure

> Motor de growth insights sobre el sitio web de una empresa — evidencia observable, no un checklist genérico.

Repo de arranque del proyecto para **Cristopher Echevarría**. Documenta la interpretación del brief, la arquitectura propuesta, el stack técnico evaluado y el plan de construcción, antes de empezar a programar.

## Qué es esto

No es un checklist de sitio, como lo ejecutan la mayoría de las agencias. Es una tesis de growth: identifica hasta 5 growth opportunities y gaps frente a los competidores, respaldadas por evidencia observable, usando el sitio web propio y el de la competencia como lever. No ofrece una solución directa — abre una primera conversación, una oportunidad para salir del típico cold reach genérico.

## Las 3 formas en que se usa

1. **Cold Reach** — un solo hook: el insight más verificable e interesante, y menos insultante, para abrir una conversación fría. El objetivo se infiere del contexto.
2. **Follow-up post-call** — versión más profunda, referenciada a lo hablado en la llamada. Funciona como un mini pre-SOW (statement of work).
3. **Inbound self-serve** — el audit completo (4-5 insights), gateado detrás de un mail. El onboarding captura el objetivo; tiene que generar deseo de agendar la call.

## 💰 Costo estimado de operación

**≈ USD 61–118 por mes**, a cargo de Cristopher (cuentas y suscripciones propias — ver [`docs/reference/stack.md`](docs/reference/stack.md) para el detalle por herramienta).

Es un costo variable, no una suscripción fija: crece o baja según cuántos audits se corran por mes. La estimación asume un volumen inicial bajo-moderado. Este número es aparte del fee de implementación del proyecto — es lo que cuesta *operar* la solución una vez construida, mes a mes.

## Cómo está armado

Ver [`docs/explanation/arquitectura.md`](docs/explanation/arquitectura.md) para el diagrama completo. En resumen:

```
URL + objetivo → Capa de datos (3 niveles de confiabilidad) → Generación de candidatos (6 familias) → Selección/Ranking → Render según instancia
```

## 🖼️ UI del producto (mockup)

**[Ver el mockup navegable →](https://claude.ai/code/artifact/c7bcb0a8-c527-4244-9dc2-d4e8ac019394)**

Las 5 pantallas de la Instancia Inbound — landing, formulario, procesando, resultados e insight expandido — con datos de ejemplo (la misma auditoría de `nortia.io` del tutorial). Todavía no hay UI construida en este proyecto; esto es el mockup de referencia para diseñarla.

> Es un link privado (Claude Artifact) — compartilo desde el menú de share de esa página si Cristopher necesita verlo sin tu cuenta.

## Documentación

La documentación de producto está organizada con **Diátaxis** — un framework que separa los documentos en 4 tipos según lo que el lector necesita en ese momento: aprender haciendo, resolver una tarea puntual, consultar un dato exacto, o entender el porqué de una decisión.

- 📚 **Tutoriales** (aprender haciendo)
  - [`docs/tutorials/primer-audit-manual.md`](docs/tutorials/primer-audit-manual.md) — arma un insight completo a mano, paso a paso, con un ejemplo ficticio
- 🛠️ **Guías prácticas** (cómo resolver una tarea concreta)
  - [`docs/how-to/evaluar-la-calidad-de-un-insight.md`](docs/how-to/evaluar-la-calidad-de-un-insight.md)
  - [`docs/how-to/inferir-el-objetivo-en-cold-reach.md`](docs/how-to/inferir-el-objetivo-en-cold-reach.md)
  - [`docs/how-to/elegir-que-mostrar-segun-la-instancia.md`](docs/how-to/elegir-que-mostrar-segun-la-instancia.md)
- 📖 **Referencia** (consulta rápida de datos exactos)
  - [`docs/reference/brief-original.md`](docs/reference/brief-original.md) — el requerimiento original de Cristopher, transcripto tal cual
  - [`docs/reference/insight-object.md`](docs/reference/insight-object.md) — los campos del objeto insight
  - [`docs/reference/tipos-de-insight.md`](docs/reference/tipos-de-insight.md) — las 6 familias
  - [`docs/reference/niveles-de-evidencia.md`](docs/reference/niveles-de-evidencia.md) — medido / recuperado / inferido
  - [`docs/reference/capa-de-datos.md`](docs/reference/capa-de-datos.md) — qué devuelve cada herramienta y a qué insight llega
  - [`docs/reference/agentes.md`](docs/reference/agentes.md) — qué decide cada agente de IA del pipeline
  - [`docs/reference/instancias.md`](docs/reference/instancias.md) — tabla comparativa de las 3 instancias
  - [`docs/reference/stack.md`](docs/reference/stack.md) — herramientas evaluadas por función (cuentas y suscripciones a cargo del cliente)
- 💡 **Explicación** (el porqué de las decisiones de diseño)
  - [`docs/explanation/arquitectura.md`](docs/explanation/arquitectura.md)
  - [`docs/explanation/filosofia-del-insight.md`](docs/explanation/filosofia-del-insight.md) — por qué esto no es un checklist

Más el plan de construcción del proyecto — no es documentación de producto, es planificación:

- [`docs/roadmap.md`](docs/roadmap.md) — fases de construcción y criterios de validación

## Estado del proyecto

📋 **Etapa de planificación.** Este repo documenta el diseño del sistema antes de empezar a programar. El primer hito es validar el motor de insights (Fase 1) corriéndolo manualmente contra sitios reales, antes de invertir en la versión web self-serve.
