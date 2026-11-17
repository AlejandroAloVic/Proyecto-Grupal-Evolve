# Idea candidata

Recomendador de ofertas de empleo según el perfil profesional.

# Datos necesarios

# Fichas de fuentes

## Headcount Labs

## Feina Activa

## ECYL

## ESCO

### Origen y acceso.  

**Proveedor y responsable**: La fuente ESCO (European Skills, Competences, Qualifications and Occupations) es una clasificación europea desarrollada y mantenida por la Dirección General de Empleo, Asuntos Sociales e Inclusión (DG EMPL) de la Comisión Europea.

**Enlace de acceso**: https://esco.ec.europa.eu/en/use-esco/download 

**Método de obtención**: Descarga directa desde el portal oficial de ESCO. Se obtuvo el paquete de datos denominado ESCO dataset - v1.2.1 - classification - es - csv, correspondiente a la versión 1.2.1 de la clasificación, en español y en formato CSV. Se han usado solo tres ficheros: 

- `occupations_es.csv`: información sobre las ocupaciones. 
- `skills_es.csv`: información sobre las competencias y conocimientos. 
- `occupationSkillRelations_es.csv`: relaciones entre ocupaciones y competencias. 

**Fecha de acceso**: 9/11/2026. 

**Pasos y requisitos de acceso**: Se accedió al portal público de ESCO, se seleccionó la versión 1.2.1, el contenido correspondiente a la clasificación, el idioma español y el formato CSV. Posteriormente, se descargó el paquete y se extrajeron los ficheros. El acceso y la descarga son gratuitos y no requieren adquirir una licencia de pago. 

### Condiciones de uso.  
La clasificación ESCO puede descargarse, utilizarse, reproducirse y reutilizarse gratuitamente para cualquier finalidad, de acuerdo con la información publicada por la Comisión Europea y la Decisión 2011/833/UE sobre la reutilización de documentos de la Comisión. 
La Comisión establece dos condiciones principales: 

- Reconocer expresamente la fuente e indicar que se utiliza la clasificación ESCO de la Comisión Europea. 
- Identificar claramente cualquier versión modificada o adaptada de la clasificación. 

Por tanto, las condiciones permiten el uso de los datos en el proyecto, su transformación, la publicación de resultados y la redistribución de los datos reutilizados, siempre que se respeten las condiciones de atribución y se indique que se han realizado modificaciones. 

**Evidencia de las condiciones de uso**: https://esco.ec.europa.eu/en/use-esco 

### Protección y privacidad.  
La fuente no contiene datos personales. Por tanto, no se trata información sensible o confidencial procedente de esta fuente, y no resulta necesario aplicar medidas de anonimización.

Los ficheros originales y los datos procesados podrán compartirse en el repositorio del proyecto, respetando las condiciones de atribución de ESCO. 

### Frecuencia y cobertura.  
ESCO es una clasificación de referencia que se actualiza periódicamente para reflejar cambios en el mercado laboral y en el ámbito de la educación y la formación. Las actualizaciones pueden ser:

- Versiones principales: incorporan cambios importantes, como nuevas ocupaciones, competencias o modificaciones en la estructura de la clasificación. 
- Versiones menores: se centran principalmente en mejoras de calidad, correcciones de términos, relaciones y traducciones, sin incorporar necesariamente nuevos conceptos. 

La versión utilizada en el proyecto es la v1.2.1, publicada en diciembre de 2025. La versión anterior principal, v1.2.0, se publicó en mayo de 2024. La clasificación cubre el ámbito europeo y está disponible en 28 idiomas, incluidos los idiomas oficiales de la Unión Europea y otros idiomas adicionales. 

Como su finalidad es proporcionar una clasificación estructurada y relativamente estable, su frecuencia de actualización es adecuada. 

### Granularidad y variables. 

La fuente está organizada en tres conjuntos de datos con diferentes niveles de detalle:

- Ocupaciones (`occupations_es.csv`). Cada fila representa un concepto de ocupación. Entre sus variables principales se encuentran:
    - concept_uri: identificador URI de la ocupación.
    - preferred_label: denominación principal de la ocupación. 
    - alt_labels: denominaciones alternativas. 
    - description: descripción de la ocupación. 
    - isco_group: grupo ocupacional según la clasificación ISCO. 
    - regulated_profession_note: información sobre si se trata de una profesión regulada. 
    - code y nace_code: códigos relacionados con la clasificación ocupacional y las actividades económicas. 

- Competencias (`skills_es.csv`). Cada fila representa un concepto de competencia o conocimiento. Entre sus variables principales se encuentran: 
    - concept_uri: identificador URI de la competencia. 
    - preferred_label: denominación principal. 
    - alt_labels: denominaciones alternativas. 
    - description: descripción del concepto. 
    - skill_type: tipo de concepto. 
    - reuse_level: nivel de reutilización o ámbito de aplicación. 

- Relaciones entre ocupaciones y competencias (`occupationSkillRelations_es.csv`). Cada fila representa una relación entre una ocupación y una competencia. Sus variables principales son:
    - occupation_uri: URI de la ocupación relacionada. 
    - skill_uri: URI de la competencia relacionada. 
    - relation_type: indica si la competencia es esencial u opcional para la ocupación. 
    - occupation_label y skill_label: denominaciones asociadas a los conceptos. 

Las URI permiten relacionar los tres conjuntos de datos y mantener la integridad de las asociaciones.

# EDA

# Diagnóstico

# Decisiones de limpieza

# Resultados

# Conclusiones

