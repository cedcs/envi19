# Edición

Este documento técnico, elaborado en el marco del Proyecto “Noticias del Viejo Imperio, 1860-1866”, tiene por objeto facilitar al usuario la labor de edición de la información textual transcrita en la anterior fase, desarrollando en paralelo las actividades de segmentación, serialización y semantización correspondientes a la edición digital de los textos a publicar. Se corresponde con la cuarta fase, denominada de *Edición*, como se puede extraer del documento técnico *Algoritmo de procesos*.

Si en la fase anterior, de *Transcripción*, se produjeron documentos digitales en formato `plaintext/markdown` que incluían, tanto la transcripción de la documentación propiamente dicha, como una estructura primaria de metadatos, en esta penúltima fase se transformarán aquellos documentos –algunos en solitario, otros en conjunto…– en documentos digitales en formato `application/json` , sujeta a la [RFC 4627](https://www.rfc-editor.org/info/rfc4627), que permitirán aprovechar mejor las ventajas de los entornos digitales para su visualización, publicación y reutilización.

La elección de este formato, basado en el lenguaje JSON –las siglas en inglés de *JavaScript Object Notation*–, se debe a muchas razones. No es una de ellas su difusión en el ámbito de los proyectos de edición digital, en los que, si bien desde 2015 a la fecha se ha incrementado su utilización, siempre ha sido como lenguaje de intercambio de datos, de extracción de información o de gestión con otros sistemas, desechando sus posibilidades para el etiquetado de textos en favor del más extendido TEI-XML. Después de una investigación bastante intensa, y del establecimiento de una comparación entre las virtudes y defectos de ambos sistemas, nos decantamos por JSON en detrimento de TEI por diversas razones, que a continuación se muestran:

1. En cuanto a los procesos internos a nuestro proyecto, y en especial en lo tocante a esta fase de *Edición*, mediante el empleo de una estructura general en formato JSON, las acciones a realizar sobre los datos –segmentación, serialización y semantización– podrán ser realizadas simultáneamente antes de preparar la publicación final, dejando un sólo archivo útil, y no nos será necesario dividirlas en subfases o etapas menores, repitiendo la revisión tres veces, como hubiéramos tenido que realizar de usar XML-TEI, en base a la experiencia de proyectos pasados, como lo fueron *[Avisos de Levante](https://avisosdelevante.wordpress.com)* y la *[Biblioteca Digital del Pensamiento Novohispano](http://www.bdpn.unam.mx/)*.
2. Tomando como base la multitud de razones presentadas por Desmond Schmidt en su epílogo al libro *Per una critica del testo digitale. Letteratura, filologia e rete* (Roma, Bulzoni, 2018, pp. 181-199), de la autoría de Domenico Fiormonte, y a lo por este último expresado en el capítulo de la misma obra titulado “Filologia digitale ed edizione dei testi” (pp. 157-174), pudimos establecer sin dejar lugar a dudas que, si TEI está en declive y JSON está en alza, debíamos apostar por un nuevo sistema cuyas características, además de no ser en punto alguno menores a las de TEI, tienen la ventaja de su juventud y de haber sido establecidas, no como aquel pseudo-estándar por extensión, sino como un estándar oficial expresado en la [RFC 8259](https://www.rfc-editor.org/info/rfc8259) del IETF.
3. La selección previa de ciertas formas de visualización de los objetos finales, como eran su organización en narrativas guiadas por cartografía ([*Storymaps.JS*](https://storymap.knightlab.com/)), en colecciones de textos periodísticos ordenados cronológicamente ([*Timeline.JS*](http://timeline.knightlab.com/)), en grafos elaborados a partir del etiquetado de transcripciones de debates políticos (*[Cytoscape.JS](https://js.cytoscape.org/)*), nos forzó, dado que dichas herramientas emplean JSON como lenguaje para la introducción de datos, a utilizarlo con estos fines. Por supuesto, son muchas más las opciones de visualización directa de la información textual editada en JSON que para aquella etiquetada con TEI-XML, de modo que la ventaja es evidente. Por otra parte, no existe a la fecha –al menos, hasta donde pudimos saber– una herramienta de visualización de ediciones críticas digitales que sea funcional mediante JSON, lo que conllevó que, a partir de las dos primeras antedichas, de código abierto y producto del [Knight Lab](https://knightlab.northwestern.edu) de la Northwestern University, pudiéramos desarrollar un software propio para la presentación de ediciones críticas digitales ([*Envi.JS*](https://envi19.cl/envi-software/)) que se ofreciera bajo los mismos parámetros que cualquier otro producto del presente proyecto –*vid infra*–.
4. Si bien el nivel de legibilidad de un texto expresado en XML-TEI es muy alto, y si bien el procesamiento de datos en dicho sistema no es lento y sus posibilidades de transformación a otros lenguajes están muy desarrolladas, no son mayores –ni siquiera iguales– a las que ofrece JSON, cuya legibilidad es absoluta, aun con menores reglas y sin la constricción del anidamiento de etiquetas –sustituidas por elementos–, con un nivel de procesamiento de datos casi equivalente al de su homólogo binario CBOR y un muy alto nivel de transformabilidad y conversión, lo que fomenta la durabilidad –aun mediando conversión– de los objetos digitales desarrollados con este lenguaje.

Por supuesto, existieron más razones para su elección, y a pesar de que todas ellas excedían los límites de este proyecto, y de que las que sí nos afectaban directamente eran más que suficientes para tomar una decisión orientada a JSON, tuvieron un peso específico más que razonable en dicha elección: la posibilidad de combinar etiquetados sin que el anidamiento estorbase, o de presentar simultáneamente o en paralelo distintas variantes de un texto; el desarrollo de software que precisábamos, que no fue nunca –hasta que fue inevitable– ni una necesidad ni un planteamiento del proyecto; la posibilidad de instalarlo todo fácil y rápidamente en un servicio `git` gratuito, o de modificarlo a conveniencia para otros proyectos; el hecho de que habíamos pasado del formato *document oriented* desarrollado en proyectos anteriores a un esquema *corpus oriented* con varias colecciones coexistiendo en distintas visualizaciones… Todas estas fueron razones que, si bien no tendrían por qué haber nacido del proyecto, lo hicieron más fuerte y nos convencieron de que optar por JSON era, no ya lo menos doloso, sino lo más benéfico para este proyecto y para los que vinieran después.

Una de las razones antedichas es la coexistencia de varias colecciones, o *corpora*, dentro del mismo proyecto. Efectivamente, tal y como se explicaba en el documento técnico relativo a la fase de *Selección*, varias series documentales, bibliográficas y hemerográficas han sido seleccionadas, y sus reprografías digitales facsimilares obtenidas, para su digitalización en el presente proyecto. Dado que, como va de suso dicho, este proyecto se autodefine como *visualization driven*, elegir el software implica someterse, en cierta forma, a las constricciones que establezcan sus especificaciones técnicas. En este caso, se eligieron dos herramientas narrativas del Knightlab, antes mencionadas, para tres de los *corpora* de este proyecto, y una más, *[Cytoscape.JS](https://js.cytoscape.org/)*, para el último corpus, mientras que las ediciones digitales documentales requerirían, por sí mismas, de una herramienta independiente, la desarrollada en el seno de este proyecto.

Por tanto, se han definido, a partir de las necesidades del presente proyecto, cuatro estructuras generales de datos en JSON, una de ellas particular para cada documento integrado en el sistema, y otras tres, una por cada forma de serialización establecida. En cuanto a estas, fueron establecidas en función de la forma de los distintos corpus definidos a partir de la realización de la fase de *Selección*. A partir de esta selección, se encontró que la mayor parte de la documentación respondía a los siguientes rubros: diarios y narraciones de viaje, artículos de opinión en la prensa política, correspondencia diplomática y de gobierno, y debates legales y políticos en las Cortes.

A continuación se mostrarán las cuatro estructuras de datos elaboradas en el presente proyecto, con las especificaciones necesarias en función de la integración dentro de una superestructura más general y común a todas ellas, ya descrita en la segunda subfase de la fase de *Catalogación*.

# Clase I. Edición Digital Documental

*… [en proceso]*

# Clase II. Serialización Cartográfica Documental

Los diarios y narraciones de viaje, como se podrá deducir de sus propias expresiones, tienen una motivación y estructura eminentemente cartografiable, de manera que la visualización de sus ediciones resulta ser más funcional si representada tanto en textos fragmentados como en un mapa. Dado que JSON es, desde su propia definición, un lenguaje de serialización de datos, sirve a estos fines a la perfección. De entre el software que mejor permitiría dicho esquema de visualización de forma óptima, se eligió [*Storymap.JS*](https://storymap.knightlab.com/), que ofrece ya una forma de serialización muy adaptable a la estructura prevista por las ediciones digitales de los documentos particulares.

Siguiendo lo establecido por la propuesta informativa sobre la elaboración de meta-esquemas para el lenguaje de serialización JSON producida por la [IETF](https://datatracker.ietf.org/doc/html/draft-bhutton-json-schema), hemos podido definir la estructura general de un archivo del tipo MIME `application/schema+json` que habrá de especificar, describir y validar las serializaciones cartográficas documentales aquí elaboradas y presentadas.

**NOTA:** Añadir aquí el enlace al esquema correspondiente

Dentro de la estructura general definida para cada archivo JSON del presente proyecto, se comienza dicho archivo por la integración de los metadatos descriptivos especificados en la segunda subfase de *Catalogación* y englobados en una cadena `"citation"`, para luego pasar a formar la estructura propia de esta serialización. Se establecerá un array de datos dentro de un elemento `slides` –diapositivas– que se integrará, a su vez, dentro de un elemento `storymap`, definidor de la forma de serialización como declaración del mismo.

```json
{
  "citation" : { … },
  "storymap": {
    "slides": [ … ]
  }
}
```

La primera de las diapositivas o `slides` del conjunto ha de ser, necesariamente y a efectos de su visualización, diferente de las demás, pues ha de constituir su portada y acceso a la serialización. Dos diferencias principales existen entre esta diapositiva y las demás: la primera, la existencia de un elemento `"type"`, con un valor `"overview"`, que ninguna otra diapositiva presentará.

Por su parte, el resto de diapositivas podrán tener un elemento –`"uniqueid"`– que exprese en su valor un identificador inequívoco de dicha diapositiva: de acuerdo con el esquema de metadatos, y dado que para esta función se empleará de forma predeterminada el DOI establecido para el documento concreto, se empleará una formación análoga a la que presentan los capítulos de libros que exhiben DOIs particulares, es decir, emplear una secuencia numérica de tres dígitos siguiendo al código y separado de él por un guión bajo –`_001`, `_002`, y así sucesivamente–.

```json
{
  "type": "overview",
  "date": "ÁMBITO TEMPORAL DE LA NARRACIÓN",
  "location": {
    "lat": 00.000000,
    "lon": 00.000000,
    "name": "TOPÓNIMO DE INICIO",
    "icon": "ICONO DE ACCIÓN",
    "line": true
  },
  "text": {
    "headline": "TÍTULO",
    "text": "PORTADA DE LA OBRA, O PORTADILLA",
  },
  "media": {
    "caption": "CÉDULA DESCRIPTIVA DE LA IMAGEN",
    "credit": "REFERENCIA DE LA IMAGEN",
    "alt": "TEXTO ALTERNATIVO A LA IMAGEN",
    "url": "ENLACE URL A LA IMAGEN"
  }
},
```

```json
{
  "uniqueid": "IDENTIFICADOR INEQUÍVOCO",
  "date": "FECHA EXTENDIDA",
  "location": {
    "lat": 00.000000,
    "lon": -00.000000,
    "name": "TOPÓNIMO",
    "icon": "ICONO DE ACCIÓN",
    "line": true
  },
  "text": {
    "headline": "ENCABEZADO",
    "text": "TRANSCRIPCIÓN TEXTUAL",
    "entities": {
      "agent": ["SUJETO", … , "SUJETO"],
      "action": "ACCIÓN",
      "object": ["OBJETO", … , "OBJETO"]
    }
  },
  "media": {
    "caption": "CÉDULA DESCRIPTIVA DE LA IMAGEN",
    "credit": "REFERENCIA DE LA IMAGEN",
    "alt": "TEXTO ALTERNATIVO A LA IMAGEN",
    "url": "ENLACE URL A LA IMAGEN"
  }
}
```

Después, `"date"`, como se podrá suponer, servirá en la diapositiva de portada para expresar el ámbito temporal de la narración, mientras que en cualquier otra servirá para expresar, en su valor, la fecha concreta de la acción descrita. Por su parte, `"location"` está destinado a expresar la información geográfica de inicio de la acción: latitud y longitud se expresan por separado, mediante elementos `"lat"`  y `"lon"`, en formato decimal a seis cifras.

El elemento `"name"` contendrá, por su parte, expresado en su valor, el topónimo de inicio para la portada, y el topónimo central a la acción descrita en cualquier otra diapositiva, enlazado mediante la formación de etiquetas HTML5 –que JSON permite y fomenta– a la URL del artículo de la Wikipedia en español sobre el topónimo concreto enunciado en este elemento.

Siguiendo con la misma subestructura de datos, `"icon"` enlazará a la imagen en formato PNG –por sus siglas en inglés, *Portable Network Graphic*– de un icono representativo de la acción principal a desarrollarse en la diapositiva concreta, mientras que en la portada enlazará al icono del proyecto; y, finalmente, `"line"` determinará si se dibujará una línea entre el nodo de localización de una diapositiva con la siguiente, desde la de portada hasta la final.

La siguiente subestructura está definida por el elemento `"text"`, y habrá de contener, de forma general, otros dos elementos constantes a su vez: `"headline"`, que si en la portada sirve para expresar el título del documento, en las demás diapositivas presentará el encabezado de la sección concreta descrita; y `"text"`, que en la presentación exhibirá como valor, en formato HTML5, la información que la obra ofrezca en su portada, y en las demás diapositivas contendrá, bajo iguales premisas, la transcripción textual de la sección concreta.

Más allá de los requerimientos del esquema predispuesto por la herramienta elegida para su publicación y visualización, se ha establecido una subestructura dependiente de la anterior que pretende describir la acción desarrollada en cada sección. Definida por el elemento `"entities"`, contendrá tres elementos a su vez: `"agent"`, `"action"` y `"object"`. El primero de ellos está destinado a expresar el o los agentes que desarrollan la acción concreta descrita, salvo en los casos en que la acción no tenga sujeto agente –como en los eventos meteorológicos, o en los accidentes náuticos–; el segundo, describe la acción, con el verbo de la misma en forma de infinitivo; el tercero contendrá los objetos sobre los que el sujeto –o los accidentes, meteorológicos o de otro tipo– ejerce la acción. Si bien, como decimos, el primero puede no existir, también es cierto que pueden ser varios los valores, a expresar como se muestra en el ejemplo, al igual que sucede con el último de estos elementos. Por supuesto, acción sólo puede haber una primaria, y aunque podría haber acciones secundarias –deshilvanables hasta el hastío…– no serán consignadas en esta serialización simplificada.

Por último, el elemento `"media"` servirá para mostrar, si lo hubiese, cualquier objeto digital –iconográfico, cartográfico…– que pueda enriquecer de alguna manera el expresado en el valor `"text"` contenido en su homólogo anterior. Una serie de elementos sirven a este fin: `"caption"` mostrará en su valor una cédula descriptiva de la imagen, a modo de título, que puede obtenerse por lo general de la propia imagen o de su descripción archivística; `"credit"` servirá para proporcionar la referencia de la imagen, proporcionando la signatura y la información proporcionada por las herramientas de descripción archivística correspondientes a su reservorio de origen, siempre siguiendo el esquema de citación CMOS 17 empleado en la segunda subfase de *Catalogación*; el elemento `"alt"` contendrá el texto alternativo a la presentación de la imagen, que servirá al fin único de no dejar en blanco el espacio cuando existan dificultades para la previsualización de la imagen; y, por último, `"url"` expresará el enlace a la URL de visualización de la imagen en línea, mismo que, cuando sea posible, lo hará a repositorios abiertos.

# Clase III. Serialización Cronológica de Corpus

Esta estructura de serialización corresponde, por lo general, a los artículos de opinión en la prensa política. Se entendió desde un principio que una serialización cronológica sería más conveniente al análisis de la evolución de dichas formas e interpretaciones, puestas en relación con los hechos históricos contextuales relevantes al punto. Es por ello que se eligió el software [*Timeline.JS*](http://timeline.knightlab.com/), que también ofrece, como en el anterior caso, una estructura de serialización de la información versátil y expresable dentro de los márgenes antedichos.

Siguiendo lo establecido por la propuesta informativa sobre la elaboración de meta-esquemas para el lenguaje de serialización JSON producida por la [IETF](https://datatracker.ietf.org/doc/html/draft-bhutton-json-schema), hemos podido definir la estructura general de un archivo del tipo MIME `application/schema+json` que habrá de especificar, describir y validar las serializaciones cronológicas de corpus, en forma de colección o antología, aquí elaboradas y presentadas.

**NOTA:** Añadir aquí el enlace al esquema correspondiente

Dentro de la estructura general definida para cada archivo JSON del presente proyecto, se comienza dicho archivo por la integración de los metadatos descriptivos especificados en la segunda subfase de *Catalogación* y englobados en una cadena `"citation"`, para luego pasar a formar la estructura propia de esta serialización.

A diferencia de la anterior forma de serialización, existe en este caso una imposición por parte del software elegido –[*Timeline.JS*](http://timeline.knightlab.com/)– para establecer una suerte de portada al corpus general, o a su serialización, para ser más exactos. En todo caso, no representa una dificultad, ni siquiera una imitación falsaria, sino tan sólo la forma de presentación de esta estructura. Esta, enunciada por el elemento `"timeline"`, contendrá dos elementos que servirán a esta presentación, `"text"` y `"media"`, dentro de un elemento `"title"` que establece la portada.

El primer elemento describirá la serialización, otorgándole un título como valor a su elemento `"headline"` y una descripción mediante un elemento `"text"`, mientras que el segundo dota a la portada de un objeto digital que la enriquece y muestra su potencial uso en una serie de elementos descriptivos de la misma: `"caption"` para su cédula descriptiva, `"credit"` para su referencia según los esquemas archivísticos y la norma CMOS17, `"alt"` para mostrar un texto alternativo a su visualización y `"url"` para enlazar a la URL donde se encuentre alojada la imagen.

```json
{
  "citation" : { … },
  "timeline": {
    "title": {
      "text": {
        "headline": "TÍTULO DE LA SERIALIZACIÓN",
        "text": "DESCRIPCIÓN DE LA SERIALIZACIÓN"
       },
      "media": {
        "caption": "CÉDULA DESCRIPTIVA DE LA IMAGEN",
        "credit": "REFERENCIA DE LA IMAGEN",
        "alt": "TEXTO ALTERNATIVO A LA IMAGEN",
        "url": "ENLACE URL A LA IMAGEN"
      },
    },
  "eras": [ … ],
  "events": [ … ]
  }
}
```

Como se puede ver en la anterior estructura, a esta subestructura inicial que sirve de presentación a la estructura general, siguen dos posibles matrices de datos, `"eras"` y `"events"`. Como bien se puede deducir de sus enunciados, la primera se corresponde a los períodos que dan contexto a la información serializada, mientras que la segunda habrá de contener la propia serialización. Con elementos muy similares a los descritos en estructuras anteriores, no está de más que expliquemos aquí, pormenorizadamente, cómo es su estructura y cuáles son las expresiones de sus valores.

```json
{
  "uniqueid": "IDENTIFICADOR INEQUÍVOCO",
  "autolink": true,
  "start_date": {
    "display_date": "FECHA PARA VISUALIZACIÓN",
    "year": "AÑO, EN CUATRO DÍGITOS",
    "month": "MES, EN DOS DÍGITOS",
    "day": "DÍA, EN DOS DÍGITOS"
  },
  "end_date": {
    "display_date": "FECHA PARA VISUALIZACIÓN",
    "year": "AÑO, EN CUATRO DÍGITOS",
    "month": "MES, EN DOS DÍGITOS",
    "day": "DÍA, EN DOS DÍGITOS"
  },
  "text": {
    "headline": "NOMBRE DEL PERÍODO",
    "text": "DESCRIPCIÓN DEL PERÍODO"
  }
}
```

Los períodos serán ordenados de forma secuencial mediante un elemento `"uniqueid"`, cuya conformación dependerá del método de periodización elegido en cada caso. Desde luego, los períodos pueden superponerse, de forma que varios sistemas de periodización podrán visualizarse simultáneamente. Un elemento `"autolink"` servirá para que cualquier enlace en código HTML5 que se inserte en cualquiera de los valores de los elementos de esta subestructura se active automáticamente como “clicable”, es decir, que pueda ser activado inmediatamente a su pulsación, cuando tenga un valor `true`, anulándose dicha acción cuando el valor sea `false`.

Seguidamente se expresarán las fechas de inicio –`"start_date"`– y finalización –`"end_date"`– del período descrito. Para dar los valores en forma que puedan ser visualizados tanto textualmente, a modo de etiquetas, como estructuralmente, en su posición cronolineal, se presentan dos conjuntos de elementos: el primero está formado por un sólo elemento, `"display_date"`, que servirá para mostrar la fecha en el primer sentido; el segundo, formado por los elementos `"year"`, `"month"` y `"day"`, servirá para su posicionamiento lineal. Ambos conjuntos se replican en ambos elementos que indican las fechas de inicio y finalización del período.

Finalmente, un elemento `"text"` proporciona el ámbito de descripción del período especificado, conteniendo para ello dos elementos: el primero, `"headline"`, servirá para contener el nombre otorgado al período descrito, mientras que el segundo, homónimo del superior, contendrá la descripción textual del mismo.

Los eventos de la cronolínea tienen una estructura muy similar a la que ya explicamos en la anterior forma de serialización para las diapositivas, si bien dos adecuaciones han sido añadidas a aquella forma.

```json
{
  "uniqueid": "IDENTIFICADOR INEQUÍVOCO",
  "group": "CONJUNTO A QUE PERTENECE",
  "autolink": true,
  "start_date": {
    "display_date": "FECHA PARA VISUALIZACIÓN",
    "year": "AÑO, EN CUATRO DÍGITOS",
    "month": "MES, EN DOS DÍGITOS",
    "day": "DÍA, EN DOS DÍGITOS"
  },
  "text": {
    "headline": "ENCABEZADO",
    "text": "TRANSCRIPCIÓN TEXTUAL",
    "entities": {
      "agent": ["SUJETO", … , "SUJETO"],
      "action": "ACCIÓN",
      "object": ["OBJETO", … , "OBJETO"]
    }
  },
  "media": {
    "caption": "CÉDULA DESCRIPTIVA DE LA IMAGEN",
    "credit": "REFERENCIA DE LA IMAGEN",
    "alt": "TEXTO ALTERNATIVO A LA IMAGEN",
    "url": "ENLACE URL A LA IMAGEN"
  }
}
```

Un elemento –`"uniqueid"`– servirá para expresar en su valor un identificador inequívoco de dicho evento: de acuerdo con el esquema de metadatos, y dado que para esta función se empleará de forma predeterminada el DOI establecido para el documento concreto, se empleará una formación análoga a la que presentan los capítulos de libros que exhiben DOIs particulares, es decir, emplear una secuencia numérica de tres dígitos siguiendo al código y separado de él por un guión bajo –`_001`, `_002`, y así sucesivamente–.

Seguidamente, se aplicará un elemento `"group"`, que sirve para agrupar los eventos en conjuntos: dado que este formato se empleará formalmente en el presente proyecto para la serialización estructurada de un corpus de artículos periodísticos de distintos orígenes, procedencias y adscripciones ideológicas, está clara la utilidad de este elemento, aunque el rango de valores posibles está aún por determinar. Le seguirá un elemento `"autolink"`, con la misma función y valores posibles explicados para el caso anterior, y que, de antemano, tendrá como valor expresado `true`.

Seguidamente se expresará la fecha del evento mediante, no un elemento "date", como sucediera en la anterior estructura, sino una `"start_date"`, en formalización de la subestructura periódica. Para dar los valores en forma que puedan ser visualizados tanto textualmente, a modo de etiquetas, como estructuralmente, en su posición cronolineal, se presentan dos conjuntos de elementos: el primero está formado por un sólo elemento, `"display_date"`, que servirá para mostrar la fecha en el primer sentido; el segundo, formado por los elementos `"year"`, `"month"` y `"day"`, servirá para su posicionamiento lineal.

La siguiente subestructura está definida por el elemento `"text"`, y habrá de contener, de forma general, otros dos elementos constantes a su vez: `"headline"`, que habrá de presentar el encabezado de la noticia concreta descrita; y `"text"`, que exhibirá como valor, en formato HTML5, la transcripción textual de la noticia concreta.

Más allá de los requerimientos del esquema predispuesto por la herramienta elegida para su publicación y visualización, se ha establecido una subestructura dependiente de la anterior que pretende describir la acción desarrollada en cada sección. Definida por el elemento `"entities"`, contendrá tres elementos a su vez: `"agent"`, `"action"` y `"object"`. El primero de ellos está destinado a expresar el o los agentes que desarrollan la acción concreta descrita, salvo en los casos en que la acción no tenga sujeto agente –como en los eventos meteorológicos, o en los accidentes náuticos–; el segundo, describe la acción, con el verbo de la misma en forma de infinitivo; el tercero contendrá los objetos sobre los que el sujeto –o los accidentes, meteorológicos o de otro tipo– ejerce la acción. Si bien, como decimos, el primero puede no existir, también es cierto que pueden ser varios los valores, a expresar como se muestra en el ejemplo, al igual que sucede con el último de estos elementos. Por supuesto, acción sólo puede haber una primaria, y aunque podría haber acciones secundarias –deshilvanables hasta el hastío…– no serán consignadas en esta serialización simplificada.

Por último, el elemento `"media"` servirá para mostrar, si lo hubiese, cualquier objeto digital –iconográfico, cartográfico…– que pueda enriquecer de alguna manera el expresado en el valor `"text"` contenido en su homólogo anterior. Una serie de elementos sirven a este fin: `"caption"` mostrará en su valor una cédula descriptiva de la imagen, a modo de título, que puede obtenerse por lo general de la propia imagen o de su descripción archivística; `"credit"` servirá para proporcionar la referencia de la imagen, proporcionando la signatura y la información proporcionada por las herramientas de descripción archivística correspondientes a su reservorio de origen, siempre siguiendo el esquema de citación CMOS 17 empleado en la segunda subfase de *Catalogación*; el elemento `"alt"` contendrá el texto alternativo a la presentación de la imagen, que servirá al fin único de no dejar en blanco el espacio cuando existan dificultades para la previsualización de la imagen; y, por último, `"url"` expresará el enlace a la URL de visualización de la imagen en línea, mismo que, cuando sea posible, lo hará a repositorios abiertos.

# Clase IV. Serialización Relacional de Corpus

Por último, tanto la correspondencia diplomática y de gobierno, como los debates legales y políticos sucedidos en las Cortes y publicados en las actas parlamentarias y en la prensa política y de gobierno, presentan dos estructuras muy similares por lo relacional de sus puntos. Aunque el primero de estos *corpora* tiene una estructura cronológica que podría estructurarse como se describió en el anterior punto, se consideró más conveniente que ambos corpus especificados aquí mostraran la estructura relacional que les es inherente, de manera que se optó por su presentación mediante un grafo dirigido elaborado con el software [*Cytoscape.JS](https://js.cytoscape.org/).*

El software a emplear en esta visualización presenta una estructura propia de datos en formato JSON, pero también acepta la instalación de un módulo que permite la utilización, tanto de entrada como de salida, de una especificación propuesta en la IETF como “[JSON-Graph Specification](https://github.com/jsongraph/json-graph-specification)”, con un tipo MIME de archivo asociado `graph/json`. A pesar de que en el marco del presente proyecto hemos tratado desde un inicio de fundamentar nuestras decisiones en la existencia tanto de software de visualización de código libre, abierto y gratuito, como de estándares establecidos por la IETF para la interpretación de lenguajes de serialización y etiquetado de textos, emplearemos en este punto, a la espera de que se asiente dicha especificación en un documento de recomendación, aquella de que el software nos provee, con la esperanza de que pronto –vista la velocidad de desarrollo de JSON– podremos transformar nuestras serializaciones de datos en un formato estandarizado.

*… [en proceso]*

# *Referencia*

El presente documento, ***Reglas de Edición del Proyecto “Noticias del Viejo Imperio, 1860-1866”***, creado por David Domínguez Herbón, es una publicación respaldada por el [Centro de Estudios Americanos](https://artesliberales.uai.cl/centros/centro-de-estudios-americanos/) y la [Facultad de Artes Liberales](https://artesliberales.uai.cl/) de la Universidad Adolfo Ibáñez, el [Instituto Universitario de Investigación en Estudios Latinoamericanos](https://ielat.com/) de la Universidad de Alcalá y el [Centro Europeo para la Difusión de las Ciencias Sociales](http://www.archivodelafrontera.com/), instituciones bajo cuyo auspicio se publica.

Todos los objetos digitales en esta web se publican en el marco del [Proyecto Fondecyt de Iniciación Nº 112000245](https://s3.amazonaws.com/documentos.anid.cl/iniciacion/2020/fallo/NominaProyectosAprobadosIniciacion2020.pdf) “Noticias del Viejo Imperio. La Expedición del Pacífico y la Guerra hispano-sudamericana en los imaginarios geopolíticos de la España liberal (1860-1866)”, financiado por la [Agencia Nacional de Investigación y Desarrollo](https://www.anid.cl/), del [Ministerio de Ciencia, Tecnología, Conocimiento e Innovación](http://www.minciencia.gob.cl), del Gobierno de Chile.

Este proyecto se adhiere a la [Budapest Open Access Initiative](https://www.budapestopenaccessinitiative.org/boai-10-translations/spanish). Todos los objetos digitales de este proyecto se distribuyen bajo una [Licencia Creative Commons *Zero* 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/deed.es).

*Correo webmaster [admin@envi19.cl](mailto:admin@envi19.cl)* · *Versión 1.0  ·  Fecha de creación: 02 de marzo de 2021  ·  Última actualización: 12 de julio de 2021*