# Stack técnico evaluado

Todas las cuentas y suscripciones corren a cargo de Cristopher. Este documento resume las opciones evaluadas por función, priorizando pago por uso sobre suscripción fija — el volumen de uso inicial del producto todavía es incierto, así que no tiene sentido comprometerse a un mínimo mensual alto desde el día uno.

| Función | Herramienta elegida | Presupuesto estimado (mensual) | Alternativa | Por qué esta y no la otra |
|---|---|---|---|---|
| Motor de razonamiento (LLM que genera y estructura los insights) | Claude Sonnet 4.6 | USD 10–40 (según volumen de audits) | GPT-5 (USD 1.25 / USD 10 por millón de tokens) | Consistencia con el resto del sistema; la diferencia de precio no justifica cambiar de proveedor acá |
| Orquestación del pipeline | n8n | Ya pago por Cristopher — USD 0 adicional | — | Decisión ya tomada, todo el proyecto vive ahí |
| Performance del sitio (Core Web Vitals) | Google PageSpeed Insights API | USD 0 (gratis, 25.000 consultas/día) | WebPageTest API Pro (USD 18.75/mes) | Gratis y confiable, no hay razón para pagar algo equivalente |
| Detección de stack tecnológico | Desarrollo propio (nodo HTTP en n8n + parsing de firmas conocidas) | USD 0 (solo horas de desarrollo) | BuiltWith / Wappalyzer API (USD 250–295/mes) | Suscripción cara para algo puntual mientras el volumen es incierto |
| Datos SEO reales (rankings, keywords) | DataForSEO | USD 50 (carga mínima; cubre volumen bajo-medio) | Ahrefs API (USD 249/mes) | Pay-per-use tiene más sentido que un mínimo mensual alto desde el día uno |
| Test de AEO (presencia en respuestas de LLMs en vivo) | API de Perplexity (Sonar), armado a medida | USD 1–5 | Otterly.ai (desde USD 29/mes) | Uso puntual por audit, no monitoreo continuo |
| Búsqueda web con fuente y fecha (funding, headcount, founders) | SerpAPI (plan gratis) / Exa (pago por uso) | USD 0–7 | SerpAPI de pago (USD 25/mes) | Alcanza de sobra para el volumen inicial |
| Lectura de sitio propio y de competidores | Firecrawl (cuenta propia de Cristopher) | USD 0–16 | ScrapingBee (desde USD 49/mes) | Más barato y ya evaluado desde el arranque |
| Hosting del frontend estático (landing, formulario, resultados) | Vercel Hobby | USD 0 | GitHub Pages | Más simple si más adelante hace falta un dominio propio |
| **Total estimado** | | **≈ USD 61–118/mes** | | |

> El rango depende directamente de cuántos audits se corran por mes — es un costo variable que crece con el uso del producto, no una suscripción fija. **Este costo es aparte y no forma parte del fee de implementación** — es lo que le cuesta a Cristopher operar su propia solución una vez construida.

> **Nota sobre el gate de mail:** no hace falta una herramienta externa tipo Tally — el formulario ya es una pantalla propia del frontend, que postea directo al webhook de n8n (ver [`explanation/arquitectura.md`](../explanation/arquitectura.md)).

## Nota operativa

Cada cuenta y API key la crea y paga Cristopher. Durante el desarrollo se comparte acceso temporal de forma segura (nunca por WhatsApp o mail en texto plano — un gestor de contraseñas compartido o variables de entorno). Se recomienda rotar las keys una vez finalizado el proyecto, para que el acceso de desarrollo no quede activo indefinidamente.
