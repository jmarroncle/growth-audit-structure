# Growth Audit Structure

> Motor que genera una auditoría de growth completa a partir de una URL — evidencia observable, no un checklist genérico.

Repo del proyecto para **Cristopher Echevarría**. Esta es la versión **MVP** (Minimum Viable Product — la versión más chica que ya sirve): el producto hace **una sola cosa**, generar una auditoría completa. Nada más.

## Qué es esto

No es un checklist de sitio, como lo ejecutan la mayoría de las agencias. Es una tesis de growth: identifica hasta 5 growth opportunities y gaps frente a los competidores, respaldadas por evidencia observable, usando el sitio web propio y el de la competencia como lever. No ofrece una solución directa — es un punto de partida, no el final de una venta.

## Qué NO hace este MVP (a propósito)

La primera versión de este repo intentaba construir tres "salidas" de software distintas — un mensaje de cold reach, un follow-up post-call, y la entrega inbound. Se corrigió el alcance parcialmente: **cold reach y follow-up no son trabajo del sistema** — son Cristopher usando a mano el resultado de una auditoría ya generada, con la misma auditoría como materia prima. La entrega web self-serve sí sigue siendo parte del producto, porque ahí sí hace falta automatizar algo real: nadie de Cristopher tiene que estar mirando cuando un visitante pide su auditoría.

Esa primera versión completa (con el switch de 3 instancias) quedó guardada en [`archive/v1-con-instancias/`](archive/v1-con-instancias/) como referencia — ver [la nota de archivo](archive/v1-con-instancias/NOTA-DE-ARCHIVO.md) para el detalle del cambio de alcance.

## Cómo está armado

Ver [`docs/explanation/arquitectura.md`](docs/explanation/arquitectura.md) para el diagrama completo. En resumen:

```
Formulario web → Capa de datos (6 herramientas, 3 niveles de confiabilidad) → Agente generador (6 familias) → Agente selector → Nodo de código (colapsa + diversidad) → La auditoría completa, entregada por mail
```

## 🖼️ UI del producto (mockup)

**[Ver el mockup navegable →](https://claude.ai/code/artifact/c7bcb0a8-c527-4244-9dc2-d4e8ac019394)**

Las 5 pantallas de la entrega web self-serve — landing, formulario, procesando, resultados e insight expandido — con datos de ejemplo (la misma auditoría de `nortia.io` del tutorial).

> Es un link privado (Claude Artifact) — compartilo desde el menú de share de esa página si Cristopher necesita verlo sin tu cuenta.

## 💰 Costo estimado de operación

**≈ USD 61–118 por mes**, a cargo de Cristopher (cuentas y suscripciones propias — ver [`docs/reference/stack.md`](docs/reference/stack.md) para el detalle por herramienta). Es un costo variable que crece con el volumen de auditorías, no una suscripción fija.

## Documentación

Organizada con **Diátaxis** — separa los documentos en 4 tipos según lo que el lector necesita en ese momento.

- 📚 **Tutoriales**
  - [`docs/tutorials/primer-audit-manual.md`](docs/tutorials/primer-audit-manual.md) — arma un insight completo a mano, paso a paso, con un ejemplo ficticio
- 🛠️ **Guías prácticas**
  - [`docs/how-to/evaluar-la-calidad-de-un-insight.md`](docs/how-to/evaluar-la-calidad-de-un-insight.md)
- 📖 **Referencia**
  - [`docs/reference/brief-original.md`](docs/reference/brief-original.md) — el requerimiento original de Cristopher, transcripto tal cual, con una nota de alcance
  - [`docs/reference/insight-object.md`](docs/reference/insight-object.md) — los campos del objeto insight
  - [`docs/reference/tipos-de-insight.md`](docs/reference/tipos-de-insight.md) — las 6 familias
  - [`docs/reference/niveles-de-evidencia.md`](docs/reference/niveles-de-evidencia.md) — medido / recuperado / inferido
  - [`docs/reference/capa-de-datos.md`](docs/reference/capa-de-datos.md) — qué devuelve cada herramienta y a qué insight llega
  - [`docs/reference/agentes.md`](docs/reference/agentes.md) — qué decide cada agente de IA del pipeline
  - [`docs/reference/stack.md`](docs/reference/stack.md) — herramientas evaluadas por función (cuentas y suscripciones a cargo del cliente)
- 💡 **Explicación**
  - [`docs/explanation/arquitectura.md`](docs/explanation/arquitectura.md)
  - [`docs/explanation/filosofia-del-insight.md`](docs/explanation/filosofia-del-insight.md) — por qué esto no es un checklist

Más el plan de construcción — no es documentación de producto, es planificación:

- [`docs/roadmap.md`](docs/roadmap.md)

## Estado del proyecto

📋 **Etapa de planificación.** Próximo hito: correr el motor manualmente contra 8-10 sitios reales para validar que la calidad del insight se sostiene en la práctica.
