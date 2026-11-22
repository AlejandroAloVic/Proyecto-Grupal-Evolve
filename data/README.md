# Datos del proyecto 

## Fuente ESCO 

**ESCO (European Skills, Competences, Qualifications and Occupations)** es una clasificación europea de ocupaciones, competencias, conocimientos y cualificaciones desarrollada por la Comisión Europea.

### Obtención de los datos originales 

Para obtener los datos necesarios: 

1. Acceder al portal de descargas de ESCO: https://esco.ec.europa.eu/en/use-esco/download 
2. Seleccionar la versión 1.2.1 de la clasificación, en contenido clasificación, tipo de archivo CSV e idioma español (es). 
3. Rellenar un formulario con el correo, el tipo de organización que solicita y el uso que se pretende. 
4. Al correo indicado llega un mensaje con el enlace de descarga. 
5. Descargar y extraer los ficheros. 

Los ficheros necesarios son: 
- `occupations_es.csv` 
- `skills_es.csv` 
- `occupationSkillRelations_es.csv` 

### Descripción de los conjuntos de datos 

#### Ocupaciones (`occupations_es.csv`)

Cada registro representa una ocupación de la clasificación ESCO. Variables principales: 

| Variable | Descripción | 
|---|---| 
| `concept_uri` | Identificador URI único de la ocupación. | 
| `preferred_label` | Denominación principal de la ocupación. | 
| `alt_labels` | Denominaciones alternativas de la ocupación. | 
| `description` | Descripción de la ocupación. | 
| `isco_group` | Grupo ocupacional según la clasificación ISCO. | 
| `regulated_profession_note` | Información sobre la regulación de la profesión. | 
| `code` | Código asociado a la ocupación. | 
| `nace_code` | Código o códigos de actividades económicas relacionados. | 
| `in_scheme` | Esquema de clasificación al que pertenece el concepto. | 

#### Habilidades (`skills_es.csv`) 

Cada registro representa una competencia o conocimiento de la clasificación ESCO. Variables principales: 

| Variable | Descripción | 
|---|---| 
| `concept_uri` | Identificador URI único de la competencia. | 
| `preferred_label` | Denominación principal de la competencia. | 
| `alt_labels` | Denominaciones alternativas. | 
| `description` | Descripción de la competencia. | 
| `skill_type` | Tipo de concepto: competencia o conocimiento. | 
| `reuse_level` | Nivel de reutilización o ámbito de aplicación de la competencia. | 
| `in_scheme` | Esquema de clasificación al que pertenece el concepto. | 

#### Relaciones entre ocupaciones y habilidades (`occupationSkillRelations_es.csv`) 

Cada registro representa una relación entre una ocupación y una competencia. Variables principales: 

| Variable | Descripción | 
|---|---| 
| `occupation_uri` | URI de la ocupación relacionada. | 
| `occupation_label` | Denominación de la ocupación. | 
| `relation_type` | Tipo de relación: esencial u opcional. | 
| `skill_type` | Tipo de competencia relacionada. | 
| `skill_uri` | URI de la competencia relacionada. | 
| `skill_label` | Denominación de la competencia. | 

Las variables `occupation_uri` y `skill_uri` permiten relacionar este conjunto de datos con los conjuntos de ocupaciones y competencias, respectivamente. 

### Proceso de limpieza y generación de los datos 

El proceso de limpieza se encuentra documentado en el notebook: `notebooks/01_analisis_esco.ipynb`. Para generar los ficheros limpios: 

1. Descargar y colocar los tres ficheros originales en `data/raw/esco/`. 
2. Abrir el notebook `01_analisis_esco.ipynb`. 
3. Ejecutar las celdas en orden, desde la carga de los datos originales hasta el guardado de los resultados. 
4. Los ficheros procesados se guardarán en `data/silver/esco/`. 

### Atribución de la fuente 

Esta publicación utiliza la clasificación ESCO de la Comisión Europea (**This publication uses the ESCO classification of the European Commission**).

Los datos almacenados en `data/silver/` constituyen una versión procesada y modificada de los datos originales de ESCO, mediante operaciones de limpieza y transformación realizadas en el marco de este proyecto.

Los datos originales se conservan sin modificaciones en `data/raw/`.

## Fuente Feina Activa

**Feina Activa** es el portal de empleo del **Servei d'Ocupació de Catalunya (SOC)** / **Generalitat de Catalunya** (`feinaactiva.gencat.cat`), del que se obtienen ofertas de empleo y vacantes laborales en formato XML.

### Obtención de los datos originales

Para obtener los datos necesarios:

1. Acceder al portal de empleo **Feina Activa** (`https://feinaactiva.gencat.cat/`) o consultar el conjunto de datos de ofertas de empleo en los portales de datos abiertos vinculados a la Generalitat de Catalunya / `datos.gob.es`, según la vía de acceso o feed XML habilitado para la extracción.
2. Obtener o exportar el fichero XML de ofertas de empleo correspondiente a la consulta o lote de extracción.
3. Colocar el fichero XML original en `data/raw/feina_activa/` (junto con su registro de extracción `metadata_extraccion.json` si se ha generado durante la ingesta).
4. Verificar que los ficheros originales en `data/raw/feina_activa/` se conservan sin modificar como copia bruta de referencia.

### Descripción de los conjuntos de datos

#### Ofertas de empleo (`offers_feina_activa_silver.csv`)

Cada registro representa una oferta de empleo publicada en el lote analizado (`4.890` registros y `19` columnas estandarizadas en la capa Silver). Variables principales:

| Variable | Descripción |
|---|---|
| `id` | Identificador único de la oferta. |
| `url` | Enlace a la publicación original de la oferta. |
| `title` | Título o puesto anunciado en la oferta. |
| `content` | Descripción detallada de las funciones y condiciones del puesto. |
| `company` | Nombre de la empresa o entidad empleadora. |
| `experience` | Experiencia requerida o valorada para el puesto. |
| `requirements` | Requisitos específicos solicitados en la oferta. |
| `studies` | Nivel de estudios o formación requerida. |
| `contract` | Tipo de contrato ofertado. |
| `working_hours` | Tipo de jornada laboral. |
| `date` | Fecha de la oferta (`datetime64[us]`). |
| `salary_min` | Salario mínimo indicado (`Float64`). |
| `salary_max` | Salario máximo indicado (`Float64`). |
| `city` | Municipio o localidad de la oferta. |
| `region` | Provincia o región de la oferta. |
| `disability` | Información relativa a discapacidad en el puesto. |
| `postcode` | Código postal (`string`, preservando ceros a la izquierda). |
| `status` | Estado de la oferta en el origen. |
| `origin` | Origen dentro del XML (`FA` o `SICAS`). |

### Proceso de limpieza y generación de los datos

El proceso de limpieza y validación se encuentra documentado en el notebook: `notebooks/01_limpieza_faina.ipynb`. Para generar el fichero limpio:

1. Colocar el fichero XML original en `data/raw/feina_activa/`.
2. Abrir el notebook `01_limpieza_faina.ipynb`.
3. Ejecutar las celdas en orden, desde la carga y exploración inicial hasta la validación y exportación de resultados.
4. El fichero procesado se guardará en `data/silver/feina_activa/offers_feina_activa_silver.csv`.

### Atribución y trazabilidad de los datos

Este proyecto utiliza información procedente del portal de empleo **Feina Activa** (**Servei d'Ocupació de Catalunya / Generalitat de Catalunya**).

El fichero almacenado en `data/silver/feina_activa/offers_feina_activa_silver.csv` constituye una versión procesada y estandarizada de los datos originales mediante operaciones de limpieza, tipado y validación realizadas en este proyecto, conservando los nulos reales y sin alteraciones destructivas en Silver.

Los datos originales se conservan sin modificaciones en `data/raw/feina_activa/`.S

### Fuente ECYL

**ECYL (Portal de Empleo de Castilla y León)** Es el servicio público de empleo de Castilla y León. Un organismo autónomo encargado de las actividades de fomento del empleo, la formación para el empleo y la orientación e intermediación en el mercado de trabajo de la comunidad de Castilla y León, adscrito a la Consejería competente en materia laboral, en la actualidad la Consejería de Industria, Comercio y Empleo.

### Obtención de los datos originales

Para obtener los datos necesarios:
1. Acceder al portal de análisis de datos abiertos de Castilla y León (https://datosabiertos.jcyl.es/web/es/analisis-datos-abiertos.html). Acceder al buscador de datos para poder buscar el dataset de empleo. Buscar el dataset de ofertas de empleo. Pinchar en el enlace de la descripción.
Este caso tiene varias opciones para obtener los datos:
*Caso 1: Exportar los datos*
2. Pulsar en el botón de exportar los datos.
3. Descargar los datos en el formato que queramos usar: CSV, Excel o JSON.
4. Guaradrlos en "data/raw/ECYL/".
*Caso 2: Mediante API*

