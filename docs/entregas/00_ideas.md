# IDEAS

## Idea eventos

### Título y descripción
Predicción de afluencia y optimización de stock y personal para eventos locales y locales de ocio. Herramienta que predice la afluencia de público a eventos culturales, mercadillos, conciertos locales o locales de ocio en base a factores externos, ayudando a los organizadores a dimensionar correctamente el personal necesario y el aprovisionamiento de materias primas para evitar mermas o pérdidas de venta.

### Problema y usuario
Está dirigida principalmente a pequeños organizadores de eventos, asociaciones culturales, gestores de espacios gastronómicos o pequeños hosteleros que tienen dificultades para estimar cuánta gente acudirá a sus eventos, especialmente cuando no hay un sistema de venta de entradas anticipadas obligatorio. Actualmente planifican el personal y el stock "a ojo" o basándose en experiencias pasadas poco estructuradas, lo que a menudo genera exceso de mermas por sobreestimación o pérdida de ingresos y mala experiencia de usuario por falta de personal.

### Uso y valor
El organizador introduce los datos clave del evento (ubicación, tipo de actividad, fecha, horario y si es al aire libre o en recinto cerrado). El sistema cruza esta información con predicciones meteorológicas, datos de la agenda cultural de la ciudad y patrones históricos similares para devolver una estimación de afluencia esperada. Además, traduce esa predicción en recomendaciones prácticas de negocio: número estimado de asistentes, sugerencia de personal en barra/sala y volumen orientativo de aprovisionamiento. Como posible ampliación futura, se podrían añadir alertas automáticas de coincidencia con grandes eventos masivos en la misma zona que alteren el flujo de público.

### Datos
Se necesitan registros históricos y previsiones en tiempo real de eventos, agenda urbana y factores ambientales. Las fuentes candidatas para las fuentes de datos son:
- AEMET OpenData: (https://opendata.aemet.es/centrodedescargas/info). API oficial de la Agencia Estatal de Meteorología para consultar el histórico climático y las predicciones meteorológicas, factor clave que condiciona la afluencia a eventos al aire libre o locales de ocio.
- Datos.gob.es: (https://datos.gob.es/). Catálogo nacional de referencia que recopila datasets públicos sobre agendas culturales, festivos y eventos de múltiples administraciones del país.
- Portales de Datos Abiertos Autonómicos y Locales: (Como el Portal de la Comunidad de Madrid o el Catálogo de Cultura y Ocio de la Junta de Andalucía en https://www.juntadeandalucia.es/datosabiertos/portal/catalogo-datos/cultura-y-ocio). Facilitan APIs estándar (CKAN / OpenAPI) para la extracción automatizada de eventos culturales, ferias, festivos locales y programación de ocio municipal.

### Primera versión o MVP
Incluirá un formulario sencillo para introducir los parámetros del evento, la conexión con una fuente validada de meteorología y eventos locales, un modelo predictivo básico de estimación de asistencia y un panel que muestre el número previsto de asistentes junto con una recomendación orientativa de stock y personal. El alcance inicial se limitará a un tipo de evento concreto (por ejemplo, mercadillos gastronómicos o pequeños conciertos) y a una única ciudad o zona geográfica piloto. Quedan fuera la integración directa con pasarelas de venta de entradas, la gestión automatizada de proveedores y la contratación directa de personal.

### Viabilidad y dudas
La principal incertidumbre es la disponibilidad y calidad de datos granulares sobre eventos pequeños que no dejen registro digital masivo, así como comprobar si los modelos predictivos logran un error aceptable con variables externas como el clima. Para evaluar la viabilidad, se realizarán pruebas preliminares cruzando una muestra de eventos pasados reales con los datos meteorológicos e históricos de la AEMET y la agenda municipal. Por último, se contrastará con organizadores locales si las estimaciones y las recomendaciones de stock les resultan intuitivas y útiles para su operativa diaria.

## Idea 2

...

## Idea 3

...
