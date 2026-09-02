# Tutorial: armar un primer insight a mano, de punta a punta

Este tutorial recorre el proceso completo con un ejemplo ficticio — la empresa inventada **"Nortia" (nortia.io)**, una startup B2B de software. El objetivo es que veas, paso a paso, cómo una observación cruda se convierte en un insight terminado, sin saltarte ninguno de los pasos que el motor automatiza en la Fase 1 del proyecto (ver [`roadmap.md`](../roadmap.md)).

## Paso 1 — Definís el input

- **URL:** nortia.io
- **Objetivo:** en este ejemplo lo conocemos porque es inbound — Nortia lo declaró en el onboarding: *"queremos más demos calificadas"*.

## Paso 2 — Recolectás datos en los 3 niveles

Vas juntando evidencia y la etiquetás por origen a medida que la encontrás (ver [`reference/niveles-de-evidencia.md`](../reference/niveles-de-evidencia.md)):

- **Medido:** corrés Lighthouse sobre nortia.io y sobre sus 3 competidores directos. Nortia carga en 4.2s; los 3 competidores cargan en menos de 2s.
- **Medido:** leés el texto de la home de Nortia y de los 3 competidores. Los 4 sitios abren con una variación de "la plataforma todo-en-uno para tu equipo".
- **Recuperado:** buscás en LinkedIn el perfil del CEO de Nortia (con fecha de la búsqueda) y encontrás un post de hace 3 semanas hablando de "ser la única plataforma pensada para equipos remotos-first" — esa frase no aparece en ningún lado del sitio.
- **Inferido:** no hace falta para este ejemplo, pero si dijeras algo como "probablemente su equipo de producto está sobrecargado", eso iría acá, marcado como hipótesis.

## Paso 3 — Generás candidatos en las familias relevantes

Con esta evidencia, el dato del mismo claim que los competidores encaja en la familia **Posicionamiento y narrativa** (ver [`reference/tipos-de-insight.md`](../reference/tipos-de-insight.md)). El dato de velocidad de carga podría ir a **Capacidad de growth**, pero es más débil todavía sin conectarlo a una consecuencia de negocio.

## Paso 4 — Aplicás el checklist de calidad

Repasás [`how-to/evaluar-la-calidad-de-un-insight.md`](../how-to/evaluar-la-calidad-de-un-insight.md) contra el candidato de posicionamiento:

- ¿Lever es el sitio web? Sí.
- ¿Tiene evidencia etiquetada? Sí — dos medidas (texto propio y de competidores) y una recuperada (el post del CEO).
- ¿Encadena? Todavía no — falta conectar "por qué importa" y "mecanismo".
- ¿Es genérico? El claim compartido sí lo es, pero la evidencia del post del CEO lo vuelve específico de Nortia.
- ¿Es accionable vía sitio? Sí — se puede reescribir la home.
- Objetivo declarado (más demos calificadas) → esto encaja: un mensaje indistinguible de la competencia reduce las demos calificadas porque el visitante no entiende por qué elegir Nortia.

## Paso 5 — Armás el objeto insight final

Siguiendo el schema de [`reference/insight-object.md`](../reference/insight-object.md):

```
tipo: Posicionamiento y narrativa
objetivo: Más demos calificadas
claim: El value prop de nortia.io y el de sus 3 competidores directos abren con la misma
       promesa ("plataforma todo-en-uno para tu equipo"), así que un visitante que llega
       comparando opciones no tiene forma de distinguir a Nortia del resto.
evidencia:
  - [medido] Home de Nortia y de los 3 competidores comparadas, mismo claim central
  - [recuperado, fecha de búsqueda incluida] Post de LinkedIn del CEO (hace 3 semanas):
    "ser la única plataforma pensada para equipos remotos-first" — no aparece en el sitio
mecanismo: Un visitante que no distingue a Nortia de sus 3 alternativas más cercanas agenda
           menos demos calificadas — compara por precio o abandona, en vez de elegir por
           diferenciación.
dirección: Llevar la narrativa de "remotos-first" del LinkedIn del CEO a la home, donde
           hoy no existe.
confianza: Media-alta (mezcla evidencia medida con una recuperada bien fechada)
línea_de_servicio: Copywriting / mensaje de marca
```

Compará este resultado contra el ejemplo genérico ("mejorá el H1") de [`explanation/filosofia-del-insight.md`](../explanation/filosofia-del-insight.md) — la diferencia es que este insight no se podría haber escrito sin mirar a los 3 competidores y sin buscar qué dice el CEO afuera del sitio.

## Siguiente paso

Este mismo proceso, hecho a mano acá, es lo que la Fase 1 del proyecto (ver [`roadmap.md`](../roadmap.md)) automatiza — primero corriendo contra sitios reales para calibrar que la calidad se mantenga sin intervención manual.
