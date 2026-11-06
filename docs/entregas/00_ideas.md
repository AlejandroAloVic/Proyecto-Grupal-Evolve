# EQUIPO
Miembros del grupo:
- Alejandro Alonso Vicente
- Pablo Sacie Moreno
- Alba López Gadea
- Jamilton Daniel Vinueza Chalco

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

## Idea trabajo

### Título y descripción
Recomendador de ofertas de empleo según el perfil profesional. Herramienta que recomienda ofertas de empleo según las competencias, la formación y la experiencia del usuario. Además de ordenar las ofertas por compatibilidad, explica qué requisitos cumple, cuáles no se han identificado en su perfil y qué competencias podría mejorar.

### Problema y usuario
Está dirigida principalmente a personas con poca experiencia profesional, como estudiantes y recién graduados, que tienen dificultades para identificar qué puestos encajan con sus capacidades e interpretar los requisitos de las ofertas. Actualmente recurren a portales de empleo, búsquedas por palabras clave y revisiones manuales, métodos que no siempre permiten valorar de forma clara la compatibilidad entre su perfil y cada puesto.

### Uso y valor
El usuario introduce su perfil mediante un formulario y, si resulta viable, podrá cargar su CV. El sistema compara esa información con las ofertas disponibles y muestra las más relevantes, explicando las competencias coincidentes y los requisitos que faltan o no aparecen en el perfil. Así podrá priorizar a qué ofertas presentarse y detectar aspectos que mejorar para aumentar sus oportunidades laborales. Como posible ampliación futura, se podrían sugerir otras ocupaciones compatibles y las competencias necesarias para acceder a ellas.

### Datos
Se necesitan ofertas reales de empleo y una clasificación de referencia de ocupaciones y competencias. Las fuentes candidatas para las ofertas de empleo son:  
- Adzuna API: https://developer.adzuna.com/overview. Primera opción que se está evaluando, con posibilidad de filtrar por ubicación. Se ha consultado al proveedor sobre el registro como estudiante y el uso académico de los datos, incluido su almacenamiento temporal y análisis. El acceso y los permisos están pendientes de confirmación. 
- Headcount Labs: https://headcountlabs.com/countries/spain/. Alternativa para obtener ofertas de España. Queda pendiente comprobar el acceso efectivo, las condiciones del plan disponible y los permisos de uso y almacenamiento. 
- Feina Activa: https://feinaactiva.gencat.cat/api/offers/offers-xml. Ofrece posibles datos en formato XML, pero se centra en Cataluña. Es necesario comprobar la licencia, la estructura y la calidad de los datos. 
- ECYL: https://jcyl.opendatasoft.com/explore/dataset/ofertas-de-empleo/api/. Alternativa de ofertas estructuradas de Castilla y León, cuya disponibilidad y condiciones de reutilización están pendientes de verificar. 
La fuente de referencia candidata para las competencias es ESCO (https://esco.ec.europa.eu/en/use-esco/download), una clasificación europea de ocupaciones y habilidades.

### Primera versión o MVP
Incluirá un formulario para introducir el perfil, la obtención y el procesamiento de ofertas de una fuente validada, la comparación de competencias y requisitos y un listado de ofertas ordenadas por compatibilidad con una explicación de cada resultado. 
El alcance inicial se limitará a personas con poca experiencia y a una ubicación concreta. Quedan fuera la recomendación de trayectorias profesionales alternativas, las candidaturas automáticas, la gestión de solicitudes y la integración con cuentas de portales de empleo.

### Viabilidad y dudas
La principal incertidumbre es conseguir suficientes ofertas detalladas que puedan utilizarse legalmente. También habrá que comprobar si es posible extraer requisitos de textos redactados en lenguaje natural y evaluar la utilidad de las recomendaciones. Para ello, habría que probar las fuentes con una muestra pequeña, revisando su acceso, cobertura, estructura, calidad y condiciones de uso. Por último, se contrastaría con usuarios potenciales si las recomendaciones y sus explicaciones les ayudan a elegir mejor las ofertas.

## Idea Piezas Defectuosas

### Título y descripción

Detectar defectos en piezas prefabricadas de hormigón mediante Inteligencia Artificial. La idea consiste en desarrollar una aplicación que analice fotografías de piezas de hormigón para identicar posibles defectos, como grietas, roturas o irregularidades en la superficie. 


### Problema y usuario
Esta idea está pensada para empresas que se dedican a fabricar piezas prefabricadas de hormigón, donde el control de calidad es una parte importante del proceso. La revisión de las piezas suele hacerse siguiendo planos y especificaciones técnicas, sin embargo, una vez terminadas las piezas, pueden aparecer defectos en la superficie, que deben ser identificados y revisados. Esta herramienta esta dirigido al personal de calidad para facilitar la inspección de las piezas antes de su entrega.

### Uso y valor
El personal de calidad podrá utilizar la aplicación para cargar fotografías de las piezas de hormigón una vez fabricadas. El sistema analizará las imágenes para identificar posibles defectos y señalará las piezas que necesitan una revisión. De esta manera, la empresa podrá agilizar las inspecciones, llevar un registro de los defectos encontrados y reducir el riesgo de que una pieza defectuosa pase desapercibida. 

### Datos

Se necesitan fotografías de superficies de hormigón, tanto con defectos como en buen estado. 
Se han encontrado tres posibles fuentes: 
- SDNET2018: https://digitalcommons.usu.edu/all_datasets/48/ . Primera alternativa para comenzar, esta base de datos contiene 56000 imágenes, fue publicada en el 2018 por la Universidad Estatal de Utah y están clasificadas según tengan grietas o no, los datos son públicos, por lo que pueden utilizarse citando su procedencia, lo que nos quedaría pendiente es comprobar su funcionamiento con imágenes de piezas prefabricadas, ya que las imágenes proceden de puentes, muros y pavimentos. 
- ConViD: https://data.mendeley.com/datasets/fx3rthfjhy/4. Contiene fotografías reales de grietas, coqueras, huecos y desconchamientos, tomadas con teléfonos móviles en diferentes condiciones climáticas, se podría utilizar para ampliar la detención de otros defectos, queda pendiente revisar la cantidad y distribución de imágenes. 
- HiC: https://github.com/jdkuhnke/HiC. Esta base contiene imágenes coqueras en hormigón, algunas con anotaciones que permiten localizar los defectos, su uso está permitido para investigación no comercial, por lo que se debería revisar las condiciones si el proyecto llegara a comercializarse. 

### Primera versión o MVP
El usuario carga las fotografías de piezas de hormigón en la aplicación, está analizará las imágenes para identificar posibles grietas y mostrará el resultado para que el personal de calidad pueda revisarlo. También se buscará guardar un registro de las inspecciones realizadas y los defectos detectados. 
Al inicio, el proyecto se centrará en la detección de grietas. Si los datos y el tiempo lo permiten, se ampliará a otros defectos, como coqueras y desconchamientos. 


### Viabilidad y dudas

La principal dificultad será conseguir imágenes que representen las condiciones reales de fabricación de piezas prefabricadas, debido a que las bases de datos encontradas proceden principalmente de otras estructuras de hormigón. También se debe comprobar que el modelo si es capaz de detectar las grietas con suficiente precisión. 
Para evaluar la viabilidad del proyecto se realizarán pruebas con las bases de datos disponibles. Si es posible, sería interesante contar con fotografías de una empresa fabricante para comprobar su funcionamiento en un entorno real. 
