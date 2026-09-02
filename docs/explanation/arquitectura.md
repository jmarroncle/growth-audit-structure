# Por qué la arquitectura está armada así

## El flujo completo

El pipeline se orquesta y vive dentro de **n8n** (la herramienta de automatización con la que Cristopher va a operar el proyecto). En este MVP arranca con un trigger manual — Cristopher carga la URL y el objetivo a mano — y termina en la auditoría completa. No hay web, no hay formulario, no hay envío de mail: eso quedó fuera de alcance (ver [`roadmap.md`](../roadmap.md)).

```mermaid
flowchart TD
    T[Trigger manual en n8n<br/>Cristopher carga URL + objetivo] --> IN[URL + objetivo]

    IN --> PS
    IN --> ST
    IN --> AEO
    IN --> TXT
    IN --> WEB
    IN --> SEO

    subgraph CapaDatos [Nodos HTTP Request - capa de datos]
        PS["📊 PageSpeed Insights<br/>Core Web Vitals"]
        ST["🔧 Nodo Code: detección de stack<br/>(HTML + firmas conocidas)"]
        AEO["🤖 Perplexity API (Sonar)<br/>test de AEO"]
        TXT["📝 Firecrawl<br/>texto/diseño propio y competidores"]
        WEB["🔍 SerpAPI / Exa<br/>búsqueda web con fuente y fecha"]
        SEO["📈 DataForSEO<br/>rankings reales"]
    end

    PS --> GEN
    ST --> GEN
    AEO --> GEN
    TXT --> GEN
    WEB --> GEN
    SEO --> GEN

    GEN["🧠 Agente generador de candidatos<br/>(Claude Sonnet 4.6) — 6 familias"] --> SEL

    SEL["🧠 Agente selector (Claude)<br/>evidencia, relevancia, distancia de lo<br/>genérico, accionabilidad, riesgo de insulto"] --> COL

    COL["⚙️ Nodo Code: colapsa hallazgos<br/>+ fuerza diversidad de familias"] --> OUT["🎯 La auditoría completa<br/>4-5 insights con evidencia"]

    classDef trigger fill:#eef0ec,stroke:#9aa39c,color:#1a1d1f;
    classDef tool fill:#e3e8ec,stroke:#3a6c8a,color:#1a1d1f,stroke-width:2px;
    classDef agente fill:#dcece9,stroke:#1f6b66,color:#1a1d1f,stroke-width:2px;
    classDef code fill:#eaece7,stroke:#5c6360,color:#1a1d1f;
    classDef outcome fill:#dcece9,stroke:#1f6b66,color:#1a1d1f,stroke-width:3px;

    class T,IN trigger
    class PS,AEO,TXT,WEB,SEO tool
    class ST,COL code
    class GEN,SEL agente
    class OUT outcome
```

| Color | Qué significa |
|---|---|
| 🟩 Verde azulado | **Agente de IA** (Claude) razonando — genera candidatos o rankea por criterio subjetivo. Detalle de cada uno en [`reference/agentes.md`](../reference/agentes.md) |
| 🟦 Azul | **Llamada a una herramienta externa** — HTTP Request a una API (PageSpeed, Perplexity, Firecrawl, SerpAPI/Exa, DataForSEO) |
| ⬜ Gris | **Nodo de código determinístico** — sin IA: parsear HTML, colapsar hallazgos, forzar diversidad |

## Qué hace el sistema con el resultado

El pipeline termina cuando entrega la auditoría — no manda mails, no le habla a un prospecto, no elige un canal. El resultado queda guardado en algún lugar que Cristopher pueda abrir (un Google Doc o una fila en Sheets, a definir en la implementación) para que él lo use en lo que necesite después. Eso ya es su proceso comercial, no parte de este sistema — ver la [nota de archivo](../../archive/v1-con-instancias/NOTA-DE-ARCHIVO.md) para el porqué de este límite.

## Por qué 3 niveles de datos y no uno solo

El brief original de Cristopher marca un problema concreto de este tipo de herramientas: un LLM no sabe rankings SEO reales, no sabe si una empresa levantó una ronda la semana pasada, y si se le pregunta igual, inventa una respuesta con la misma confianza que si supiera el dato de verdad. Separar los datos en "barato y confiable", "recuperable pero sensible a la fecha" y "difícil o riesgoso" (ver [`reference/niveles-de-evidencia.md`](../reference/niveles-de-evidencia.md)) obliga al sistema a ser honesto sobre qué tan seguro está de cada afirmación, en vez de sonar igual de seguro sobre todo. Ver [`reference/capa-de-datos.md`](../reference/capa-de-datos.md) para el mapa completo: qué devuelve cada herramienta del stack y a qué familia de insight llega.

## Por qué existe un agente selector, además del generador

El motor genera muchos candidatos de insight por auditoría. La mayoría son ruido: repiten el mismo hallazgo con otras palabras, son demasiado genéricos, o son ciertos pero suficientemente humillantes como para arruinar la puerta de entrada. Por eso la selección son dos nodos distintos, no uno:

- **El agente selector (nodo `SEL`)** — un llamado más a Claude, que rankea cada candidato por criterios que requieren juicio: fuerza de la evidencia que lo respalda, relevancia al objetivo indicado, qué tan lejos está de un consejo genérico aplicable a cualquier sitio, si es accionable a través del sitio web, y el riesgo de insultar. Es un agente y no código porque estos criterios son subjetivos, no una fórmula.
- **El nodo de código (`COL`)** — determinístico, sin IA: colapsa los hallazgos relacionados en una sola tesis (para no repetir el mismo punto dos veces con distinta evidencia) y fuerza que los insights finales toquen familias distintas entre sí. Esto sí es una regla mecánica, así que no hace falta gastar una llamada a un LLM en resolverla.

El resultado final no son 5 variaciones del mismo problema, sino un panorama de ángulos distintos.

## Por qué n8n como capa de orquestación, y no un backend a medida

Como Cristopher va a operar todo el proyecto sobre n8n, sus nodos HTTP Request llaman a cada fuente de datos de la capa de evidencia, y sus nodos de IA generan y seleccionan los insights — no hace falta programar ni hostear un backend aparte. Para este MVP el trigger es manual porque no hay ningún canal (web, mail) esperando el resultado en el momento; si más adelante se retoma la idea de un self-serve web (ver [`roadmap.md`](../roadmap.md)), ese trigger manual se reemplaza por un webhook sin tocar el resto del pipeline.
