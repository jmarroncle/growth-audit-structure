# Por qué la arquitectura está armada así

## El flujo completo

Todo el pipeline se orquesta y vive dentro de **n8n** (la herramienta de automatización con la que Cristopher va a operar el proyecto) — no hay un backend separado. n8n recibe el trigger, llama a cada fuente de datos con nodos HTTP Request, llama al modelo para generar y seleccionar los insights, y entrega el resultado por el canal que corresponda a cada instancia.

```mermaid
flowchart TD
    subgraph N8N [n8n - orquestación completa del pipeline]
        direction TB

        subgraph Triggers [Triggers de entrada]
            T1[Webhook: formulario inbound]
            T2[Trigger manual / cron: cold reach]
            T3[Webhook: CRM - llamada finalizada]
        end

        T1 --> IN[URL + objetivo]
        T2 --> IN
        T3 --> IN

        IN --> B1

        subgraph CapaDatos [Nodos HTTP Request - Capa de datos]
            B1[Barato y confiable<br/>PageSpeed, stack tecnológico,<br/>test de AEO, análisis de texto/diseño]
            B2[Recuperable<br/>Búsqueda web con fuente y fecha<br/>funding, headcount, posts de founders]
            B3[Difícil / riesgoso<br/>SEO real vía DataForSEO/Ahrefs]
        end

        B1 --> C
        B2 --> C
        B3 --> C

        C[Nodo AI: genera candidatos<br/>en las 6 familias] --> D["Nodo AI/Code: función de selección<br/>(evidencia, relevancia, distancia de lo<br/>genérico, accionabilidad, riesgo de insulto)"]
        D --> D1[Colapsa hallazgos relacionados<br/>+ fuerza diversidad de familias]

        D1 --> E{Nodo Switch: instancia}
        E --> E1[Cold Reach<br/>1 solo hook]
        E --> E2[Follow-up post-call<br/>mini pre-SOW]
        E --> E3[Inbound self-serve<br/>4-5 insights completos]
    end

    E1 --> O1[Nodo salida:<br/>mensaje para SDR/LinkedIn]
    E2 --> O2[Nodo salida:<br/>doc o email de follow-up]
    E3 --> O3[Nodo salida:<br/>email al prospecto<br/>+ registro en Sheets/CRM]
```

## Por qué n8n como capa de orquestación, y no un backend a medida

El plan original contemplaba un backend propio (hosteado en algo como Vercel o Railway) para conectar el formulario con el motor. Como Cristopher va a operar todo el proyecto sobre n8n, ese rol lo cumple n8n directamente: sus triggers (webhook, cron, o disparado desde el CRM) reemplazan al backend custom, sus nodos HTTP Request llaman a cada fuente de datos de la capa de evidencia, y sus nodos de IA generan y seleccionan los insights. Esto simplifica el proyecto — una sola herramienta para operar, monitorear y debuggear el pipeline completo, en vez de un backend separado que además de mantenerse necesitaría su propio hosting.

## Por qué 3 niveles de datos y no uno solo

El brief original de Cristopher marca un problema concreto de este tipo de herramientas: un LLM no sabe rankings SEO reales, no sabe si una empresa levantó una ronda la semana pasada, y si se le pregunta igual, inventa una respuesta con la misma confianza que si supiera el dato de verdad. Separar los datos en "barato y confiable", "recuperable pero sensible a la fecha" y "difícil o riesgoso" (ver [`reference/niveles-de-evidencia.md`](../reference/niveles-de-evidencia.md)) obliga al sistema a ser honesto sobre qué tan seguro está de cada afirmación, en vez de sonar igual de seguro sobre todo.

## Por qué existe una función de selección, y no se muestran todos los candidatos

El motor genera muchos candidatos de insight por auditoría. La mayoría son ruido: repiten el mismo hallazgo con otras palabras, son demasiado genéricos, o — en cold reach — son ciertos pero suficientemente humillantes como para cerrar la conversación antes de que empiece. La función de selección existe para hacer ese descarte antes de que el destinatario lo vea, priorizando por:

- fuerza de la evidencia que lo respalda,
- relevancia al objetivo inferido o declarado,
- qué tan lejos está de un consejo genérico aplicable a cualquier sitio,
- si es accionable a través del sitio web,
- y, solo en cold reach, el riesgo de insultar.

Después de rankear, se colapsan los hallazgos relacionados en una sola tesis (para no repetir el mismo punto dos veces con distinta evidencia) y se fuerza diversidad de familias — así el resultado final no son 5 variaciones del mismo problema, sino un panorama de ángulos distintos.

## Por qué el mismo motor sirve para 3 instancias distintas

Cold reach, follow-up post-call e inbound comparten exactamente el mismo pipeline hasta el paso de selección — lo único que cambia es qué objetivo alimenta la generación de candidatos y cuánto del stack seleccionado se muestra. Esto es deliberado: separar "cómo se generan los insights" de "cómo se presentan" evita mantener tres lógicas de negocio distintas y permite que una mejora en la calidad del motor (por ejemplo, mejor detección de evidencia) beneficie a las 3 instancias a la vez. Ver [`reference/instancias.md`](../reference/instancias.md) para el detalle de cada una.
