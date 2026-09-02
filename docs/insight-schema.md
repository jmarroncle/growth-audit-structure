# El objeto Insight

Cada insight que genera el motor es un objeto con estos campos:

| Campo | Qué contiene |
|---|---|
| `tipo` | Una de las 6 familias (ver [`architecture.md`](architecture.md)) |
| `objetivo` | A qué objetivo de negocio sirve este insight |
| `claim` | La observación central |
| `evidencia` | Cada pieza de evidencia, con su origen etiquetado (medido / recuperado / inferido) |
| `mecanismo` | La consecuencia como causa-efecto — nunca como cálculo de ROI |
| `dirección` | El movimiento sugerido, con el sitio web como lever |
| `confianza` | Derivada del origen de la evidencia que lo respalda |
| `línea_de_servicio` | A qué línea de servicio conecta este insight |

## Por qué esto y no un checklist

Lo que hace bueno a un insight es que **encadena, no suma temas**: observación con evidencia → por qué importa frente a los competidores → qué cuesta como mecanismo → dirección. Un insight genérico se queda en el primer paso y lo aplana a "arreglá esto".

## Ejemplo del molde

**❌ Genérico:**
> "Mejorá el H1."

**✅ Como lo queremos:**
> El value prop que comunicás en el sitio y el de tus cuatro competidores más cercanos abren con el mismo claim [claim example], así que el buyer al que targeteás [ICP] no te distingue.
>
> Desventajas:
> - Lista 1
> - Lista 2
> - Lista 3
>
> Lo único que solo vos podés decir aparece en el LinkedIn de tu CEO y en ninguna parte del sitio *(recuperado)*.
>
> **Nuestra oportunidad:** identificar [posible accionar].

## Selección y organización

El motor genera muchos candidatos. Una función de selección los rankea por fuerza de la evidencia, relevancia al objetivo, distancia de lo genérico y accionabilidad vía sitio. En cold reach se suma un criterio adicional: **riesgo de insulto** — un insight cierto pero humillante cierra la puerta en frío.

Después se colapsan los hallazgos relacionados en una sola tesis stackeada, y se fuerza que los insights finales toquen familias distintas entre sí (diversidad).

## Las 3 instancias de uso

| Instancia | Objetivo | Formato |
|---|---|---|
| **Cold reach** | Inferido del contexto | 1 solo hook — el insight más verificable, interesante y menos insultante. Exige al menos una evidencia medida o recuperada. |
| **Follow-up post-call** | "Locked" de la conversación | Más profundo, referenciado a lo hablado. Es un mini pre-SOW. |
| **Inbound** | Capturado por el onboarding | Self-serve, gateado detrás del mail. Tiene que crear deseo de la call. |
