# Stack técnico evaluado

Todas las cuentas y suscripciones corren a cargo de Cristopher. Este documento resume las opciones evaluadas por función, priorizando pago por uso sobre suscripción fija — el volumen de uso inicial del producto todavía es incierto, así que no tiene sentido comprometerse a un mínimo mensual alto desde el día uno.

| Función | Recomendado para arrancar | Alternativa (mejor si escala en volumen) |
|---|---|---|
| Motor de razonamiento | Claude Sonnet 4.6 | GPT-5 |
| Performance del sitio (Core Web Vitals) | Google PageSpeed Insights API — gratis | WebPageTest API Pro |
| Detección de stack tecnológico | Desarrollo propio (lectura de HTML + firmas conocidas) | BuiltWith / Wappalyzer API |
| Datos SEO reales (rankings, keywords) | DataForSEO — pago por uso | Ahrefs API |
| Test de AEO (Answer Engine Optimization) | API de Perplexity (Sonar), armado a medida | Otterly.ai |
| Búsqueda web con fuente y fecha | SerpAPI (plan gratis) / Exa (pago por uso) | SerpAPI de pago |
| Lectura de sitio propio y de competidores | Firecrawl | ScrapingBee |
| Hosting (Instancia inbound / web) | Vercel Hobby — gratis | Railway |
| Captura de mail + formulario | Tally — gratis | Kit (ex ConvertKit) |

## Nota operativa

Cada cuenta y API key la crea y paga Cristopher. Durante el desarrollo se comparte acceso temporal de forma segura (nunca por WhatsApp o mail en texto plano — un gestor de contraseñas compartido o variables de entorno). Se recomienda rotar las keys una vez finalizado el proyecto, para que el acceso de desarrollo no quede activo indefinidamente.
