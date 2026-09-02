# Arquitectura

## Diagrama de flujo

```mermaid
flowchart TD
    A[Input: URL + objetivo] --> B1

    subgraph CapaDatos [Capa de datos - 3 niveles de confiabilidad]
        B1[Barato y confiable<br/>Performance, stack tecnológico,<br/>test de AEO, análisis de texto/diseño]
        B2[Recuperable<br/>Funding, headcount, posts de founders<br/>con fuente y fecha]
        B3[Difícil / riesgoso<br/>Rankings SEO reales<br/>usar con cautela]
    end

    B1 --> C
    B2 --> C
    B3 --> C

    subgraph Candidatos [Generación de candidatos - 6 familias]
        C1[Posicionamiento y narrativa]
        C2[Demanda y visibilidad en AI]
        C3[Funnel y conversión]
        C4[Capacidad de growth]
        C5[Credibilidad]
        C6[Cobertura de comité de compra]
    end

    C[Candidatos generados] --> D[Función de selección]
    D --> D1["Rankea por: fuerza de evidencia,<br/>relevancia al objetivo,<br/>distancia de lo genérico,<br/>accionabilidad,<br/>riesgo de insulto en frío"]
    D1 --> D2[Colapsa hallazgos relacionados<br/>+ fuerza diversidad de familias]

    D2 --> E{Instancia}
    E --> E1[Cold Reach<br/>1 solo hook]
    E --> E2[Follow-up post-call<br/>mini pre-SOW]
    E --> E3[Inbound self-serve<br/>4-5 insights completos]
```

## Los 3 niveles de evidencia

Cada insight cita de dónde sale cada dato, y eso define cómo se afirma:

| Origen | Cómo se afirma | Ejemplos |
|---|---|---|
| **Medido** | Directo, como hecho | Lighthouse, stack detectado, ranking real, presencia en respuesta de un LLM corriendo la query en vivo |
| **Recuperado** | Con fuente y fecha chequeada | Ronda de inversión, post de un founder, headcount |
| **Inferido** | Como hipótesis, nunca como hecho | "Las señales sugieren que..." |

## El objetivo determina el framing, no el contenido

El mismo hallazgo cambia de titular según el objetivo de la empresa analizada. Un sitio sin proof, para quien levanta funding es "no parecés fundable"; para quien quiere clientes es "no generás confianza para convertir". El objetivo no crea insights nuevos — decide cuáles suben al top y con qué encabezado.

- **En inbound:** el objetivo lo captura el onboarding del formulario.
- **En cold reach:** lo infiere el agente a partir del contexto (ej: una empresa que levantó ronda y contrata un growth lead tiene, probablemente, el objetivo de escalar pipeline).
