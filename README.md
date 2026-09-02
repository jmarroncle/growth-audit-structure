# Growth Audit Structure

> Motor que genera una auditoría de growth completa a partir de una URL — evidencia observable, no un checklist genérico.

Repo del proyecto para **Cristopher Echevarría**. Esta es la versión **MVP** (Minimum Viable Product — la versión más chica que ya sirve): el producto hace **una sola cosa**, generar una auditoría completa. Nada más.

## Qué es esto

No es un checklist de sitio, como lo ejecutan la mayoría de las agencias. Es una tesis de growth: identifica hasta 5 growth opportunities y gaps frente a los competidores, respaldadas por evidencia observable, usando el sitio web propio y el de la competencia como lever. No ofrece una solución directa — es un punto de partida, no el final de una venta.

## Qué NO hace este MVP (a propósito)

La primera versión de este repo intentaba construir tres "salidas" de software distintas — un mensaje de cold reach, un follow-up post-call, y un formulario self-serve en la web. Se corrigió el alcance: **eso no es trabajo del sistema.**

El producto genera una auditoría. Lo que Cristopher hace después con ella — mandarla en frío, profundizarla en una llamada, entregarla a un lead — es su propio proceso comercial, con la misma auditoría como materia prima. No hay que construir software para eso.

Esa primera versión (con el pipeline de 3 instancias, el frontend web y su mockup de UI) quedó guardada en [`archive/v1-con-instancias/`](archive/v1-con-instancias/) como referencia — ver [la nota de archivo](archive/v1-con-instancias/NOTA-DE-ARCHIVO.md) para el porqué del cambio.

## Cómo está armado

Ver [`docs/explanation/arquitectura.md`](docs/explanation/arquitectura.md) para el diagrama completo. En resumen:

```
URL + objetivo (a mano) → Capa de datos (6 herramientas, 3 niveles de confiabilidad) → Agente generador (6 familias) → Agente selector → Nodo de código (colapsa + diversidad) → La auditoría completa
```

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
