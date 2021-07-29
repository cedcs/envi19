# Catalogación

Dentro del algoritmo de procesos del presente proyecto se producen tres objetos técnicos concretos: una *reprografía* *facsimilar digital* proporcionada por diversas instituciones de resguardo y/o digitalización de fondos, un *archivo de texto plano* con la transcripción del texto en formato Markdown y un *archivo JSON* que contiene el texto segmentado y etiquetado para su edición. Todos ellos integrarán *metadatos*, aunque desde este proyecto dichos metadatos sólo se integrarán en dos de ellos. Pero, ¿qué son metadatos?

De forma general, podemos decir que son [“datos que proporcionan información sobre otros datos”](https://es.wikipedia.org/wiki/Metadato). Si consideramos que las etiquetas que vamos a aplicar sobre el texto son datos identificados de forma sistemática, precisaremos de ciertos *metadatos* que den orden y/o estructura a dichos datos. Constituyen, así, una descripción de las características de un conjunto de datos enunciada siguiendo un estándar, y que tiene vital importancia para la administración de un sistema digital. Por ejemplo, la ficha catalográfica al inicio de un libro impreso y su colofón constituyen, en buena medida, los metadatos de dicho libro, pues proporcionan información general del mismo que ayuda a su identificación y ordenamiento; del mismo modo, podemos considerar metadatos los textos de las etiquetas traseras de los botes de champú, o los escritos en las que lleva cosidas internamente la ropa que llevamos puesta.

La labor de *catalogación por metadatos* de los objetos técnicos concretos producto de la transcripción textual se realiza, en este proyecto, en dos momentos diferenciados dentro del algoritmo de procesos, puesto que son dos los productos finales de esta técnica. Un primer momento corresponde a la tercera fase de dicho algoritmo, de *Transcripción*, como se describe en la *Secuencia descriptiva del algoritmo de procesos*, mientras que el segundo momento de catalogación por metadatos se produce en la quinta fase, de *Edición*, según se especifica en el antedicho documento. A continuación se muestran, de forma consecutiva, ambas fases a fin de que resulte más fácil la comprensión e interrelación de los contenidos explicitados en las acciones técnicas descritas.

# Subfase I: la Catalogación en la Transcripción

La primera de las subfases técnicas de la transcripción corresponde, pues, a la catalogación del documento informático que se va a producir mediante la inclusión de una primitiva ‒por lo inicial‒ forma de metadatos descriptivos. La principal función dentro del algoritmo completo del objeto técnico producto de esta fase ‒una *ficha catalográfica*‒ es la de servir de base para la construcción de los metadatos que contendrá el encabezamiento del objeto técnico definitivo del proceso, que será la transcripción editada.

Para ello, el agente encargado de la transcripción deberá proceder a la identificación del documento en función de una forma simplificada del estándar internacional de descripción archivística [ISAD(G)](http://www.icacds.org.uk/eng/ISAD%28G%29.pdf%20%22ISAD(G)%20en%20ICACDS) adaptada al esquema de metadatos [Dublin Core](https://es.wikipedia.org/wiki/Dublin_Core), de manera que el documento digital estará perfectamente identificado dentro y hacia afuera del sistema, y remitirá tanto al documento de archivo del cual proviene, como a la reprografía facsimilar digital a partir de la cual fue transcrito. La ficha catalográfica resultante encabezará este archivo, preparatorio, como ya dijimos, de la creación del objeto técnico producto de la siguiente fase.

A continuación, se muestra un listado explicativo con los metadatos distribuidos por áreas de información que será necesario cumplimentar para cada *archivo de texto plano* que se produzca como producto de la fase de *Transcripción*.

### 1. Denominación

Los *metadatos del archivo* son aquellos concernientes a la identificación inequívoca del documento. Se ha definido un código que será importante para este fin, dado que será necesario a la hora de llevar a buen puerto las labores de segmentación, serialización y semantización en las siguientes fases.

En primer lugar, los impresos bibliográficos pueden clasificarse en dos categorías, cada una de ellas con sus reglas diferenciadas:

- si son publicaciones bibliográficas en general, el nombre comenzará por las siglas ‘ib’, que lo distinguen como un impreso bibliográfico, seguidas de un guión, luego, en minúsculas, el o los apellidos (siendo más de una persona, separados por un guión bajo los de cada uno de los de los demás) de quien ostente la responsabilidad de autoría o de edición del volumen, seguidos de otro guión sencillo, luego el año y, tras otro guión, el título en letras minúsculas, sin acentos, la letra ‘ñ’ sustituida por la combinación homófona ‘nh’ y cada palabra separada de la contigua por un guión bajo, como se puede comprobar en el siguiente ejemplo:

    ```
    ib-almagro-1866-breve_descripcion_de_los_viajes_hechos_en_america
    ```

- si se trata de la transcripción de los documentos parlamentarios excerptas de los diarios de sesiones publicados, el nombre comenzará también por las siglas ‘ib’, que lo distinguen como un impreso bibliográfico, seguidas de un guión, las siglas ‘ds’, que lo identifican como parte de dichos diarios de sesiones acompañadas inmediatamente del ordinal volumen de aquella publicación, seguidas de un guión sencillo, a continuación las páginas de inicio y final del fragmento transcrito separadas por un guión bajo, otro guión sencillo, el año correspondiente y, tras otro guión sencillo, una corta y sucinta descripción de lo discutido en dicho fragmento escrito en letras minúsculas, sin acentos, la letra ‘ñ’ sustituida por la combinación homófona ‘nh’ y cada palabra separada de la contigua por un guión bajo, como se puede comprobar en el siguiente ejemplo:

    ```
    ib-ds46-1836-132_146-discusion_sobre_la_independencia_de_america
    ```

En caso de que se trate de un impreso hemerográfico, es decir, de una publicación periódica, se comenzará por las siglas ‘ih’ que lo identifican como tal, seguidas de un guión sencillo, luego el nombre del periódico en letras minúsculas y sus partes –de tenerlas– separadas por guiones bajos, otro guión sencillo, luego el lugar de publicación en las mismas condiciones que el nombre de la publicación, otro guión, la fecha bajo la ISO 8601, cada uno de sus elementos separados entre sí por guiones bajos, y, tras un último guión, el título de la nota o artículo de prensa en letras minúsculas, sin acentos, la letra ‘ñ’ sustituida por la combinación homófona ‘nh’ y cada palabra separada de la contigua por un guión bajo, como se puede comprobar en el siguiente ejemplo y nunca, bajo ningún concepto, empleando como base los metadatos heredados en la reprografía facsimilar digital de origen:

```
ih-el_espanhol-madrid-1837_04_01-la_guerra_en_america
```

Para los impresos iconográficos se emplearán como siglas de distinción ‘ii’, sean pinturas o bocetos, seguidas de un guión, el o los apellidos del autor en letras minúsculas, sin acentos y la letra ‘ñ’ sustituida por la combinación homófona ‘nh’, seguidas por el año de realización, otro guión y, por último, el título o una descripción de su expresión iconográfica siguiendo la misma guía empleada para los apellidos, separando en esta ocasión cada palabra de la contigua por un guión bajo, como se muestra en el siguiente ejemplo:

```
ii-salaya-1869-retrato_de_casto_mendez_nunhez_(1824_1869)
```

En cuanto a los impresos que denominaremos litográficos, sean estos de contenido o expresión cartográfica o iconográfica, iniciarán por las siglas ‘ic’, seguidas por un guión sencillo, luego el apellido del autor separado con un guión bajo del apellido del impresor, un guión sencillo, el año de publicación y, tras otro guión del mismo tipo, el título o una concisa descripción de su contenido en letras minúsculas, sin acentos, la letra ‘ñ’ sustituida por la combinación homófona ‘nh’ y cada palabra separada de la contigua por un guión bajo, como se puede comprobar en el siguiente ejemplo:

```
ic-jefferys_cartwell-1779-depiction_of_the_west_indies
```

Para seguir por orden con los manuscritos, comenzaríamos por los documentos en forma general, que comenzarían por las siglas ‘mr’ que los identificarán como relaciones manuscritas, seguidas de un guión, luego las siglas del archivo según las establezca la institución de resguardo del documento en cuestión, en letras minúsculas, seguidas por un guión, tres siglas identificativas del fondo al que está adscrito, otro guión, el número de legajo al que pertenece, otro guión, el número de expediente, otro guión, los folios que lo limitan, con las letras ‘r’ o ‘v’ según sean recto o vuelto, separados ambos por un guión bajo, y, tras otro guión, su título o una concisa descripción de su contenido en letras minúsculas, sin acentos, la letra ‘ñ’ sustituida por la combinación homófona ‘nh’ y cada palabra separada de la contigua por un guión bajo, como se puede comprobar en el siguiente ejemplo:

```
mr-ahn-meg-63-n4-163r_184v-reglamento_de_la_comision_cientifica_del_pacifico
```

En el caso de documentos manuscritos de contenido epistolar, comenzarán por las siglas ‘me’, seguidas por un guión sencillo; luego, del mismo modo que se procede con los anteriores, las siglas del archivo según las establezca la institución de resguardo del documento en cuestión, en letras minúsculas, seguidas por un guión, tres siglas identificativas del fondo al que está adscrito, otro guión, el número de legajo al que pertenece, otro guión, el número de expediente, otro guión, los folios que lo limitan, con las letras ‘r’ o ‘v’ según sean recto o vuelto, separados ambos por un guión bajo, otro guión, la fecha en formato ISO 8601, cada uno de sus elementos separados entre sí por guiones bajos, y, tras un último guión, los apellidos del remitente y el destinatario separados por un guión bajo, en letras minúsculas, sin acentos, la letra ‘ñ’ sustituida por la combinación homófona ‘nh’ y cada palabra separada de la contigua por un guión bajo, como se puede comprobar en el siguiente ejemplo:

```
me-ahn-meg-63-n4-185r_186v-1863_04_07-almagro_cabanillas
```

Análogamente, como se puede comprobar, todos los materiales documentales manuscritos comienzan por siglas distintas para diferenciar su contenido, y prosiguen de la misma manera, especificando su signatura de forma coherente, sólo variando las últimas secciones. Así, en el caso de materiales iconográficos o cartográficos, comenzarían los primeros por las siglas ‘mi’ y los segundos por ‘mc’, y se procedería en ambos casos en sus partes términas del mismo modo que en sus homólogos impresos, con la salvedad de no tener que indicar el apellido del impresor o la fecha completa cuando sólo se cuente con el año.

### 2. Metadatos del Documento

El proceso de catalogación por metadatos está dividido, en cualquiera de sus dos subfases ‒a saber, al inicio de la fase de *Transcripción* y como parte de la fase de *Edición*‒ en tres apartados: el primero de ellos, declarativo, se presenta como una forma de identificar cada archivo concreto; el segundo, referencial, vincula la edición con su original, tanto en lo analógico-archivístico como en lo reprográfico-digital; el tercero, expositivo, describe propiamente cada edición de forma estandarizada, coherente y concreta.

En cuanto al primer apartado, en esta primera subfase consta únicamente de una etiqueta de **Descripción** ‒`[dc:description]`‒ en la que se especifica el nombre del archivo, mismo que, como se ha comprobado en el anterior primer punto, se elaborará de distintas formas según sea la procedencia de las reprografías facsimilares que le den origen. De forma general, *ut supra*, se procederá al establecimiento de una codificación a partir de la signatura, información bibliográfica o hemerográfica del documento de cuyo texto se realizará la transcripción. La elaboración de dicho código de identificación queda a discreción del técnico usuario, ya que son muchas las instituciones y tipos de origen de los documentos recopilados en el presente proyecto.

```markdown
[dc:description]mr-ahn-meg-63-n4-163r_184v-reglamento_de_la_comision_cientifica_del_pacifico
```

### 3. Metadatos del Original

Después de este primer campo, cuyo establecimiento es fundamental porque da nombre a cada archivo digital que contiene una transcripción, seguirían los campos de vinculación con otros elementos, tanto internos como externos, por medio de una URL en cada caso.

En primer lugar, se expresará el **Título** ‒`[dc:title]`‒ o encabezamiento de la obra original, siguiendo estrictamente las reglas de transcripción establecidas para este proyecto.

```markdown
[dc:title]Reglamento de la Comisión Científica del Pacífico
```

Se le añade, a continuación, una etiqueta `[dc:lang]`, destinada a expresar el valor de la **Lengua** en que fue producida mayormente la obra original editada aquí, es decir, la lengua que abarque tanto o más de un 70 % de la obra original. Para ello se empleará, siguiendo las recomendaciones de la iniciativa *Dublin Core*, una combinación de dos estándares internacionales, a saber, la norma ISO 639-1 para códigos lingüísticos y la norma ISO 3166-2 para códigos nacionales, de manera que puedan ser expresadas variantes nacionales de lenguas como la castellana. Ambos valores se expresarán coherentemente con las propias normas, y separados por un guión sencillo: `es-ES`, `es-CL`, `fr-FR` y `en-GB` son sólo algunos ejemplos.

```markdown
[[dc:l](dc:title)ang]es-ES
```

A continuación se expresará textualmente la información relativa a la mención de responsabilidad de creación sobre el documento original, es decir, su **Creador o Creadora** ‒`[dc:creator]`‒, siguiendo un esquema en el que los apellidos antecederán al nombre o nombres, separados ambos con una coma y un espacio en blanco. Cuando sea posible, es decir, cuando esta exista, se deberá incluir, entre paréntesis, un enlace URL a su biografía en la edición de Wikipedia en la lengua en que dicha persona responsable de la producción del documento original desarrollara su carrera.

```markdown
[[dc:creator](dc:creator)]Almagro y Vega, Manuel de (https://es.wikipedia.org/wiki/Manuel_Almagro_(antropólogo) "Almagro y Vega, Manuel de")
```

Seguidamente se expresará gráficamente la **Signatura** del documento original analógico según aparezca expresada por su institución de preservación y/o productora de la herramienta de catalogación y descripción archivística empleada para su identificación mediante la etiqueta `[dc:source]`, así como una URL entre paréntesis enlazando a la ficha catalográfica que dicha institución haya compartido en línea, siempre y cuando esta sea accesible mediante un [enlace permanente](https://es.wikipedia.org/wiki/Enlace_permanente), o *permalink*.

Después, deberá expresarse la signatura de la **Reprografía** digital facsimilar proporcionada, bien por la institución de preservación, bien por otra vinculada a ella, que será por lo general distinta de la anterior *Signatura*, pero que, cuando no lo sea, se consignará el mismo valor expresado de la misma manera, tras una etiqueta `[dc:relation]`. Como en otros casos, precederá a la URL que enlace directamente a la reprografía digital facsimilar, no ya a la ficha catalográfica, de nuevo colocada entre paréntesis. En resumidas cuentas, los términos empleados para describir a la *Fuente*, en tanto figura analógica, y al *Intermediario*, en tanto figura digital, son distintos, como se puede ver en su expresión general a continuación:

```markdown
[dc:source]BNE, MSS/7231 (http://catalogo.bne.es/uhtbin/cgisirsi/x/0/0/57/5/3?searchdata1=4662667{CKEY}&searchfield1=GENERAL^SUBJECT^GENERAL^^&user_id=WEBSERVER)
[dc:relation]BNE, bdh0000094985 (http://bdh.bne.es/bnesearch/detalle/bdh0000094985)
```

Siguiendo el hilo, **Editorial** ‒`[dc:publisher]`‒ es una etiqueta que se empleará para expresar textualmente la información relativa a la mención de responsabilidad sobre la publicación del documento original, caso de que haya sido impreso y publicado, o sobre el marco de producción del mismo, si ha quedado como manuscrito. Se seguirá, para ello, el mismo esquema `Apellidos, Nombre` empleado para la mención de responsabilida de creación, o bien el nombre completo de la publicación, postergando el artículo si lo tuviera ‒`Mercurio de Valparaíso, El`‒, y seguido también de un enlace URL a la página web de dicha persona o entidad de la edición de Wikipedia en la lengua en que dicha persona o entidad responsable de la producción o publicación del documento original se desarrollara.

```markdown
[dc:publisher]Mercurio de Valparaíso, El (https://es.wikipedia.org/wiki/El_Mercurio_de_Valparaíso)
```

Por último dentro de esta sección, se incorporarán los metadatos relativos a las fechas de **Creación** ‒`[dc:created]`‒ y de **Publicación** ‒`[dc:issued]`‒ del documento original, según se encuentren expresadas en las herramientas de descripción archivística correspondientes. De nuevo, como sucediera en un caso anterior, sería un ejercicio ocioso por lo fútil tratarlas por separado: la primera de ellas contendrá, como su propia expresión indica, la fecha en que fue concluida la producción del documento editado, mientras que la segunda contendrá la fecha en que fue publicada, recibida por su destinatario o puesta a disposición del público, siempre que exista una distinción entre ambas, replicándose en caso contrario el metadato expresado en la primera de ellas. En cualquier caso, para la expresión gráfica de los valores de estos términos se empleará siempre, tanto en este lugar como a lo largo de todo este proyecto, la expresión recomendada por la norma ISO 8601, mediante la cual se expresan consecutivamente año ‒con 4 dígitos‒, mes y día ‒ambos con 2 dígitos‒, separados por guiones sencillos.

```markdown
[dc:created]1861-04-23
[dc:issued]1861-05-17
```

### 4. Metadatos de la Edición

En primer lugar, dentro del conjunto de metadatos destinados a describir el producto editorial fruto de la fase de *Transcripción*, se utilizará la etiqueta **Colaborador** ‒`[dc:contributor]`‒ para contener la expresión onomástica de la mención de responsabilidad en grado de colaboración sobre la producción de la edición, es decir, los apellidos y el nombre ‒separados por una coma y un espacio‒ de la persona responsable de la transcripción y edición del documento en cuestión, además de, consecutivamente, un enlace a la página personal o de redes sociales de elección de dicha persona en pausa parentética.

```markdown
[[dc:contributor](dc:contributor)]Domínguez Herbón, David (https://twitter.com/herdado)
```

Después, se incluirá la **Referencia Bibliográfica**, es decir, una expresión textual de la forma en que se debe citar, no ya el documento original del que deriva la reprografía digital facsmiliar empleada en la edición realizada en el presente proyecto, sino dicha edición. Para ello se empleará la etiqueta `[dc:citation]`, con una sola forma siguiendo las reglas establecidas por *The Chicago Manual of Style* en su edición 17ª (CMOS17).

```markdown
[dc:citation]Barreiro, Agustín Jesús, “Historia de la Comisión Científica del Pacífico (1862 a 1865)”, ed. por David Domínguez Herbón, en Rodrigo Escribano Roca, dir., *Noticias del Viejo Imperio (1862-1866)*, Viña del Mar: Universidad Adolfo Ibáñez - Facultad de Artes Liberales - Centro de Estudios Americanos / Universidad de Alcalá - Instituto Universitario de Investigación en Estudios Latinoamericanos, 2021 [DOI].
```

Por supuesto, deberán incluirse los datos relativos a las entidades que amparan la **Publicación** de las ediciones producidas en el marco del presente proyecto, mismas que ya se habrán podido comprobar en el caso antecedente. Dado que este proyecto está enmarcado dentro de uno mayor cuyas entidades de respaldo académico son concretas y estables, los valores de expresión de estos metadatos serán constantes y comunes a todas las ediciones, tanto en cuanto a las expresiones textuales como a los enlaces URL. Y dado que se trata de varias instituciones, serán varias las etiquetas del mismo tipo ‒`[dc:publisher]`‒ que se aplicarán consecutivamente. Por supuesto, cada una de ellas irá seguida de un enlace a la página principal de su instituciones correspondiente, entre paréntesis.

```markdown
[[dc:publisher](dc:publisher)]Proyecto Noticias del Viejo Imperio, 1862-1866 ([http://envi19.cl/](http://envi19.cl/))
[[dc:publisher](dc:publisher)]Universidad Adolfo Ibáñez - Facultad de Artes Liberales ([https://artesliberales.uai.cl/](https://artesliberales.uai.cl/))
[[dc:publisher](dc:publisher)]Universidad Adolfo Ibáñez - Centro de Estudios Americanos ([https://artesliberales.uai.cl/centros/centro-de-estudios-americanos/](https://artesliberales.uai.cl/centros/centro-de-estudios-americanos/))
[[dc:publisher](dc:publisher)]Universidad de Alcalá - Instituto Universitario de Investigación en Estudios Latinoamericanos ([https://ielat.com/](https://ielat.com/))
[[dc:publisher](dc:publisher)]Fundación Centro Europeo para la Difusión de las Ciencias Sociales ([http://www.archivodelafrontera.com/](http://www.archivodelafrontera.com/))
```

Seguidamente, será necesario añadir las etiquetas correspondientes para expresar los valores de metadatos de las fechas de **Última Modificación** ‒*vel* creación, o finalización del proceso de edición, si se quiere‒ mediante la etiqueta `[dc:modified]`, y de **Puesta a Disposición** del público ‒*vel* publicación en la plataforma‒ con la etiqueta `[dc:available]`. De nuevo, en ambos casos se seguirá la misma norma ISO 8601, según lo recomienda la iniciativa *Dublin Core*, con los cuatro dígitos del año, los dos del mes y los dos del día expresados consecutivamente, separados por guiones sencillos.

```markdown
[dc:modified]2021-05-02
[dc:available]2021-06-11
```

A continuación, se expresará textualmente la **Categoría** de la edición dentro de un esquema jerárquico de varios niveles transversales, para lo que se utilizarán, consecutivamente, tres etiquetas `[dc:type]`. Los valores que se podrán expresar en cualquiera de estas tres etiquetas serán constantes y comunes para todas las ediciones cuyos metadatos habrán de ser registrados. Estas tipologías han sido establecidas a partir de diferentes características de los objetos digitales de los que se pretenden producir ediciones, y que pasaremos a describir a continuación:

- según la forma de *Publicación* de los objetos originales, estos pueden ser clasificados como `bibliográfico`, `cartográfico`, `documental`, `escultórico`, `fotográfico`, `hemerográfico`, `litográfico`, `musical`, `panfletario` o `pictórico`;
- según la *Estructura* interna de dicha publicación, podrán ser considerados `acta`, `anuncio`, `artículo`, `aviso`, `bitácora`, `canción`, `carta`, `carta de navegación`, `circular`, `composición`, `crónica`, `debate`, `declaración`, `decreto`, `despacho`, `diario`, `discurso`, `ensayo`, `escultura`, `fotocomposición`, `fotografía`, `guía`, `historia`, `informe`, `lección`, `ley`, `libreto`, `litografía`, `mapa`, `maqueta`, `mensaje`, `misiva`, `modelo`, `narración`, `nota de prensa`, `noticia`, `orden`, `partitura`, `plano`, `poesía`, `reportaje`, `representación`, `retrato`, `tratado` o `vista`; y, por último,
- según su *Estilo* compositivo, podrán ser `administrativo`, `amatorio`, `antropológico`, `apologético`, `biográfico`, `corográfico`, `cronístico`, `descriptivo`, `elegíaco`, `encomiástico`, `enunciativo`, `épico`, `etnográfico`, `exegético`, `ficcional`, `hagiográfico`, `historiográfico`, `informativo`, `jurídico`, `moral`, `narrativo`, `pedagógico`, `performativo`, `político`, `prescriptivo`, `sintético`, `técnico`, `teológico` o `testimonial`.

No obstante la coexistencia de tres formas –que no niveles– descriptivas, si bien de la primera de ellas, es decir, de aquella que expresa la forma de *Publicación*, sólo se mostrará un valor para cada elemento transcrito, editado y publicado, es probable que del segundo tipo haya que emplear más de uno, y es claro que, por lo general, del tercero se mostrará más de un tipo para cada elemento. Por supuesto, podrán ser empleadas tantas etiquetas `[dc:type]` como sean necesarias. A continuación mostramos un ejemplo de esta forma de categorización:

```markdown
[dc:type]bibliográfico
[dc:type]crónica
[dc:type]diario
[dc:type]épico
[dc:type]narrativo
[dc:type]testimonial
```

A fin de que cada edición concreta muestre en su esquema de metadatos un DOI correctamente formado y preparado para su vinculación directa, se incluirá este a modo de **Identificador**, mediante una etiqueta `[dc:identifier]` conforme a lo establecido por la iniciativa *Dublin Core*. Así, se expresarán tanto el código alfanumérico proporcionado por el servicio de alojamiento para las ediciones documentales, siguiendo para ello las recomendaciones de la norma [RFC 4452](https://tools.ietf.org/html/rfc4452), conforme a la norma ISO DOI, como su forma en URL entre paréntesis.

```markdown
[dc:identifier]10.1000/182 (https://doi.org/10.1000/182)
```

Después se pasará a expresar el **Formato** mediante el término `[dc:format]`, mismo que tiene por objetivo contener la expresión del tipo [MIME](https://es.wikipedia.org/wiki/Multipurpose_Internet_Mail_Extensions) de todas y cada una de las ediciones producidas en este proyecto, por lo que los valores aquí manifestados serán constantes y comunes a todas ellas. Su valor, por ende, será siempre `plaintext/markdown`, añadiéndose a continuación dos etiquetas más, con la expresión `[dc:conformsTo]` para indicar que este tipo concreto, y su tipología, se adhieren a lo establecido en las recomendaciones [RFC 7763](https://tools.ietf.org/html/rfc7763) y [RFC 7764](https://tools.ietf.org/html/rfc7764), respectivamente, cada una de ellas seguida de la URL de su especificación técnica entre paréntesis. En este sentido, podría parecer equivocado el formato, dado que la publicación se realizará en el sitio web: esta duda se resuelve si tenemos en cuenta que dicha publicación web será únicamente subsidiaria de aquella destinada a descarga, en un archivo alojado con un DOI asociado, como hasta ahora se ha venido considerando.

```markdown
[dc:format]plaintext/markdown
[dc:conformsTo]RFC 7763 ([https://tools.ietf.org/html/rfc7763](https://tools.ietf.org/html/rfc7763))
[dc:conformsTo]RFC 7764 ([https://tools.ietf.org/html/rfc7764](https://tools.ietf.org/html/rfc7764))
```

A continuación se consignará la **Extensión** del documento mediante una etiqueta `[dc:extent]`, tomando como magnitud la más representativa de longitud del espacio de almacenamiento, `bytes`, y teniendo presente, de nuevo, que el objeto cuya extensión se ha de medir es el archivo `plaintext/markdown` hasta aquí descrito, y no su expresión en el sitio web, cuyo formato será xml ó html, ni cualquiesquiera otros archivos para descarga derivados de aquél.

```markdown
[[dc:extent]768 bytes](dc:extent)
```

Por último, se concluirán los metadatos con la adición de dos etiquetas más, `[dc:license]` y `[dc:rights]`, que tienen por objetivo expresar tanto la licencia de uso y reproducción sobre los objetos digitales concretos ‒es decir, sobre los archivos `plaintext/markdown`‒ como los derechos de propiedad intelectual y acceso a dichos objetos. Los valores expresados en estos términos serán constantes a lo largo de todo el proyecto y comunes a todos los objetos digitales producidos y publicados en su desarrollo.

```markdown
[dc:license]CC0 1.0 Universal ([https://creativecommons.org/publicdomain/zero/1.0/deed.en](https://creativecommons.org/publicdomain/zero/1.0/deed.enDOI))
[dc:rights]Open Access / Public Domain Dedication ([https://www.budapestopenaccessinitiative.org/read](https://www.budapestopenaccessinitiative.org/read))
```

Como se puede observar en la expresión de dichos términos, se ha optado por una licencia [Creative Commons *Zero* 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/deed.en), dado que todas las ediciones a publicarse en el marco del actual proyecto parten de originales que forman ya parte del Dominio Público a nivel mundial, y dado que no existe ninguna reclamación de derecho alguno sobre los originales, no existe razón alguna por la que debiera haberla sobre unas ediciones que, por sí mismas, ya muestran tanto el crédito a sus realizadores, como al proyecto en cuyo marco se producen, y a las instituciones que lo respaldan.

# Subfase II: la Catalogación en la Edición

La primera de las subfases técnicas de la *Edición* corresponde, pues, a la (re)catalogación del documento informático que se va a producir mediante la inclusión de una forma simple de metadatos descriptivos, trasladando los valores de los metadatos integrados en la primera subfase de catalogación ‒*vid supra*‒ a una subestructura de metadatos en formato JSON que pueda ser integrada en la estructura de publicación prediseñada. No dejará de ser, por ende, una ficha catalográfica referente a la producida con anterioridad: al emplear un esquema de metadatos [DCMI](http://purl.org/dc/elements/1.1/) ‒que, aunque diseñado para su implantación en XML, ha sido adaptado al formato en uso‒ se fomentarán su representación, interoperabilidad, transformabilidad y descubribilidad de sus valores expresados.

Para ello, el agente encargado de la edición deberá proceder a la transferencia de los valores de los metadatos expresados en la ficha catalográfica producida en la primera subfase de la *Catalogación* a un esquema ya diseñado. Es probable que, en el marco de las plataformas de publicación empleadas o desarrolladas para el presente proyecto, se relice una integración análoga de estos valores, pero no será el mismo esquema empleado en esta subfase, dado que la intención última de ésta es transformar todos los metadatos de catalogación en metadatos DCMI-JSON que puedan conformarse en un archivo monolítico y, a la vez, ser interpretados por separado, sin dejar de identificar y describir inequívocamente cada documento digital producido en el proyecto.

A continuación se muestra un listado explicativo con los metadatos distribuidos por áreas de información que será necesario cumplimentar para cada *archivo JSON* que se produzca como producto de la fase de *Edición*. Es necesario tener en cuenta que, en el caso de esta subfase, dado que los metadatos no están destinados a describir sino el producto final, su estructuración debe tener otro ordenamiento que responda a la descripción de este, y no tanto ya de su original.

Primeramente, se definirá y establecerá una estructura de esquema `application/schema+json` que organice, describa y valide cualquier sección de metadatos de cualquier archivo `application/json` producido en el presente proyecto. Para ello se seguirán los lineamientos establecidos por la  [DCMI](http://purl.org/dc/elements/1.1/) para producir esquemas en este formato, mismos que, a partir de un antecedente general, nosotros emplearemos para producir una sola estructura a integrarse dentro de cada uno de los documentos de esquema de este proyecto, que serán cuatro: uno para las ediciones digitales documentales, otro para las serializaciones cartográficas, otro más para las serializaciones cronológicas y un último esquema para las seriaciones relacionales de corpus.

```json
{
  "title" : "JSON schema for DCMI input data",
  "description" : "JSON schema for descriptive citations based on the Dublin Core Metadata Initiative Specification",
  "$schema" : "[http://json-schema.org/draft-07/schema#](http://json-schema.org/draft-07/schema#)",
  "$id" : "[https://cedcs-hd.github.io/json-schemes/dcmi-data.json](https://cedcs-hd.github.io/json-schemes/dcmi-data.json)",
  "type" : "array",
  "items" : {
    "type" : "object",
    "properties" : {
      "dc:type" : {
        "description" : "The class within the set of classes specified by the DCMI Type Vocabulary, used to categorize the nature or genre of the resource.",
        "type" : "string",
        "enum" : [ "article-newspaper", "book", "collection", "dataset", "document", "legislation", "manuscript", "map", "musical_score", "pamphlet", "performance", "regulation", "report", "song", "speech", "treaty" ],
        "conformsto": "[http://purl.org/dc/dcmitype/](http://purl.org/dc/dcmitype/)"
      },
      "dc:identifier" : {
        "description" : "An unambiguous reference to the resource within a given context.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/identifier](http://purl.org/dc/elements/1.1/identifier)"
      },
      "dc:bibliographiccitation" : {
        "description" : "A bibliographic reference for the resource. Recommended practice is to include sufficient bibliographic detail to identify the resource as unambiguously as possible. It shall conform to CMOS 17: [https://www.chicagomanualofstyle.org/tools_citationguide.html."](https://www.chicagomanualofstyle.org/tools_citationguide.html.%22),
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/identifier](http://purl.org/dc/elements/1.1/identifier)"
      },
      "dc:description" : {
        "description" : "An account of the resource. Description may include but is not limited to: an abstract, a table of contents, a graphical representation, or a free-text account of the resource. In this special case, we shall use this item to provide the name of the digital JSON archive being catalogued.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/description](http://purl.org/dc/elements/1.1/description)"
      },
      "dc:title" : {
        "description" : "A name given to the resource.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/title](http://purl.org/dc/elements/1.1/title)",
      },
      "dc:alternative" : {
        "description" : "An alternative name for the resource. As the distinction between titles and alternative titles is application-specific, in this case we shall use this item to represent the original title of the edited text.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/title](http://purl.org/dc/elements/1.1/title)"
      },
      "dc:creator" : {
        "description" : "An entity responsible for making the resource. Recommended practice is to identify the creator with a URI. If this is not possible or feasible, a literal value that identifies the creator may be provided. Such being the case, we shall use an ordered way to do it so.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/creator](http://purl.org/dc/elements/1.1/creator)"
      },
      "dc:contributor" : {
        "description" : "An entity responsible for making contributions to the resource. The guidelines for using names of persons or organizations as creators apply to contributors.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/contributor](http://purl.org/dc/elements/1.1/contributor)"
      },
      "dc:language" : {
        "description" : "A language of the resource. Recommended practice is to use either a non-literal value representing a language from a controlled vocabulary or a literal value consisting of a language tag. We shall use for this purpose the IETF RFC 5646 code: [https://www.rfc-editor.org/info/rfc5646."](https://www.rfc-editor.org/info/rfc5646.%22),
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/language](http://purl.org/dc/elements/1.1/language)"
      },
      "dc:publisher" : {
        "description" : "An entity responsible for making the resource available. Examples of a publisher include a person, an organization, or a service. Typically, the name of a publisher should be used to indicate the entity.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/publisher](http://purl.org/dc/elements/1.1/publisher)"
      },
      "dc:source" : {
        "description" : "This property is intended to be used with non-literal values. The described resource may be derived from the related resource in whole or in part. Best practice is to identify the related resource by means of a URI or a string conforming to a formal identification system.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/source](http://purl.org/dc/elements/1.1/source)"
      },
      "dc:relation" : {
        "description" : "A related resource. Recommended practice is to identify the related resource by means of a URI. If this is not possible or feasible, a string conforming to a formal identification system may be provided.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/relation](http://purl.org/dc/elements/1.1/relation)"
      },
      "dc:created" : {
        "description" : "Date of creation of the resource. Recommended practice is to describe the date, date/time, or period of time as recommended for the property Date, of which this is a subproperty. Along this project, IETFs' RFC 3339 shall be used for dates: [https://www.rfc-editor.org/info/rfc3339](https://www.rfc-editor.org/info/rfc3339)",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/date](http://purl.org/dc/elements/1.1/date)"
      },
      "dc:modified" : {
        "description" : "Date on which the resource was changed. Recommended practice is to describe the date, date/time, or period of time as recommended for the property Date, of which this is a subproperty. Along this project, IETFs' RFC 3339 shall be used for dates: [https://www.rfc-editor.org/info/rfc3339](https://www.rfc-editor.org/info/rfc3339)",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/date](http://purl.org/dc/elements/1.1/date)"
      },
      "dc:available" : {
        "description" : "Date that the resource became or will become available. Recommended practice is to describe the date, date/time, or period of time as recommended for the property Date, of which this is a subproperty. Along this project, IETFs' RFC 3339 shall be used for dates: [https://www.rfc-editor.org/info/rfc3339](https://www.rfc-editor.org/info/rfc3339)",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/date](http://purl.org/dc/elements/1.1/date)"
      },
      "dc:subject" : {
        "description" : "A topic of the resource. Recommended practice is to refer to the subject with a URI. If this is not possible or feasible, a literal value that identifies the subject may be provided. Both should preferably refer to a subject in a controlled vocabulary.",
        "type" : "string",
        "enum" : [ "administrative", "amatory", "anthropological", "apologetic", "biographical", "chorographic", "chronisticle", "concise", "descriptive", "educational", "elegiac", "encomiastic", "epic", "ethnographic", "exegetic", "expository", "fictional", "hagiographical", "historiographic", "informative", "legal", "moral", "narrative", "performative", "political", "prescriptive", "technical", "testimonial", "theological" ],
        "conformsto": "[http://purl.org/dc/elements/1.1/subject](http://purl.org/dc/elements/1.1/subject)"
      },
      "dc:format" : {
        "description" : "The file format, physical medium, or dimensions of the resource. Recommended practice is to use a controlled vocabulary where available. For example, for file formats one could use the list of Internet Media Types [MIME]. Any document produced within this project shall be contained by 'json/application' files, as described in the IETFs RFC 8259: [https://www.rfc-editor.org/info/rfc8259."](https://www.rfc-editor.org/info/rfc8259.%22),
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/format](http://purl.org/dc/elements/1.1/format)"
      },
      "dc:extent" : {
        "description" : "The size or duration of the resource. Recommended practice is to specify the file size in megabytes. Because of the small size of the files produced within this project, we shall use bytes instead.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/format](http://purl.org/dc/elements/1.1/format)"
      },
      "dc:rights" : {
        "description" : "Information about rights held in and over the resource. Typically, rights information includes a statement about various property rights associated with the resource, including intellectual property rights.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/rights](http://purl.org/dc/elements/1.1/rights)"
      },
      "dc:license" : {
        "description" : "A legal document giving official permission to do something with the resource. Recommended practice is to identify the license document with a URI. If this is not possible or feasible, a literal value that identifies the license may be provided.",
        "type" : "string",
        "conformsto": "[http://purl.org/dc/elements/1.1/rights](http://purl.org/dc/elements/1.1/rights)"
      }
    }
  },
  "required" : [ "dc:type", "dc:identifier", "dc:bibliographiccitation", "dc:title", "dc:contributor", "dc:language", "dc:publisher", "dc:source", "dc:created", "dc:modified", "dc:format", "dc:extent", "dc:rights", "dc:license" ],
  "additionalProperties" : false
}
```

De este metaesquema se deduce clara e inequívocamente la estructura general que habrá de tener la sección de metadatos que se integrará en todos los documentos `application/json` producidos en el presente proyecto. Si bien podríamos haber utilizado el esquema JSON proporcionado por el proyecto [CSL](https://citationstyles.org/), que puede ser interpretado o sirve de sistema de exportación para multitud de herramientas de software, por lo que su interoperabilidad estaba garantizada, preferimos usar este esquema, diseñado a partir de una simplificación de las especificaciones de la DCMI y de su transformación en JSON.

Para comenzar con la integración de los metadatos descriptivos ya diseñados en cada documento independiente ‒o sus secciones, en el caso de serializaciones‒, todo el conjunto se habrá de integrar, en posición antecedente a cualquier otro elemento o subestructura ‒o en posición inicial, en el caso de secciones‒, dentro del valor matricial de un elemento `"citation"`, como se habrá de especificar en los esquemas correspondientes a las ediciones y serializaciones documentales.

- Dentro del conjunto, se iniciará con un elemento `"dc:type"`, que habŕa de contener, expresado como valor único, el tipo de documento que estemos describiendo, dentro de un rango limitado, como queda descrito en el esquema antecedente: `"article-newspaper"`, `"book"`, `"collection"`, `"dataset"`, `"document"`, `"legislation"`, `"manuscript"`, `"map"`, `"musical_score"`, `"pamphlet"`, `"performance"`, `"regulation"`, `"report"`, `"song"`, `"speech"` y `"treaty"`.
- Se continuará con un elemento `"dc:identifier"`, que integrará tanto el DOI de la publicación concreta como la URL de dicho DOI.
- Después, se expresará, como valor de un elemento `"dc:bibliographiccitation"`, la forma en que el objeto digital descrito habrá de citarse, empleando para ello el formato de citación de [*The Chicago Manual of Style*](https://www.chicagomanualofstyle.org/tools_citationguide.html), en su 17ª edición.
- A esto seguirá un elemento `"dc:description"`, cuya función será la de servir de almacenamiento en su valor al nombre del documento que esté siendo catalogado, sin alteraciones, con su extensión.
- Dos elementos, `"dc:title"` y `"dc:alternative"`, servirán para expresar tanto el título otorgado –es decir, aquel cuya grafía se haya actualizado o el que le haya sido otorgado cuando no lo tuviera– como el título original –preservando su grafía–, además del enlace a la URL de su publicación en el proyecto.
- El personal implicado en la producción de la edición digital tendrá su lugar a continuación, consignando como valor de `"dc:creator"` a la persona que posea la mención de responsabilidad sobre la autoría del original de la obra catalogada, enlazando además a la URL de su artículo de la Wikipedia en español, y como expresión del valor de un elemento `"dc:contributor"` a la persona responsable de la edición dentro del marco del presente proyecto, enlazando a la URL de su página personal o a su usuario de redes sociales de conveniencia.
- El código lingüístico de la edición, es decir, aquel que represente más del 70% de la expresión total en la misma, se habrá de expresar como valor del elemento `"dc:language"`, y aunque no ha sido esta expresión restringida en el esquema –*vid supra*–, lo más probable es que dentro del presente proyecto no se empléen otros valores que no sean `"es-ES"`, `"es-CL"`, `"es-PE"`, `"fr-FR"` y `"en-UK"`.
- A continuación, se consignará la información relativa a las entidades académicas involucradas en este proyecto, que irán debidamente etiquetadas en HTML5 a fin de que, además de expresarse debidamente, queden enlazadas por separado a las URLs de sus respectivos sitios web institucionales, todo el conjunto expresado como valor único de un elemento `"dc:publisher"`.
- Se procederá después, mediante dos elementos distintos, `"dc:source"` y `"dc:relation"`, a consignar la información relativa a la fuente original de la edición: mientras el primero expresará como valor la signatura del original analógico en su repositorio de preservación, enlazando a su ficha catalográfica mediante HTML5, el segundo expresará la signatura –cuando se encuentre diferenciada– de la reprografía digital facsimilar empleada en este presente proyecto, enlazando a la URL del objeto digital concreto.
- Las fechas serán el siguiente paso, expresándose tres: en primer lugar, el elemento `"dc:created"` contendrá como valor la fecha de creación del original; segundo, un elemento `"dc:modified"` servirá para expresar la fecha de finalización de la edición documental o de la serialización en el presente proyecto; por último, `"dc:available"` será el elemento empleado para expresar la fecha de publicación. Todas las fechas en el presente proyecto serán consignadas empleando para ello el estándar de la IETF [RFC 3339](https://www.rfc-editor.org/info/rfc3339).
- En cuanto a la descripción de los contenidos, se ha elegido cuidadosamente, tras una profunda revisión de la documentación fruto de la fase de *Selección*, un conjunto de 30 posibles valores asociables a materias, que se expresarán –cuantas sean necesarias– como valores de una matriz expresada en el elemento `"dc:subject"`. Estos valores posibles son: `"administrative"`, `"amatory"`, `"anthropological"`, `"apologetic"`, `"biographical"`, `"chorographic"`, `"chronisticle"`, `"concise"`, `"descriptive"`, `"educational"`, `"elegiac"`, `"encomiastic"`, `"epic"`, `"ethnographic"`, `"exegetic"`, `"expository"`, `"fictional"`, `"hagiographical"`, `"historiographic"`, `"informative"`, `"legal"`, `"military"`, `"moral"`, `"narrative"`, `"performative"`, `"political"`, `"prescriptive"`, `"technical"`, `"testimonial"` y `"theological"`.
- Dos elementos, `"dc:format"` y `"dc:extent"`, servirán para expresar en sus valores, respectivamente, el tipo MIME del objeto digital que esté siendo catalogado –que siempre seguirá lo establecido en la [RFC 4627](https://www.rfc-editor.org/info/rfc4627) de la IETF– y el tamaño en bytes de dicho objeto digital.
- Por último, se consignará la información legal del objeto digital concreto, información que será constante en todos las ediciones documentales y serializaciones elaborados en el marco de este proyecto. Los elementos `"dc:rights"` y `"dc:license"` servirán a estos efectos, declarando el acceso abierto al objeto digital catalogado, con la adhesión de este proyecto a la [BOAI](https://www.budapestopenaccessinitiative.org/boai-10-translations/spanish), y su pase directo a dominio público, mediante una licencia [Creative Commons *Zero*](https://creativecommons.org/publicdomain/zero/1.0/deed.es).

Veamos ahora, finalmente, el conjunto de metadatos establecido dentro de la estructura general del documento:

```json
{
  "citation" : {
    "dc:type" : [ "article-newspaper", "book", "collection", "dataset", "document", "legislation", "manuscript", "map", "musical_score", "pamphlet", "performance", "regulation", "report", "song", "speech", "treaty" ],
    "dc:identifier" : "<a target='_black' href='URL DEL DOI'>DOI</a>",
    "dc:bibliographiccitation" : "FORMA DE CITAR, EN CMOS 17, EN HTML5",
    "dc:description" : "NOMBRE Y EXTENSIÓN DEL RECURSO DIGITAL",
    "dc:title" : "<a target='_black' href='URL DE PUBLICACIÓN'>TÍTULO OTORGADO</a>",
    "dc:alternative" : "TÍTULO ORIGINAL",
    "dc:creator" : "<a target='_black' href='URL DEL ARTÍCULO'>APELLIDOS, NOMBRE</a>",
    "dc:contributor" : "<a target='_black' href='URL DE LA WEB PERSONAL'>APELLIDOS, NOMBRE</a>",
    "dc:language" : "CÓDIGO LINGÜÍSTICO",
    "dc:publisher" : "<a target='_black' href='https://artesliberales.uai.cl/centros/centro-de-estudios-americanos/'>Universidad Adolfo Ibáñez - Centro de Estudios Americanos</a>, <a target='_black' href='https://artesliberales.uai.cl/'>Universidad Adolfo Ibáñez - Facultad de Artes Liberales</a>, <a target='_black' href='https://ielat.com/'>Universidad de Alcalá - Instituto Universitario de Investigación en Estudios Latinoamericanos</a> y <a target='_black' href='http://cedcs.eu/'>Fundación Centro Europeo para la Difusión de las Ciencias Sociales</a>",
    "dc:source" : "<a target='_black' href='PERMALINK A LA FICHA CATALOGRÁFICA'>SIGNATURA DEL RECURSO FÍSICO</a>",
    "dc:relation" : "<a target='_black' href='PERMALINK A LA REPROGRAFÍA'>SIGNATURA DEL RECURSO DIGITAL</a>",
    "dc:created" : "FECHA DE CREACIÓN/PUBLICACIÓN DEL ORIGINAL",
    "dc:modified" : "FECHA DE CREACIÓN DEL RECURSO DIGITAL",
    "dc:available" : "FECHA DE PUBLICACIÓN",
    "dc:subject" : [ "administrative", "amatory", "anthropological", "apologetic", "biographical", "chorographic", "chronisticle", "concise", "descriptive", "educational", "elegiac", "encomiastic", "epic", "ethnographic", "exegetic", "expository", "fictional", "hagiographical", "historiographic", "informative", "legal", "moral", "narrative", "performative", "political", "prescriptive", "technical", "testimonial", "theological" ],
    "dc:format" : "json/application",
    "dc:extent" : "TAMAÑO EN BYTES",
    "dc:rights" : "Open Access: <a target='_black' href='https://www.budapestopenaccessinitiative.org/boai-10-translations/spanish'>Budapest Open Access Initiative</a>",
    "dc:license" : "Public Domain Dedication: <a target='_black' href='https://creativecommons.org/publicdomain/zero/1.0/deed.es'>Creative Commons Zero 1.0 Universal</a>"
  }.
  …
}
```

# *Referencia*

El presente documento, ***Reglas de Catalogación del Proyecto “Noticias del Viejo Imperio, 1860-1866”***, creado por David Domínguez Herbón y Álvaro Casillas Pérez: es una versión del documento [*Reglas de Catalogación del Proyecto “Avisos de Levante”*](https://avisosdelevante.wordpress.com/proyecto_esp/catalogacion/), creado por David Domínguez Herbón, Ricardo Fabián Chimal Avalos y Gennaro Varriale; es una publicación respaldada por el [Centro de Estudios Americanos](https://artesliberales.uai.cl/centros/centro-de-estudios-americanos/) y la [Facultad de Artes Liberales](https://artesliberales.uai.cl/) de la Universidad Adolfo Ibáñez, el [Instituto Universitario de Investigación en Estudios Latinoamericanos](https://ielat.com/) de la Universidad de Alcalá y el [Centro Europeo para la Difusión de las Ciencias Sociales](http://www.archivodelafrontera.com/), instituciones bajo cuyo auspicio se publica.

Todos los objetos digitales en esta web se publican en el marco del [Proyecto Fondecyt de Iniciación Nº 112000245](https://s3.amazonaws.com/documentos.anid.cl/iniciacion/2020/fallo/NominaProyectosAprobadosIniciacion2020.pdf) “Noticias del Viejo Imperio. La Expedición del Pacífico y la Guerra hispano-sudamericana en los imaginarios geopolíticos de la España liberal (1860-1866)”, financiado por la [Agencia Nacional de Investigación y Desarrollo](https://www.anid.cl/), del [Ministerio de Ciencia, Tecnología, Conocimiento e Innovación](http://www.minciencia.gob.cl), del Gobierno de Chile.

Este proyecto se adhiere a la [Budapest Open Access Initiative](https://www.budapestopenaccessinitiative.org/boai-10-translations/spanish). Todos los objetos digitales de este proyecto se distribuyen bajo una [Licencia Creative Commons *Zero* 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/deed.es).

*Correo webmaster [admin@envi19.cl](mailto:admin@envi19.cl)* · *Versión 1.0  ·  Fecha de creación: 02 de marzo de 2021  ·  Última actualización: 12 de julio de 2021*