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