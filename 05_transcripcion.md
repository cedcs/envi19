# Transcripción

Este documento técnico, elaborado en el marco del Proyecto “Noticias del Viejo Imperio, 1860-1866”, tiene por objeto facilitar al usuario la labor de transferencia de la información textual contenida en una reprografía facsimilar digital a un soporte digital textual. Se corresponde con la tercera fase, denominada de *Transcripción*, como se puede extraer del documento técnico *Algoritmo de procesos del Proyecto “Noticias del Viejo Imperio, 1860-1866”*.

La labor de transcripción tiene que producir, necesariamente, un objeto técnico concreto, que es en este caso un archivo de texto plano editado en formato Markdown ‒es decir, `plaintext/markdown`‒ que contenga la misma información textual que contiene la reprografía facsimilar digital de origen, producto de la primera fase, de *Selección*. Esta acción técnica ‒tal y como se utiliza el concepto de acción en este proyecto‒ es un trasiego tipológico de la obra escrita que consiste en tomar los documentos de archivo y trasladar las expresiones textuales en ellos contenidas a otro contenedor, a fin de permitir su transformación, mediante el cambio de soporte, en textos extendidos. Para esta acción técnica se han establecido y adoptado ciertas reglas de transcripción, dentro de la tradición paleográfica latina.

Para llevar a cabo esta acción técnica, se ha establecido una serie de reglas, descritas más adelante con mayor detalle, que tienen por objeto guiar y auxiliar al transcriptor en su labor de extraer el texto de las reprografías facsimilares digitales obtenidas en la anterior fase de *Selección*. Aunque la forma de transcripción que se plantea en este documento técnico parte de la tradición paleográfica latina empleada para los textos de diplomática hispánica, las reglas que aquí se proponen difieren de algunas convenciones empleadas, ya que, principalmente, están dirigidas a la elaboración de un documento digital de texto plano en formato Markdown, equivalente al tipo MIME `plaintext/markdown`, que no se visualizará en sí mismo, sino que se verá a través de una plataforma que distinguirá entre la información extraída del documento original y aquella que, en las siguientes fases del algoritmo de procesos, las de *Edición* y *Publicación*, devenga de las etiquetas añadidas al documento.

En atención al punto anterior y a la relación entre la presente y las siguientes fases, es importante distinguir entre las notas de edición y de transcripción, que habrán de elaborarse de acuerdo con el desarrollo de esta fase. Las primeras son anotaciones que se incorporan al cuerpo del texto para que posteriormente puedan visualizarse como parte de la caja de escritura, tal y como se ha venido realizando de forma usual con los criterios de paleografía para textos impresos. En cambio, cada nota de transcripción es la información complementaria y temporal que el transcriptor proporciona al etiquetador en el texto plano para que, en la siguiente fase, sea reemplazada por su forma de etiquetado correspondiente. La primera simplemente incluye los elementos incorporados dentro de un par de corchetes, en tanto que la segunda es una nota que va entre corchetes separada por una coma y que se coloca inmediatamente después del elemento textual referido, como se muestra aquí:

```markdown
[f. 124r]
¶[signo, artículo]
```

Cabe agregar algunos puntos sobre las notas de transcripción:

1. es importante señalar que no se debe dejar bajo ningún concepto un espacio en blanco entre la nota y elemento del texto referido, ya que esto ayudará a evitar errores en las fases posteriores durante las labores de segmentación en fragmentos de información y de semantización y serialización por reestructuración bajo un esquema JSON;
2. se considera recomendable, dado que se parte del empleo forzoso de un esquema de glifos Unicode UTF-8, con un final de línea común a los sistemas Unix, que se utilice como software básico un editor de código que permita, por una parte, establecer ambas condiciones propuestas, y por otra, identificar rápidamente irregularidades en el etiquetado Markdown de forma visual;
3. asimismo se considera aconsejable utilizar un software auxiliar que permita determinar y emplear de forma rápida y sencilla los glifos Unicode necesarios para la compleción de la transcripción;
4. por otra parte, para que la visualización de lo transcrito sea lo más completa posible en cuanto a los glifos representables, y lo más intrínsecamente homogénea, se recomienda encarecidamente la instalación en el sistema operativo en uso de una tipografía que comprenda las expresiones glíficas más extendidas posibles; y, por último,
5. que el contenido señalado dentro de las notas de transcripción, por tratarse de un elemento externo al texto original que señala el transcriptor, sí se apegará a las reglas de ortografía actualmente en uso.

Pasaremos a continuación a explicar, ordenada y detalladamente, las formas que tendrá la transcripción en lo general, así como las eventualidades que se puedan presentar a ella, a partir de las experiencias previas y de las determinaciones tomadas en la preparación de esta documentación técnica.

### 1. Ordenación y división

Ya estén foliados o paginados, los documentos suelen estar ordenados alfanuméricamente para su lectura. Esta ordenación se indicará entre corchetes, respetando la que indique el instrumento de descripción archivística correspondiente en caso de que varias se superpongan. La colocación de la foliación o de la paginación entre corchetes se realizará al inicio de cada folio o página.

La abreviatura a emplear para señalar la foliación será ‘f.’, o ‘ff.’ para su plural, indicando si se trata del recto de la foja o de su vuelto con una ‘r’ o una ‘v’ tras el numeral correspondiente y sin separación de él. En el caso de que el documento esté paginado, la abreviatura empleada será ‘p.’, o ‘pp.’ para su plural, indicándose a continuación exclusivamente el numeral, se encuentre expresado éste en el sistema latino o en el romano, los dos más habituales.

En el caso de encontrarse con páginas o folios vacíos, es decir, que no contengan información textual o expresable textualmente y transferible a medios digitales, este hecho se consignará dentro de los corchetes, mediante el texto ‘vacío’ o ‘vacía’, según sea folio o página, separado de la foliación o paginación mediante una coma.

En el caso improbable, pero posible, de que existan errores de paginación o foliación en el documento original, como la repetición de más de un número de página de forma consecutiva o no, o la ausencia de contabilización de folios intermedios, por poner sólo dos ejemplos comunes, se emplearán soluciones emergentes que partirán del consenso entre los responsables del proyecto y los agentes encargados de la transcripción.

```markdown
[f. 134v]
[ff. 134r-134v]
[ff. 134r y 135r]
[f. 134r, vacío]
```

```markdown
[p. 134]
[pp. 134-135]
[pp. 134 y 136]
[p. 134, vacía]
```

Por supuesto, existen divisiones dentro del texto. Si en la actualidad, en las publicaciones digitales de texto extendido, se consignan las diferencias entre *bloques*, en la época, y especialmente en el sistema escrito, dominaba el sistema paragráfico. Estableciendo, *grosso modo*, un parangón entre ambos sistemas, entre un párrafo –considerando como tal un título, un bloque de texto continuo sin separación de punto y aparte, una cita, una estrofa, una tabla, una nota al pie, etc…– y otro mediará siempre una línea en blanco, de manera que un software intérprete de Markdown pueda representar inequívocamente ambos párrafos como *bloques* diferenciados.

Finalmente, cualquier elemento cuya función sea la de separar secciones del texto será indicado con una línea recta horizontal, misma que se especifica en Markdown con tres guiones sencillos separados entre cada par por un espacio en blanco, colocado el conjunto en una línea independiente. Cuando exista una ornamentación en dicho separador, por supuesto, las reglas a seguir para su expresión serán, además de las aquí indicadas, las relativas a la expresión de figuras, *ut infra*.

### 2. Grafía y puntuación

A pesar de que el corpus documental del presente proyecto, si bien no está integrado por textos con diferentes sistemas de escritura, sí muestra disimilitudes de forma entre sus distintos repertorios gráficos, y a pesar de que emplean diversas lenguas para expresarse, dichos textos emplean en lo general los siguientes signos de escritura, grafemas o grafías: fonogramas, logogramas, determinativos semánticos y signos auxiliares.

- Los *fonogramas* son signos de escritura que representan un fonema, es decir, un sonido articulado propio de un sistema lingüístico o una combinación de estos.
- Los *logogramas*, por otra parte, son grafemas que representan una palabra o un morfema. Aunque no son abundantes estos signos en los sistemas de escritura alfabéticos –como lo son los que conforman el corpus de este proyecto–, su existencia ha sido tratada desde la paleografía como signos especiales, usualmente de abreviación, o bien ha sido desdeñada como notación aritmética, en el caso de los numerales.
- Aunque para la época su forma sea variable y su uso no sea sistemático, los *determinativos semánticos* son grafemas que se emplean en el corpus documental se restringen al uso de tildes que alteran la semántica y, en su caso, la forma de lectura del texto.
- Por su parte, los *signos auxiliares* son grafías que sirven para ordenar y facilitar la expresión de las ideas expuestas sin alterar el significado o la forma de lectura de las palabras. Para el momento de la documentación, encontraremos signos o formas de emplear esos signos que, aunque ya hayan caído en desuso, es importante retomarlos en la transcripción tal y como aparecen en el texto.

De forma general, la inserción de todos estos signos de escritura en el texto plano se puede realizar por medio de la inserción de caracteres Unicode UTF-8 que viene configurada de forma predeterminada en las opciones de teclado e idioma de entrada en los distintos sistemas operativos, sean de acceso libre o restringido. Si alguna grafía o grafema no pudiera introducirse de la forma antedicha, se puede recurrir a la inserción directa en el texto plano por medio de comandos, o mediante la utilización intermedia de una aplicación de software que muestre y permita seleccionar los signos necesarios, como se recomienda al inicio de este apartado.

Se pretende, como se puede deducir de lo antedicho, preservar íntegramente la expresión textual de los documentos seleccionados en la transferencia hacia sus transcripciones, de manera que el texto pueda ser utilizado, no sólo en la presente investigación, o en otra de carácter histórico, sino en una de cualquier disciplina. Mantener la forma literal de las grafías tiene prioridad absoluta en el texto extendido, por lo que la transcripción no realizará ningún cambio sintáctico ni ortográfico ni retórico en la transcripción con respecto del texto original. Se mantendrá la ortografía original del documento aun cuando ésta ya no se use actualmente, puesto que la normalización del etiquetado permitirá obtener resultados apropiados a las pesquisas sobre las distintas formas de escritura de un solo vocablo o sintagma, y la segmentación, serialización y semantización posteriores emplearán distintas formas como subproyecto derivado de este inicial. El uso de mayúsculas y de minúsculas se restringirá a la forma que exhiban en el texto, y cuando su distinción no llegara a ser clara, el transcriptor atenderá a su criterio para utilizar una u otra forma de la grafía. La transcripción, por tanto, se apegará a la forma del texto original.

Por lo general, estas reglas hasta aquí expresadas para la transferencia de información textual gráfica se habrán de aplicar también ante la aparición en el texto de signos ideográficos que, aunque carezcan de valor de lectura, tengan significado. La persona responsable de la labor de transcripción deberá realizar, en cualquier caso, explicitaciones sobre la complejidad de la forma figurativa de los signos incluidos en los textos. Estos signos se indicarán con el texto ‘signo’ entre corchetes, seguido de la expresión textual de su significado, separados ambos elementos, como es norma, por una coma y un espacio. La forma de expresión de dicho valor no se apegará a la forma original de enunciación, sino a la actual, dado que se trata de una nota de edición realizada por el transcriptor. A continuación se muestran cuatro casos significativos:

```markdown
†[signo, fallecido]
¶[signo, artículo]
₧[signo, pesetas]
```

Por supuesto, puede darse el caso de que aparezcan expresiones gráficas que, si bien pueden caer dentro del conjunto de lo expresable, no se corresponda exactamente la expresión gráfica permitida por el sistema Unicode UTF-8 o por la tipografía con lo que el autor o editor pretendía expresar, y que dicha incoherencia sea manifiesta a ojos del agente encargado de la transcripción. Dados esos posibles casos, se discutirá abiertamente su posible solución entre los agentes encargados de la transcripción y los responsables del proyecto.

Cabe agregar que las firmas son signos gráficos cuyo autor ha empleado para validar una información dada previamente. Para señalar su presencia, la palabra ‘rúbrica’ irá entre corchetes en el espacio que ocupe la firma dentro del texto, precedida de la palabra ‘signo’ y de una coma y un espacio, como es costumbre, señalándose, a continuación, ya dentro del texto, la información expresada mediante la rúbrica, es decir, el nombre del firmante.

```markdown
[signo, rúbrica]Luis Hernández i Pinzón
```

En lo tocante a la puntuación original del documento, esta se mantendrá inalterada aún cuando ya no se use actualmente. No se actualizará ningún tipo de acentuación gráfica, por lo que quedará a la pericia de la persona responsable de la transcripción de cada documento concreto distinguir y expresar la presencia de estos signos, especialmente en los manuscritos.

### 3. Abreviaturas

Las diferencias entre la forma de expresar abreviaturas en el período que abarca el presente proyecto –y, por ende, la documentación seleccionada para su transcripción– y la forma que estas tienen actualmente son muy escasas. Por tanto, se ha decidido elidir su notación: las abreviaturas no se señalarán de ninguna manera en el texto, y tampoco serán desarrolladas en forma alguna, sea cual sea su caso.

### 4. Énfasis

Se indicarán las formas enfáticas de expresión –titulación, mayúsculas, cursivas (itálicas u oblicuas), negritas, versales o subrayados–, bien como notas de edición dentro de la transcripción, bien aprovechando la extensión de los conjuntos Unicode, del mismo modo que las formas editoriales de ordenamiento en la caja de texto que sean viables, y otros elementos de referenciación interna o externa, o la presencia de elementos no textuales –*vid infra*–. Es importante señalar que el agente responsable de las labores propias de las siguientes fases de *Edición* y *Publicación* no contará con la versión reprográfica facsimilar digital, objeto técnico producto de la fase de *Selección*, pero que necesariamente habrá de consignar dicha información enfática del texto en su propia labor. Para ello emplearemos, como ya hemos expresado con anterioridad, el conjunto de etiquetas editoriales Markdown, según está expresada su sintaxis en su [espacio de publicación original](https://daringfireball.net/projects/markdown/syntax), y regulada mediante las recomendaciones [RFC 7763](https://tools.ietf.org/html/rfc7763) y [RFC 7764](https://tools.ietf.org/html/rfc7764) de *The Internet Engineering Task Force*. A estos documentos técnicos, y en especial a su primaria definición y descripción, remitiremos en todo caso para aclarar las dudas que pudieran surgir al momento de la transcripción.

Los títulos y encabezamientos de texto o sección se marcarán antecedidos por uno o varios símbolos de número `#` consecutivos, seguidos de un espacio en blanco: un sólo símbolo indica el nivel jerárquico más alto en el esquema de organización del texto, dos símbolos consecutivos indican el segundo nivel, y así consecutivamente hasta el sexto nivel, siendo este el menor de los posibles.

Las formas más comunes de énfasis son las cursivas, las negritas, el subrayado y las versales, también empleadas en títulos y encabezamientos. Los textos en cursivas se marcan flanqueándolos por asteriscos, es decir, colocando uno al inicio y otro al final, sin dejar espacio alguno entre ellos y las palabras de inicio y final del fragmento en cuestión; de manera análoga, para los textos en negritas se emplean dos asteriscos al inicio del fragmento y otros dos al final. Si bien no hay forma de marcar subrayado empleando la versión más sencilla de Markdown, y dado que la recomendación más extendida para ello es emplear una etiqueta HTML que sirva a la renderización del fragmento subrayado, utilizaremos para este caso los signos menor que ‘<’ y mayor que ‘>’ de la misma manera que los asteriscos para los casos antedichos. En cuanto a las versales, ampliamente utilizadas en los impresos del siglo XIX, para su presentación la persona responsable de la transcripción deberá remitirse a las herramientas de visualización de caracteres Unicode ya mencionadas para el caso de los signos, dado que el conjunto tipográfico empleado en el presente proyecto permite mostrarlas sin mayor dificultad que la de su inserción directa.

### 5. Listas y tablas

Siguiendo el mismo principio de emplear un lenguaje de marcado editorial para definir los elementos puramente editoriales, [una lista](https://daringfireball.net/projects/markdown/syntax#list) no numerada se etiquetará separando cada elemento de la misma en una línea independiente, e iniciando dicha línea con un asterisco ‘*’ seguido de un espacio en blanco; una lista numerada se ordenará de la misma manera, pero se iniciará cada línea con el número correspondiente en sentido ordinal ascendente, seguido de un punto y un espacio en blanco.

Por otra parte, aunque no existe forma en la versión básica de Markdown para definir tablas de datos, sí existe y está descrita en otras versiones más avanzadas de Markdown de uso extendido, como lo son [CommonMark](https://commonmark.org/), [GFM](https://github.github.com/gfm/) y [MultiMarkdown](https://fletcherpenney.net/multimarkdown/). La complejidad que puede entrañar para la persona encargada de la transcripción la concreción de una tabla de datos siguiendo esquemas simples como los antedichos queda más allá de lo exigible a su pericia y, en ciertos casos, puede llegar a convertirse en una tarea muy pesada. Es por ello que se ha optado en el presente proyecto por emplear cadenas de datos por fila bajo el formato de valores separados por caracteres (CSV, por sus siglas en inglés), bajo la recomendación [RFC 4180](https://tools.ietf.org/html/rfc4180). De esta manera, se preservará toda la información y se favorecerán tanto su transcripción como su sistematización y su visualización. La persona responsable de la transcripción deberá separar cada elemento por medio del mismo signo, y cada línea de la tabla se organizará en una fila distinta en el documento de texto plano, a semejanza de su ordenamiento en la reprografía facsimilar digital que le sirve de base. A continuación se muestra un ejemplo de presentación de una tabla:

```markdown
"Navío";"Base";"Capitán";"Tripulación"
"La Blanca Aurora";"Valparaíso";"Agustín Cano";"92"
"Arapiles";"Guayaquil";"Hermenegildo Costenla";"108"
```

### 6. Notas, citas y referencias

Una nota, esté su expresión de referencia situada al margen, al pie de la página o al final de la sección o del documento, siempre se colocará al final del texto, dado que es la forma más adecuada a la hora de presentarlas en las ediciones digitales de texto extendido. La expresión gráfica de una nota no dista mucho de sus análogos en los programas procesadores de texto convencionales: para señalarla, respetando siempre su lugar de inserción en el texto original, se transcribirá con el numeral correspondiente a un orden absoluto dentro del documento en sentido ordinal ascendente, antecedido por un acento circunflejo `^` y el conjunto de ambos signos entre corchetes. Al final del documento se podrá colocar una lista ordenada, iniciando cada nota el mismo conjunto antes descrito, incluidos los corchetes, seguido de dos puntos y un espacio en blanco antes de la expresión textual de la nota en cuestión, como se puede comprobar en el siguiente ejemplo:

```markdown
Cuando nos aproximamos a la bocana del puerto[^¹] nos resciviò una salva de los cañones de la fortalessa[^²].

[^¹]: 22 de iunio de 1862.
[^²]: Vallparaisso.
```

La aparición de citas textuales separadas del resto del texto en párrafos independientes se marcará, al inicio de dicho párrafo, con un símbolo mayor que ‘>’ seguido de un espacio en blanco.

Sobre tres casos particulares cabe llamar la atención:

- primeramente, que en los casos en que la edición del texto original exprese la llamada a nota de forma siempre inicial paginalmente, es decir, que cada nueva página comience a numerar las notas desde 1, no se respetará esta notación, siendo sustituida por una notación consecutiva secuencial;
- segundo, que en los casos en que el texto de una nota se exprese en varios párrafos, se respetará esta formación del texto, pero después del primer párrafo se iniciarán los siguientes con una indentación de dos espacios en blanco, a fin de preservar la integridad de dicha nota;
- y, tercero, que en los casos en que se encuentre una llamada a nota dentro de una nota, se respetará la misma estructura y la misma ordenación, tal y como se ha expresado hasta aquí, y no de otra manera.

En cuanto a las referencias a otras obras de manera general, o a documentos seleccionados para su transcripción en el presente proyecto, se podrá realizar una vinculación externa directa desde la misma transcripción a la URI de la descripción de dicho elemento en Zotero. Para ello, la expresión textual en que dicha obra o documento se refiere se colocará entre corchetes y, sin mediar espacio de separación, se seguirá el cierre de dichos corchetes de una pareja de paréntesis, dentro de los cuales se dispondrán la URI de vinculación y, tras un espacio, y entre una pareja de comillas dobles `"`, el valor del campo `[Nombre]` que se otorgara a dicha obra, documento o fragmento de unidad archivística en los *metadatos de archivo* durante la fase de *Catalogación*, como se muestra en el siguiente ejemplo:

```markdown
Durante [aquella sesión del congreso](https://t.me/envi19/34 "ib-ds46-1836-132_146-discusion_sobre_la_independencia_de_america"), se disputó por los liberales la necesidad…
```

### 7. Adiciones, interrupciones y falencias

Las adiciones al texto son todas las anotaciones que se realizan entre las líneas que conforman la caja de texto, o bien al margen por una mano distinta de la autora general del texto, y sólo se consignarán en la transcripción aquellas que hubieran sido realizadas contemporáneamente a la producción del documento. En consecuencia, los sellos, foliaciones e incorporaciones al documento realizadas con posterioridad a su producción original serán excluidos de la transcripción. Para obtener más información histórica acerca del documento, el lector o investigador podrá remitirse al instrumento de descripción archivística correspondiente.

De forma general, las adiciones se transcribirán entre barras diagonales contrapuestas y se considerarán como parte del texto transcrito. Es importante mencionar que el texto que continúa a un fragmento testado dentro de una misma línea no es considerado una adición, sino una corrección (por tanto, no se consigna entre barras).

```markdown
Sòlo \en esta ciudad/ hai dolor.
```

La persona responsable de la transcripción deberá hacer explícitas las condiciones de lectura del documento en los casos en que se presenten ausencias o interrupciones ‒voluntarias o no‒ en el fluir del mismo. Las falencias, es decir, los espacios vacíos de la escritura en que el autor interrumpió voluntariamente el texto, se transcribirán con la palabra ‘falencia’ entre corchetes.

```markdown
por todo aquello se pago la cantidad de [falencia] reales
```

Por otra parte, en aquellas secciones del texto en que el documento, por la razón que sea, haya sido mutilado ‒de manera voluntaria o no‒ , interrumpiendo el flujo del texto, serán señalados con la palabra ‘dañado’ entre corchetes.

```markdown
aqui se dab [dañado] or de su compañía
```

En cuanto a las secciones del texto que, bien por el mal estado del documento, bien por dificultades inherentes a la escritura del mismo, sean ilegibles, serán señalados con la palabra ‘ilegible’ entre corchetes.

```markdown
aqui se dab [ilegible] or de su compañía
```

Finalmente, la ubicación de los fragmentos del texto que hayan sido tachados o testados, bien por corrección, bien por error, se señalará mediante el empleo de un etiquetado Markdown, flanqueando el fragmento testado, cuando este pueda ser legible, por vírgulas, una al inicio y otra al final de dicho fragmento. Cuando sea ilegible, por tanto, se indicará esto *ut supra*, practicando la tachadura de la forma antedicha sobre el señalamiento, como se muestra en el siguiente ejemplo:

```markdown
aqui se dab~~an manos~~ de su compañía
aqui se dab~~[ilegible]~~ de su compañia
```

### 8. Figuras

Por último, la aparición de elementos iconográficos o cartográficos se señalará en el texto mediante una forma similar a la de un enlace en Markdown: iniciando con el símbolo de cierre de par de exclamaciones `!`, y cerrado el resto entre corchetes, se inserta el fragmento de texto `Alt text`; tras el corchete de cierre, se inicia, sin espacio de separación, un ámbito parentético que contendrá, primero, la URL de enlace a dicha imagen, y después, entre comillas simples `"`, el título de la imagen o una breve y concisa descripción de la misma. Dado el caso de que dicha imagen pueda ser publicada, o que se haya producido en el marco del proyecto una versión digital facsimilar por vectorialización, dicha imagen podrá ser publicada y tendrá, por tanto, una dirección URL de almacenamiento público. Dicha dirección podrá ser empleada en la referenciación de manera que se remita a ella directamente desde su lugar de aparición en el texto, antecediendo a su título o descripción dentro de los paréntesis, y separada aquella de esta por un espacio en blanco. Así se muestra en el ejemplo a continuación:

```markdown
![Alt text](https://t.me/envi19/35 "Retrado de Casto Méndez Núñez (1824-1869)")
```

# *Referencia*

El presente documento, ***Reglas de Transcripción del Proyecto “Noticias del Viejo Imperio, 1860-1866”***, creado por David Domínguez Herbón y Álvaro Casillas Pérez, es una versión del documento *[Reglas de Transcripción del Proyecto “Avisos de Levante”](https://avisosdelevante.wordpress.com/proyecto_esp/transcripcion/)*, creado por David Domínguez Herbón, Ricardo Fabián Chimal Avalos y Gennaro Varriale; es una publicación respaldada por el [Centro de Estudios Americanos](https://artesliberales.uai.cl/centros/centro-de-estudios-americanos/) y la [Facultad de Artes Liberales](https://artesliberales.uai.cl/) de la Universidad Adolfo Ibáñez, el [Instituto Universitario de Investigación en Estudios Latinoamericanos](https://ielat.com/) de la Universidad de Alcalá y el [Centro Europeo para la Difusión de las Ciencias Sociales](http://www.archivodelafrontera.com/), instituciones bajo cuyo auspicio se publica.

Todos los objetos digitales en esta web se publican en el marco del [Proyecto Fondecyt de Iniciación Nº 112000245](https://s3.amazonaws.com/documentos.anid.cl/iniciacion/2020/fallo/NominaProyectosAprobadosIniciacion2020.pdf) “Noticias del Viejo Imperio. La Expedición del Pacífico y la Guerra hispano-sudamericana en los imaginarios geopolíticos de la España liberal (1860-1866)”, financiado por la [Agencia Nacional de Investigación y Desarrollo](https://www.anid.cl/), del [Ministerio de Ciencia, Tecnología, Conocimiento e Innovación](http://www.minciencia.gob.cl), del Gobierno de Chile.

Este proyecto se adhiere a la [Budapest Open Access Initiative](https://www.budapestopenaccessinitiative.org/boai-10-translations/spanish). Todos los objetos digitales de este proyecto se distribuyen bajo una [Licencia Creative Commons *Zero* 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/deed.es).

*Correo webmaster [admin@envi19.cl](mailto:admin@envi19.cl)* · *Versión 1.0  ·  Fecha de creación: 02 de marzo de 2021  ·  Última actualización: 20 de junio de 2021*