# Idea candidata

Recomendador de ofertas de empleo según el perfil profesional.

# Datos necesarios

## Datos necesarios - Headcount Labs 

## Datos necesarios - Feina Activa

Para el recomendador de ofertas de empleo según el perfil profesional, **Feina Activa** aporta el catálogo de vacantes reales sobre el que contrastar perfiles, puestos y condiciones del mercado laboral.

* **Información ya obtenida:** muestra real de `4.890` ofertas (`19` columnas estandarizadas en `offers_feina_activa_silver.csv`), con identificador (`id`), enlace (`url`), puesto y descripción (`title`, `content`), empresa (`company`), experiencia/requisitos/estudios (`experience`, `requirements`, `studies`), condiciones laborales y salariales (`contract`, `working_hours`, `date`, `salary_min`, `salary_max`), ubicación y discapacidad (`city`, `region`, `postcode`, `disability`) y trazabilidad (`status`, `origin`).
* **Relación con el uso previsto:** `title` y `content` permiten entender el rol y las tareas del puesto; `experience`, `requirements` y `studies` orientan el encaje con el perfil del candidato; `contract`, `working_hours`, `salary_min`, `salary_max`, `city`, `region` y `postcode` permiten filtrar o priorizar ofertas según preferencias y ubicación.
* **Datos o pasos aún pendientes:** vincular estas ofertas con las ocupaciones y competencias normalizadas de **ESCO** (y con los datos que aporten las demás fuentes del equipo cuando estén listos), además de aplicar reglas de negocio o enriquecimiento en fases posteriores / capa Gold.

**Evidencias y código de Feina Activa:**
* Notebook de limpieza: `notebooks/01_limpieza_faina.ipynb`
* Salida en capa Silver: `data/silver/feina_activa/offers_feina_activa_silver.csv`

## Datos necesarios - ECYL

## Datos necesarios - ESCO

# Fichas de fuentes

## Headcount Labs

## Feina Activa

### Origen y acceso.

**Proveedor y responsable**: Feina Activa es el portal de empleo público gestionado por el Servei d'Ocupació de Catalunya (SOC) / Generalitat de Catalunya.

**Enlace de acceso**: https://feinaactiva.gencat.cat/

**Método de obtención**: Obtención del feed XML de ofertas de empleo de Feina Activa y almacenamiento de la muestra original en `data/raw/feina_activa/` (junto con su registro de extracción `metadata_extraccion.json` si procede).

**Fecha de acceso**: Pendiente de fijar exactamente la fecha de descarga del lote en este documento (las fechas registradas en las ofertas del lote abarcan del `21/08/2026` al `19/11/2026`).

**Pasos y requisitos de acceso**: Se accede al portal/feed de Feina Activa o a los canales de difusión habilitados, se obtiene el fichero XML con las ofertas y se guarda sin modificar en `data/raw/feina_activa/`. El acceso al catálogo público de ofertas no requiere compra de licencia comercial, aunque conviene revisar las condiciones específicas del canal o feed utilizado antes de redistribuir ficheros.

### Condiciones de uso.

Las ofertas de empleo de Feina Activa proceden de un servicio público del SOC / Generalitat de Catalunya, pero en esta fase conviene verificar expresamente las condiciones y avisos legales concretos aplicables al feed o descarga utilizada (incluyendo si permiten libremente la transformación, redistribución o publicación de ficheros brutos en un repositorio público).

En la capa Silver del proyecto se emplean para fines académicos y de análisis dentro del desarrollo del recomendador de ofertas según perfil profesional, conservando la trazabilidad hacia la fuente original. Si las condiciones del feed o la publicación de muestras en GitHub presentan dudas o restricciones, se priorizará el uso analítico interno del equipo, la documentación reproducible del pipeline y la publicación de agregados/resúmenes frente a la redistribución abierta de datos brutos sin confirmar.

**Evidencia de las condiciones de uso**: https://feinaactiva.gencat.cat/ (pendiente de enlazar el aviso legal o condiciones específicas del feed/catálogo correspondiente).

### Protección y privacidad.

El conjunto de ofertas de empleo está orientado a vacantes laborales (`4.890` registros en el lote analizado) y no pretende recoger datos personales de candidatos. No obstante, en campos de texto libre como `content`, `requirements` o `company` podrían aparecer eventualmente referencias de contacto, nombres propios o datos de terceros según cómo se haya redactado la oferta.

Como medidas preventivas, se trabaja únicamente con los campos necesarios de la oferta, no se incorporan datos personales de usuarios/candidatos, se excluyen del control de versiones archivos sensibles, credenciales o ficheros que no proceda publicar mediante `.gitignore`, y se revisa el contenido antes de compartir muestras públicas en el repositorio.

### Frecuencia y cobertura.

Las ofertas de empleo se publican y actualizan de forma continua en la plataforma a medida que se gestionan vacantes y se incorporan ofertas (incluyendo registros con distintos orígenes internos como `FA` o `SICAS`). En el lote analizado se registran fechas entre el `2026-08-21` y el `2026-11-19`, con cobertura centrada principalmente en el ámbito territorial de Cataluña (con presencia destacada de municipios y códigos postales de la provincia de Barcelona y del entorno del SOC).

Puede existir un desfase entre el momento en que se genera o modifica una vacante y la fecha o extracción del lote XML. Para el proyecto, la disponibilidad periódica de ofertas activas resulta útil para contrastar demandas reales del mercado laboral, teniendo en cuenta que cada extracción captura una fotografía temporal de las ofertas presentes en ese momento.

### Granularidad y variables.

Cada fila representa una oferta de empleo individual (`4.890` registros iniciales y finales tras la limpieza hacia Silver, con `19` columnas estandarizadas en `snake_case` tras eliminar `category` por estar al `100 %` vacía). Entre sus variables principales se encuentran:

- `id`: identificador único de la oferta en el conjunto.
- `url`: enlace a la oferta original.
- `title` y `content`: título del puesto y descripción detallada de funciones y condiciones.
- `company`: entidad o empresa empleadora.
- `experience`, `requirements` y `studies`: experiencia, requisitos y formación indicados en la oferta.
- `contract` y `working_hours`: tipo de contrato y jornada laboral.
- `date`: fecha asociada a la oferta (`datetime64[us]`).
- `salary_min` y `salary_max`: límites salariales mínimo y máximo (`Float64`).
- `city`, `region` y `postcode`: localidad, región/provincia y código postal (`string`, conservando ceros a la izquierda).
- `disability`, `status` y `origin`: indicador de discapacidad, estado y origen (`FA` o `SICAS`).

Al combinar Feina Activa (ofertas concretas por puesto y ubicación) con ESCO (clasificación jerárquica de ocupaciones y competencias), los niveles de detalle no son idénticos de entrada: Feina Activa aporta vacantes reales en texto/campos de oferta, mientras que ESCO aporta conceptos normalizados y relaciones ocupación-competencia, por lo que su vinculación requiere mapeo o correspondencia en fases posteriores del proyecto.

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

## EDA - Headcount Labs

## EDA - Feina Activa

Se ha explorado el conjunto de datos de ofertas de empleo de Feina Activa cargado desde el origen hacia la capa Silver, compuesto por `4.890` registros (`0` IDs duplicados y `0` filas duplicadas exactas) y fechas registradas entre `2026-08-21` y `2026-11-19`.

* **Cobertura y valores ausentes:** variables como `id`, `url`, `title`, `content`, `contract`, `working_hours`, `date`, `region`, `disability`, `status` y `origin` presentan `0` nulos. En cambio, otros campos muestran ausencias en distinta medida: `city` (`2` nulos), `postcode` (`3` nulos), `company` (`23` nulos), `experience` (`366` nulos), `salary_max` (`1.160` nulos), `salary_min` (`1.173` nulos), `requirements` (`1.601` nulos) y `studies` (`4.090` nulos).
* **Formatos, rangos y tipos:** se revisaron rangos salariales (`0` casos con mínimo mayor que máximo), cadenas de texto con saltos de línea o espacios adicionales, códigos postales con ceros a la izquierda (`postcode`), fechas (`date`) y nombres de columna en formato heterogéneo.

## EDA - ECYL

## EDA - ESCO

# Diagnóstico

## Diagnóstico - Headcount Labs

## Diagnóstico - Feina Activa

El diagnóstico distingue entre problemas técnicos de formato/estructura que conviene normalizar y ausencias reales o variabilidad propia del origen que no deben forzarse en la capa Silver:

* **Columna vacía en el lote:** `category` aparecía sin información (`100 %` vacía) en la muestra analizada, por lo que no aporta datos útiles en esta fase.
* **Nomenclatura y tipado:** los nombres de columna mezclaban estilos (*camelCase* y minúsculas) y variables como `date`, `salary_min`, `salary_max` y `postcode` requerían tipos explícitos (`datetime64[us]`, `Float64` y `string` respectivamente).
* **Textos, idioma y nulos reales:** los campos de texto libre (como `title`, `content` o `requirements`) pueden aparecer en catalán —o combinar catalán y castellano— por el origen de la fuente, y presentan saltos de línea o espacios sobrantes (especialmente en `content`) como ruido de formato; por su parte, los vacíos en `studies`, `requirements`, `salary_min`, `salary_max` o `experience` reflejan que la oferta no informó ese dato en origen (no son errores de carga ni valores imposibles).

## Diagnóstico - ECYL

## Diagnóstico - ESCO

# Decisiones de limpieza

## Decisiones de limpieza - Headcount Labs

## Decisiones de limpieza - Feina Activa

Las transformaciones aplicadas en `notebooks/01_limpieza_faina.ipynb` responden a los problemas diagnosticados y preservan la fidelidad de los datos en Silver:

* **Eliminación de columna sin información:** se retiró `category` al no contener valores útiles en este lote.
* **Estandarización de columnas y tipos:** se unificaron los nombres en `snake_case` y se tiparon las variables (`datetime64[us]` en `date`, `Float64` en `salary_min` y `salary_max`, y `string` en textos y `postcode` para conservar ceros iniciales).
* **Limpieza de texto sin normalización destructiva:** se limpiaron saltos de línea y espacios sobrantes en textos (como `content`), manteniendo los nulos reales y conservando el idioma original (incluido el catalán) sin traducir, imputar valores artificiales ni reescribir textos a lo bruto en Silver.

## Decisiones de limpieza - ECYL

## Decisiones de limpieza - ESCO

# Resultados

## Resultados - Headcount Labs

## Resultados - Feina Activa

El proceso de limpieza y validación en `notebooks/01_limpieza_faina.ipynb` generó el fichero `data/silver/feina_activa/offers_feina_activa_silver.csv` con `4.890` registros (`0` IDs duplicados, `0` filas duplicadas exactas y `0` rangos salariales invertidos) y `19` columnas estandarizadas en `snake_case`.

* **Comparación antes y después:** se conserva el volumen de `4.890` filas, se pasa de `20` columnas iniciales a `19` columnas finales al eliminar `category` (vacía al `100 %`), se normalizan textos con saltos de línea/espacios sobrantes (especialmente en `content`) y se fijan los tipos finales (`datetime64[us]` en `date`, `Float64` en `salary_min` y `salary_max`, y `string` en textos y `postcode`).
* **Problemas pendientes o reservados:** se mantienen intactos los nulos reales de origen (`studies` con `4.090`, `requirements` con `1.601`, `salary_min` con `1.173`, `salary_max` con `1.160`, `experience` con `366`, `company` con `23`, `postcode` con `3` y `city` con `2`), así como la variabilidad de redacción o idioma (incluido el catalán) en textos libres, para tratarlos en fases posteriores o en la capa Gold.

## Resultados - ECYL

## Resultados - ESCO

# Conclusiones

## Conclusiones - Headcount Labs

## Conclusiones - Feina Activa

Los datos de Feina Activa en la capa Silver son útiles para el recomendador de ofertas según perfil profesional, ya que ofrecen vacantes reales con fechas entre `2026-08-21` y `2026-11-19`, descripción del puesto, condiciones laborales y ubicación.

* **Información que falta y limitaciones:** falta vincular las ofertas con la taxonomía ESCO y con el resto de fuentes del equipo, y conviene tener en cuenta la alta ausencia de datos en campos como `studies` o salarios, las diferencias de formato y la presencia de textos en catalán (y combinaciones con castellano) en campos libres —relevantes para el encaje con el perfil y el cruce con ESCO— y el contexto de jornada o contrato al leer importes salariales.
* **Viabilidad y ajustes:** la muestra resulta viable para continuar hacia las siguientes fases del proyecto (cruce con ESCO y trabajo posterior en SQL / capa Gold), condicionado a verificar expresamente las condiciones legales de reutilización/publicación del feed utilizado y a ajustar el alcance o las fuentes si alguna restricción o el avance de las demás fuentes así lo aconseja.

## Conclusiones - ECYL

## Conclusiones - ESCO
