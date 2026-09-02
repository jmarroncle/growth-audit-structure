# Referencia: los agentes del pipeline

Los 2 nodos de IA del diagrama en [`explanation/arquitectura.md`](../explanation/arquitectura.md) — son 2 llamados distintos al mismo modelo (Claude Sonnet 4.6), cada uno con su propio prompt y su propio trabajo dentro del workflow de n8n.

| Agente (nodo) | Qué decide | Inputs | Output |
|---|---|---|---|
| **`GEN`** — Generador de candidatos | Qué insights candidatos generar, distribuidos en las 6 familias ([`tipos-de-insight.md`](tipos-de-insight.md)) | Los datos de las 6 herramientas de la capa de datos ([`capa-de-datos.md`](capa-de-datos.md)) + el objetivo (declarado por el visitante en el formulario) | Una lista de candidatos — más de los que se van a mostrar al final |
| **`SEL`** — Selector | Cuáles candidatos pasan el corte y en qué orden, aplicando el checklist de [`how-to/evaluar-la-calidad-de-un-insight.md`](../how-to/evaluar-la-calidad-de-un-insight.md): fuerza de evidencia, relevancia al objetivo, distancia de lo genérico, accionabilidad, y riesgo de insulto | Los candidatos que entregó `GEN` | Los candidatos rankeados, antes de pasar por el nodo de código que colapsa y fuerza diversidad |

## Por qué son 2 llamados y no uno solo

Cada uno tiene un trabajo distinto y se beneficia de un prompt enfocado en una sola tarea: `GEN` razona sobre evidencia técnica del sitio, `SEL` razona sobre criterios de calidad y riesgo. Mezclar los dos en un único llamado obligaría a un prompt intentando hacer las dos cosas a la vez — más difícil de calibrar y de debuggear cuando algo sale mal en una fase puntual.

## Lo que no es un agente

El nodo `COL` (colapsa hallazgos + fuerza diversidad de familias) y la detección de stack tecnológico (`ST`) son **código determinístico, sin IA** — reglas mecánicas que no necesitan razonamiento. Ver la leyenda de colores en [`explanation/arquitectura.md`](../explanation/arquitectura.md) para la distinción visual completa.
