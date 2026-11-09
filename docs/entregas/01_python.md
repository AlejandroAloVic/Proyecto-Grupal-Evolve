# Idea candidata

Recomendador de ofertas de empleo según el perfil profesional.

# Datos necesarios

# Fichas de fuentes

## Adzuna API

**Estado:** Evaluada y descartada. No utilizada como fuente de datos del proyecto.

#### Origen y acceso

Adzuna es una plataforma de búsqueda de empleo que ofrece una API para consultar información sobre ofertas de trabajo.

Se evaluó como posible fuente de datos para obtener ofertas de empleo que permitieran analizar los requisitos de los puestos y compararlos con la formación, los conocimientos, las habilidades y la experiencia de los candidatos.

**Proveedor:** Adzuna.

**Documentación oficial:** https://developer.adzuna.com/overview

**Método de obtención:** API REST.

**Formato:** JSON.

**Fecha de acceso:** 09/11/2026.

**Proceso de acceso realizado:**

- Se consultó la documentación para desarrolladores de Adzuna.
- Se contactó con el proveedor para consultar las condiciones de uso académico, almacenamiento, transformación y publicación de resultados.
- Se creó una cuenta en el portal Adzuna Developers.
- El registro asignó inicialmente el estado «Pending Activation», con 25 llamadas de prueba.
- Para disponer de acceso completo, el proveedor ofrece un plan de 8 £ mensuales, con 5.000 llamadas al mes y un máximo de 500 llamadas diarias.

**Resultado:** Se ha conseguido realizar el registro, pero no se ha obtenido una muestra de ofertas ni se ha comprobado el funcionamiento de la API.

#### Condiciones de uso

Se consultaron los términos de uso de la API:

https://developer.adzuna.com/docs/terms_of_service

También se consultó al proveedor por correo electrónico para aclarar las condiciones aplicables a un proyecto académico individual y no comercial.

En su respuesta, el proveedor confirmó los siguientes aspectos:

- Uso de la API con fines académicos.
- Almacenamiento local de los datos durante la duración del proyecto.
- Transformación de los datos y combinación con fuentes de referencia como ESCO.
- Publicación de resultados y ejemplos en el trabajo académico, siempre que se incluya la atribución correspondiente.
- Publicación del código fuente en GitHub, siempre que no se incluyan credenciales ni datos restringidos.

**Coste y disponibilidad:** El acceso inicial contempla 25 llamadas de prueba. Para disponer de acceso completo se ofrece un plan de pago de 8 £ mensuales.

**Redistribución y publicación de muestras:** No se ha obtenido una autorización específica suficientemente detallada para redistribuir ofertas completas o publicar muestras de datos en el repositorio. La confirmación sobre publicación de resultados y ejemplos está sujeta a las condiciones de atribución y a los términos aplicables.

**Decisión:** Aunque el proveedor confirmó varios usos académicos, se descarta esta fuente porque el acceso completo requiere una suscripción de pago y no se garantiza su disponibilidad gratuita durante todo el desarrollo del producto.

#### Protección y privacidad

No se ha descargado ni almacenado ninguna oferta de Adzuna para el proyecto.

#### Frecuencia y cobertura

No se ha obtenido una muestra de datos ni se han realizado consultas a la API, por lo que no se ha podido comprobar directamente la frecuencia de actualización de las ofertas ni la cobertura efectiva de los resultados.

#### Granularidad y variables

No se ha descargado ninguna muestra, por lo que no se ha podido inspeccionar la estructura real de los registros ni comprobar los tipos de datos, las unidades o los identificadores disponibles.

## Headcount Labs

## Feina Activa

## ECYL

## ESCO

# EDA

# Diagnóstico

# Decisiones de limpieza

# Resultados

# Conclusiones

