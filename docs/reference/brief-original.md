# Brief original — Audit Structure

> Transcripción del requerimiento tal como lo pasó Cristopher Echevarría en Notion. Es el documento fuente; el resto de la documentación en este repo es la interpretación y el plan de implementación sobre esta base.

> **Nota de alcance (MVP):** la sección "Instancias" de más abajo describe Cold Reach, Follow-up post-call e Inbound como si fueran 3 salidas que el sistema tiene que generar. Se corrigió esa lectura: **el producto genera una sola auditoría completa** — lo que Cristopher hace después con ella (usarla en frío, profundizarla en una llamada, entregarla a un lead) es su propio proceso comercial, no software. Ver [`archive/v1-con-instancias/NOTA-DE-ARCHIVO.md`](../../archive/v1-con-instancias/NOTA-DE-ARCHIVO.md) para el detalle de este cambio de alcance. El resto del brief (composición, anatomía del insight, tipos, niveles de evidencia) sigue vigente tal cual.

## Qué es

No es un checklist del sitio como lo ejecutan la mayorías de las otras agencias *(Flow Ninja, Flowout, Digidop)*.

Es una tesis de growth: lo más valioso que el marketing website de una empresa podría hacer por su objetivo actual, identificando growth opps y gaps de sus competidores, respaldado por lo observable. **El output es un stack de 4 o 5 insights sin ofrecer una solución directa, sino, una primera oportunidad para salir del típico cold reaching.**

## Composición

1. El lever de cada insight tiene que ser el sitio web.
2. Cada insight se apoya en evidencia observable, medible o garantizable. Sin evidencia, no hay insight.

## Cómo se afirma cada dato

Todo dato lleva una de tres etiquetas de origen, y eso define cómo se dice:

- **Medido:** se afirma directo. Lighthouse, stack detectado, ranking real, presencia en respuestas de AI corriendo la query en vivo.
- **Recuperado:** se afirma con fuente y fecha chequeada. Ronda de inversión, post de un founder, headcount.
- **Inferido:** se dice como hipótesis, nunca como hecho. "Las señales sugieren que…"

## Anatomía

Cada insight es un objeto con estos campos: tipo, objetivo al que sirve, claim (la observación), evidencia (cada pieza con su origen etiquetado), mecanismo (la consecuencia como causa y efecto, no como ROI), dirección (el movimiento, con el sitio como lever), confianza (derivada del origen de la evidencia), y línea de servicio.

Lo que lo hace bueno es que encadena, no que suma temas: observación con evidencia, por qué importa contra los competidores, qué cuesta como mecanismo, y la dirección. El genérico se queda en el primer paso y lo aplana a "arreglá esto".

## Ejemplo del molde

**Genérico:** "mejorá el H1."

**Como lo queremos:**

El value prop que comunicás en el sitio y el de tus cuatro competidores más cercanos abren con el mismo claim [claim example], así que el buyer al que targeteás [ICP] no te distingue.

Desventajas:
- Lista 1
- Lista 2
- Lista 3

Lo único que solo vos podés decir aparece en el LinkedIn de tu CEO y en ninguna parte del sitio [recuperado].

Nuestra oportunidad: identificar [posible accionar].

## Tipos de insight

- **Posicionamiento y narrativa:** diferenciación nula contra competidores, mensaje que no calza con el ICP, narrativa que no acompaña la etapa, fuga de narrativa del founder (dice en LinkedIn a dónde va, el sitio no lo refleja).
- **Demanda y visibilidad en AI:** whitespace de keywords que los competidores rankean y la empresa no, ausencia en las respuestas de los LLMs de la categoría.
- **Funnel y conversión:** sitio como brochure y no como herramienta de sales, sin camino para el visitante interesado pero no listo.
- **Capacidad de growth:** stack lento que frena shippear, vertical de producto que el sitio no explota.
- **Credibilidad:** promesa (pricing enterprise, etapa de funding) que la prueba del sitio no respalda.
- **Cobertura de comité de compra:** el sitio le habla a un rol cuando la decisión la toman varios.

## El objetivo

El mismo hallazgo cambia de titular según el objetivo de la empresa. Un sitio sin proof, para el que levanta funding es "no parecés fundable", para el que quiere clientes es "no generás confianza para convertir". El objetivo no crea insights nuevos, decide cuáles suben al top y con qué framing. En inbound lo da el onboarding. En cold reach lo infiere el agente del contexto (una empresa que levantó ronda y contrata un growth lead tiene objetivo de escalar pipeline).

> *En el MVP, el objetivo es un dato que el visitante declara en el formulario junto con la URL — ver [`explanation/filosofia-del-insight.md`](../explanation/filosofia-del-insight.md).*

## Organización

El agente genera muchos candidatos. Una función de selección los rankea por fuerza de la evidencia, relevancia al objetivo, distancia de lo genérico y accionabilidad vía sitio. En cold reach se suma un criterio, riesgo de insulto, porque en frío un insight cierto pero humillante cierra la puerta. Después se colapsan los hallazgos relacionados en una sola tesis stackeada, y se fuerza que los 5 toquen familias distintas.

## Instancias

> *Ver la nota de alcance al principio de este documento — esta sección describe el proceso comercial de Cristopher, no una función del producto.*

- **Cold reach:** objetivo inferido. Se muestra un solo hook, el insight más verificable, interesante y menos insultante, para que la charla arranque de ahí. Exige al menos una evidencia medida o recuperada.
- **Follow up post-call:** objetivo locked de la conversación. Más profundo, referenciado a lo que se habló. Es un mini pre-SOW.
- **Inbound:** el onboarding captura el objetivo. Self-serve, gateado detrás del mail. Tiene que crear deseo de la call.

## Realidad de la data

- **Barato y confiable:** stack, Lighthouse, tests de AEO con query en vivo a los LLMs, análisis de texto y diseño del sitio propio y de competidores.
- **Recuperable pero sensible a la fecha:** funding, headcount, posts de founders. Requiere búsqueda web con fuente y fecha, no memoria del modelo.
- **Difícil o riesgoso:** ranking real de keywords necesita una fuente de datos SEO de verdad, un LLM no las sabe. Market share y scraping de LinkedIn son frágiles. Runway, "el producto funciona" y "el equipo no puede shippear" son inferencia, confianza baja.
