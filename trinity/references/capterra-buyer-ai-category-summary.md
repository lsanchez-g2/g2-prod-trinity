# Worked Example: AI-Generated Category Summary on Capterra Category Pages

This example shows the trio framework applied to a Capterra Buyer Experience decision. Use as a format anchor.

---

## User question

> "Estamos pensando añadir un bloque de resumen generado por IA al principio de las category pages en Capterra. Sería un párrafo que explique la categoría, los criterios típicos de selección, y un resumen de los líderes según las reviews. ¿Lo lanzamos en Q3?"

---

## Brand and side detected

- **Brand**: Capterra
- **Trio side**: Buyer Experience
- Loaded: `brands/capterra.md`, `lenses/buyer-experience.md`, plus the three POV references and `disagreement-patterns.md`

---

## POV Designer

El bloque va al inicio de la página, justo donde el buyer está escaneando para construir un primer mapa mental de la categoría. Es una posición de alta confianza y por eso de alto riesgo.

Tres preocupaciones del Designer:

1. **El comportamiento típico en Capterra es scan-first, no read-first**. Un párrafo extenso al inicio compite con la lista de productos por la atención. El bloque tiene que ser visualmente diferenciado pero no robarle al usuario su patrón de "ojear lista, click rápido". Si el bloque añade dos pantallazos antes de que se vea el primer producto, el comportamiento se rompe.

2. **Verificación y citación**. Cuando el resumen dice "los líderes destacan por X", el buyer tiene que poder confirmar de dónde sale eso. Sin links a las reviews concretas o al menos a los productos mencionados, el bloque es decoración o es una caja negra que el buyer va a desconfiar más cuanto más se fije.

3. **Estados degradados**. Categorías con menos de 30 reviews, categorías nuevas, categorías de nicho. El resumen no puede ser uniforme. El estado "esta categoría es nueva, faltan datos" es tan importante como el estado normal.

## POV Developer

Tres preocupaciones del Developer:

1. **No generar por pageview**. Capterra tiene ~900-2000 categorías y 5.1M visitas/mes. Generar el resumen en cada carga es absurdo en coste y latencia. El patrón es: generación batch a nivel de categoría, cache con TTL (24-48h), regenerar cuando el delta de reviews supera un umbral o cuando se actualiza el ranking.

2. **Eval harness antes del lanzamiento**. El resumen va a salir al frontend de la marca. Una tasa de hallucination del 5% en 1500 categorías = decenas de páginas con afirmaciones inventadas, indexadas por Google. El eval set tiene que cubrir: categorías con poca data, categorías con liderazgo disputado, categorías recién creadas, categorías multilingües.

3. **SEO**. Este es el punto que el Designer y el PM probablemente subestiman. Bloque AI-generated en el top de category page = contenido que Google va a clasificar como AI-generated. E-E-A-T se ve afectado. Si el bloque es genérico (parecido entre categorías relacionadas), Google puede leerlo como contenido de baja calidad. Hay que: marcar `<meta>` apropiados, asegurar uniqueness real entre categorías, no canibalizar el contenido editorial existente.

Esquema de implementación: pipeline batch → eval contra reference set en cada cambio de prompt → output cacheado → fallback a "no AI summary" si el eval falla o si la categoría está en lista de exclusión.

## POV Product Manager

Trabajando hacia atrás desde outcomes:

1. **¿Qué outcome estamos sirviendo?** Hipótesis: el resumen acelera el time-to-shortlist del buyer y aumenta el click-through al producto correcto. Métrica leading: time-to-first-product-click + click-through a perfiles relevantes. Métrica lagging: leads de calidad a vendors.

2. **¿Cuál es el assumption más arriesgado?** No es "podemos generar resúmenes" (podemos). No es "los buyers van a leerlo" (lo van a leer dada la posición). El más arriesgado es: **"el resumen ayuda al buyer más de lo que lo confunde o lo hace salir satisfecho sin click a vendor"**. Si el resumen genera la sensación de "ya sé suficiente", el click-to-vendor cae y los vendors se quejan.

3. **¿Cuál es el test más barato?** A/B test en las 100 categorías de mayor tráfico. Sample size para detectar 3% de lift en click-to-vendor: dos semanas a tráfico de Capterra. Métricas: time on page, click-through a producto, click-to-vendor, exit rate.

El PM también marca: **comunicación a vendors**. Vendors con reviews mixtas o pocas reviews van a ver que ellos no aparecen en el resumen, o que aparecen con framing crítico. Mecanismo de feedback y appeal tiene que lanzarse con la feature, no después.

## Disagreement

Dos tensiones reales:

**Designer vs PM en cobertura.** Designer quiere suprimir el resumen en categorías de poca data para evitar resúmenes pobres sobre datos pobres. PM quiere cobertura amplia para testear la hipótesis a escala y para evitar crear una experiencia de dos clases que vendors puedan gamear (subiendo reviews para cruzar el umbral). Resolución: tier explícito. Bajo 30 reviews, mostrar un bloque editorial corto del tipo "Esta categoría tiene cobertura limitada por ahora - revisa las reviews disponibles abajo". No es un estado faltante, es un estado diseñado. PM consigue cobertura de un experimento bounded; Designer mantiene el suelo de confianza.

**Developer vs PM en sequencing.** Developer quiere eval harness, telemetría de coste, y fallback locked antes del primer A/B. PM quiere arrancar el A/B en semana 4 de Q3 para tener datos antes de Q4 planning. Resolución: dev-led semanas 1-2 (eval, coste, fallback), semana 3 piloto interno (G2 group employees como buyers), semanas 4-7 A/B externo 50/50 en top 100 categorías. PM consigue los datos; Developer no lanza a ciegas. Comunicación a vendors en semana 3, no semana 4.

Designer y Developer convergen en la accesibilidad (resumen anunciado por screen reader, navegable por teclado, citas como links accesibles) y en el estado de baja-data (texto editorial, no componente faltante).

## Recommendation

**Lanzar A/B en Q3 con tres precondiciones.**

1. Eval harness cubre los failure modes nombrados (poca data, liderazgo disputado, nuevas, multilingüe), con threshold claro (e.g., precisión factual ≥ 95% en set etiquetado).
2. Telemetría de coste activa desde el primer piloto, con alertas semanales por presupuesto.
3. Estado "categoría con poca data" diseñado y construido como first-class, no como afterthought.
4. SEO surface revisado: `<meta>`, uniqueness real, no canibalización del contenido editorial existente, marcado de AI-generated content donde aplique.

Secuencia: eval e infra semanas 1-2, piloto interno semana 3, A/B externo 50/50 semanas 4-7, decisión semana 8.

Comunicación a vendors en semana 3.

## Why

La recomendación cambia si:

- Eval revela precisión factual bajo 90% en el set etiquetado (no lanzar; rehacer prompt y grounding)
- Proyección de coste excede X% del coste de infraestructura de category pages (renegociar modelo o estrategia de cache)
- Piloto interno destapa un failure mode UX que el trio no vio (no pasar a A/B externo hasta resolverlo)
- Vendor success team marca un riesgo comercial no modelado (escalar antes del lanzamiento)
- SEO team detecta degradación en muestra de categorías piloto (revisar uniqueness y E-E-A-T antes de seguir)

## Validation

**Riskiest assumption**: el resumen ayuda al buyer en su decisión sin canibalizar el click-through a vendor.

**Cheapest test**: A/B 50/50 en top 100 categorías, dos semanas.

**Signal**: click-to-vendor en variante debe ser ≥ control con 95% de confianza. Time on page puede subir o bajar - el indicador leading es el click downstream, no el engagement aislado.

**Decision rule**:
- Variante gana en click-to-vendor por ≥ 2% con significancia: rollout a 100% de categorías top, expandir a long-tail con cuidado
- Variante a ±1% del control: mantener 50%, estudio cualitativo para entender por qué es neutral
- Variante pierde por > 2%: rollback, diagnóstico, rediseño antes de re-test
- Caída en organic traffic > 5% en muestra: rollback inmediato, revisión SEO independiente del A/B
