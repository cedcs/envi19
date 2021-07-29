# Procesos

Este documento tiene por objeto enunciar y describir cada una de las fases del algoritmo de procesos propuesto para cubrir la reproducción de la expresión textual contenida en una reprografía facsimilar digital a un reservorio digital que habrá de albergar ese corpus de manera que resulte apto para su análisis por medios digitales, reutilizable para otros fines y transformable para el futuro. Particularmente, este documento técnico contiene la secuencia del algorítimo de procesos propuesto para el Proyecto “Noticias del Viejo Imperio, 1860-1866”, mismo que le da marco, intención y cabida. Su redacción responde a la necesidad de explicar las fases del proceso general de transferencia textual que se requiere para el desarrollo de este proyecto, y se pretende con él responder a las necesidades del agente técnico, usuario o investigador que pretenda acercarse al mismo, no sólo para su utilización, como para su cabal comprensión.

Más allá de la definición que del término ‘algoritmo’ –tan en boga hoy día– nos pudiera dar la Real Academia Española de la Lengua, instrumentalizada mediante su *[Diccionario de la Lengua Española](http://lema.rae.es/drae/?val=algoritmo)*, emplearemos aquí la reelaboración de la misma, más concreta, menos ambigua, que propone el artículo de la [Wikipedia en español](https://es.wikipedia.org/wiki/Algoritmo): “un algoritmo […] es un conjunto prescrito de instrucciones o reglas bien definidas, ordenadas y finitas que permite realizar una actividad mediante pasos sucesivos que no generen dudas a quien deba realizar dicha actividad”. La necesidad de establecer un algoritmo que describa los procesos técnicos viene dada por que este mismo proceso establece, según Kozen (1992),

- una entrada –en este caso, el texto contenido en la reprografía documental– y una salida –aquí, el texto extendido, en formato `plaintext/markdown`– del sistema;
- una serie de pasos que constituyen una forma concreta de discretización –de secuenciación selectiva, si se quiere– del tiempo, lo que provoca que la producción de este algoritmo sea independiente de su reproducción; y
- una descripción concreta y físicamente acotada, sin que deje lugar a la ambigüedad, de las transiciones entre las fases, que es lo que se pretende en el presente conjunto de documentos técnicos.

Antes de la implementación de este proyecto, y dadas las antedichas premisas, hemos desarrollado una serie de documentos técnicos cuyo objetivo es el de permitir la consecución exitosa de nuestros objetivos. Durante la elaboración de estos documentos técnicos, hemos tenido siempre en mente la especificidad de los conceptos tratados, la ejemplificación de todos los casos comprendidos en las explicaciones, y la facilidad de uso por parte del usuario final. Estos documentos técnicos, elaborados a partir del conocimiento de diversos proyectos digitales –entre los que destacan *[Avisos de Levante](https://avisosdelevante.wordpress.com/)*,  la *[Biblioteca Digital del Pensamiento Novohispano](http://www.bdpn.unam.mx/)*, el *[Medici Archive Project](http://www.medici.org/)*, la plataforma *[Transcribe Bentham](http://blogs.ucl.ac.uk/transcribe-bentham/)* y el proyecto *[RELMIN](http://www.relmin.eu/index.php/en/)*– y de algunas recomendaciones y experiencias en la elaboración de proyectos digitales, son los siguientes:

- el presente documento técnico, nombrado *Secuencia del Algoritmo de Procesos*, que enuncia y describe cada una de las fases del algoritmo propuestas para cubrir la reproducción del texto contenido en un documento a un reservorio digital que habrá de albergar el corpus resultante;
- unas pautas de *Selección*, cuya finalidad es la de mostrar de forma transparente los procesos inherentes a los criterios búsqueda y selección de fuentes en la presente investigación histórica;
- unas reglas de *Catalogación*, que permiten la correcta implementación de un esquema de metadatos en cada uno de los productos finales del proyecto;
- unas reglas de *Transcripción* de tradición paleográfica latina, cuyo objeto es el de expresar las acciones a desarrollar en la transferencia del texto contenido en una reprografía facsimilar digital a un entorno textual digital en formato `plaintext/markdown`;
- unas reglas de *Edición*, que muestran los distintos procedimientos paralelos necesarios para completar la sistematización de la información textual digitalizada por transcripción mediante la aplicación, sobre los textos transcritos, primero, de la división discreta de la información en ellos contenida, y después, de la reestructuración de los fragmentos producidos en una estructura etiquetada en formato JSON para su almacenamiento, procesamiento, visualización y análisis; y
- unos lineamientos de *Publicación*, íntimamente vinculados a las antedichas reglas de *Catalogación*, que servirán a la disponibilización pública prolongada de los objetos fruto de este proyecto.

En el texto subsiguiente, producto de la reflexión y del empirismo en cuanto a su definición, podrá el lector –agente, usuario, investigador…– encontrar descripciones que, como indicara Cormen (*et al.*, 2009), pueden ser consideradas de alto nivel técnico, puesto que buscan establecer el problema, seleccionar el modelo o estándar a seguir y explicar el algoritmo de manera verbal, vienen acompañadas de descripciones formales en las que se usan formas codificadas de lenguaje técnico con la intención de describir la secuencia de pasos necesaria para obtener el resultado pretendido, y en muchos casos una ejemplificación de su implementación.

### 1. Selección

La primera fase técnica será la de *Selección*, que se aplicará sobre las fuentes para designar el origen y el orden de su inclusión dentro del sistema. La incorporación discrecional de elementos reprográficos siempre estará sujeta al dictamen de los responsables del proyecto, quienes serán en todo momento responsables también del propio reservorio digital.

Se ha determinado, a partir de un minucioso examen de la documentación preservada en distintos acervos, una tipología de documentos relevantes para su inclusión en este proyecto. En esta primera etapa de desarrollo del proyecto, nos ceñiremos únicamente a periódicos, revistas, diarios de sesiones, imágenes y libros. La selección de estos obligará a que sean sometidos a registro y almacenamiento, y deberán para su selección contener información que haga referencia directa a la Escuadra del Pacífico, la expedición de la misma y la posterior Guerra Hispanosudamericana, todo ello en una cronología que vaya de 1862 a 1866, dejando para una etapa de revisión de la selección posterior el período 1860-1862. Se podrán, asímismo, registrar y almacenar fuentes cuyo contenido haga referencia a la política exterior y americana de la Monarquía española.

Como objeto técnico producto de esta fase obtendremos una reprografía de cada documento que se haya seleccionado de su acervo original, que será sobre la que se apliquen las acciones técnicas de la siguiente fase.

### 2. Catalogación

Dentro del algoritmo de procesos del presente proyecto se producen tres objetos técnicos concretos: una *reprografía* *facsimilar digital* proporcionada por diversas instituciones de resguardo y/o digitalización de fondos, un *archivo de texto plano* con la transcripción del texto en formato Markdown y un *archivo JSON* que contiene el texto segmentado, serializado y semantizado. Todos ellos integrarán *metadatos*, aunque desde este proyecto dichos metadatos sólo se integrarán en dos de ellos. 

La labor de *catalogación por metadatos* de los objetos técnicos concretos producto de la transcripción textual se realiza, en este proyecto, en dos momentos diferenciados dentro del algoritmo de procesos, puesto que son dos los productos finales de esta técnica. Un primer momento corresponde a la segunda fase de dicho algoritmo, propiamente de *Catalogación*, mientras que el segundo momento de catalogación por metadatos se produce en la quinta fase, de *Edición*, según se especifica en el antedicho documento. 

Se aplican, mediante el etiquetado de metadatos dentro de los archivos de texto plano de la fase de Transcripción, tres conjuntos de metatados –Archivo, Versión y Publicación– que servirán como base para la elaboración de los cinco conjuntos de metadatos –Archivo, Estructura, Relación, Versión y Publicación– durante la fase de *Edición*.

En esta fase, por tanto, no se producen objetos técnicos concretos que puedan servir por sí mismos, sino partes de otros objetos técnicos: durante su aplicación en la fase de *Transcripción* se completan los objetos técnicos fruto de dicha fase con los metadatos necesarios, y lo mismo sucede en la fase de *Edición* con sus objetos técnicos finales.

### 3. Transcripción

La tercera fase será la de *Transcripción*, en la que se llevará a cabo la creación de un archivo de texto plano en formato Markdown a partir de la información que se capture digitalmente del texto contenido en el facsímil digital, bajo ciertas normas de transcripción ya establecidas. Dichas normas han sido elaboradas con base en una tradición latina de paleografía. Parece necesario hacer notar al usuario que al hablar de códigos de caracteres no estamos haciendo referencia a idiomas o lenguas concretas, sino a los esquemas generales de expresión escrita de las mismas, dentro de los condicionantes del ambiente digital en el que se pretende desarrollar el proyecto.

Esta fase debe incluir también las notas de transcripción, que reflejan información editorial sobre la elaboración del texto –paginación o foliación, firmas ilegibles y errores del escribano, daños y falencias del documento, etcétera– contenida tanto en el documento preservado en el acervo de origen, como en la reprografía y en el facsímil digital en forma de contenido textual o textualizable, pero que se considera de valor para la investigación histórica.

Esta fase es una de las más complejas del algoritmo de procesos, y requiere por tanto de capacitación especial, dado que el objeto técnico fruto de la misma –el archivo `plaintext/markdown`– es ya un objeto sobre el cual se pueden realizar investigaciones históricas con herramientas digitales.

### 4. Edición

### 5. Publicación

# *Referencia*

El presente documento, ***Procesos del Proyecto “Noticias del Viejo Imperio, 1860-1866”***, creado por David Domínguez Herbón y Álvaro Casillas Pérez, es una versión del documento *[Secuencia del Algoritmo de Procesos del Proyecto “Avisos de Levante”](http://avisosdelevante.net/proyecto_esp/algoritmo/)*, creado por David Domínguez Herbón, Ricardo Fabián Chimal Avalos y Gennaro Varriale; es una publicación respaldada por el [Centro de Estudios Americanos](https://artesliberales.uai.cl/centros/centro-de-estudios-americanos/) y la [Facultad de Artes Liberales](https://artesliberales.uai.cl/) de la Universidad Adolfo Ibáñez, el [Instituto Universitario de Investigación en Estudios Latinoamericanos](https://ielat.com/) de la Universidad de Alcalá y el [Centro Europeo para la Difusión de las Ciencias Sociales](http://www.archivodelafrontera.com/), instituciones bajo cuyo auspicio se publica.

Todos los objetos digitales en esta web se publican en el marco del [Proyecto Fondecyt de Iniciación Nº 112000245](https://s3.amazonaws.com/documentos.anid.cl/iniciacion/2020/fallo/NominaProyectosAprobadosIniciacion2020.pdf) “Noticias del Viejo Imperio. La Expedición del Pacífico y la Guerra hispano-sudamericana en los imaginarios geopolíticos de la España liberal (1860-1866)”, financiado por la [Agencia Nacional de Investigación y Desarrollo](https://www.anid.cl/), del [Ministerio de Ciencia, Tecnología, Conocimiento e Innovación](http://www.minciencia.gob.cl), del Gobierno de Chile.

Este proyecto se adhiere a la [Budapest Open Access Initiative](https://www.budapestopenaccessinitiative.org/boai-10-translations/spanish). Todos los objetos digitales de este proyecto se distribuyen bajo una [Licencia Creative Commons *Zero* 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/deed.es).

*Correo webmaster [admin@envi19.cl](mailto:admin@envi19.cl)* · *Versión 1.0  ·  Fecha de creación: 02 de marzo de 2021  ·  Última actualización: 20 de junio de 2021*