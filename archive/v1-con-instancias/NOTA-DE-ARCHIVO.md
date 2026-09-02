# Por qué esta versión quedó archivada

Esta fue la primera interpretación del brief de Cristopher: un pipeline que generaba la auditoría y además decidía cómo renderizarla en 3 "instancias" distintas (Cold Reach, Follow-up post-call, Inbound self-serve), con un nodo de switch, un frontend web propio, y fases de roadmap separadas para cada una.

Se corrigió el alcance: **el producto genera una sola cosa, la auditoría completa.** Cold Reach y Follow-up no son software — son Cristopher usando a mano el resultado de una auditoría ya generada dentro de su propio proceso comercial (elegir qué insight mandar en frío, profundizar uno después de una llamada). No hay que construir nada para eso.

Lo único que queda como posible función de producto a futuro es el self-serve web de Inbound (que sí requiere automatización real: alguien entra, pide su auditoría, el sistema se la manda solo) — pero quedó fuera del MVP oficial, que es solo el motor.

Esta carpeta se conserva como referencia histórica de esa primera versión, incluyendo el mockup de UI que se armó para el self-serve web (ya no vigente). La versión oficial vive en la raíz del repo.
