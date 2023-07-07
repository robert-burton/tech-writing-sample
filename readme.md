# Proyecto de divulgación científica: Cultura Solar

Este proyecto consiste en un **sitio web** que tiene como propósito la divulgación de información y material de interés, relacionado con los **eclipses solares** que se pronostica sucedan en octubre 2023 y abril 2024.

El sitio se compone principalmente de los siguientes elementos:

- **Artículos** catalogados en diferentes secciones o géneros (noticias, entrevistas, etc.).
- **Mapas interactivos**, donde se despliega información sobre los eclipses de manera gráfica.
- Repositorios de **fotos y videos**, tomados de las redes sociales de Cultura Solar.

# Estructura general del sitio

A continuación se muestra la estructura del sitio web, a manera de árbol:

- **Página principal (index.html)**: actualmente despliega una muestra de artículos hosteados e información sobre el Departamento de Astronomía de la FCFM.
	 - **Eventos**: apartado para información sobre los eclipses y otros eventos astronómicos, así como eventos organizados por el Departamento.
    	 - **Eclipses (eventos.html)**: se muestran cuentas regresivas para las fechas de inicio de los eclipses de 2023 y 2024.
        	 - **Eclipse 2023 (map2023.html)**: mapa interactivo con información del eclipse solar de 2023.
        	 - **Eclipse 2024 (map2024.html)**: similar al anterior, con información del eclipse de 2024.
      	 - **Efemérides astronómicas**: pendiente por crear.
      	 - **Próximos eventos**: pendiente por crear.
	 - **Artículos**: el contenido producido por los redactores se enlista en las siguientes páginas de acuerdo, según su sección correspondiente.
    	 - **Noticias y divulgación (Noticias.html)**
    	 - **Ciencia y tecnología (sabias-que.html)**
    	 - **Artes y humanidades (pendiente)**
    	 - **Entrevistas (entrevistas.html)**
    	 - **Historias y leyendas (historias.html)**
	 - **Multimedia**: repositorios de contenido gráfico.
    	 - **Galería de fotos (fotos.html)**: se despliegua un carrusel con publicaciones de la cuenta de instagram de Cultura Solar.
    	 - **Videos (videos.html)**: similar al anterior, con videos embebidos de la cuenta de Youtube de Cultura Solar.
    	 - **Material didáctico**: pendiente por crear.

# Estructura del proyecto

## Lenguajes utilizados

Debido a limitaciones relacionadas al plan de hosting por el que se paga a la fecha para hospedar el sitio web, se utilizan las siguientes herramientas para el desarrollo de este:
- **HTML**.
- **Javascript puro**, sin entornos como Node.js ni frameworks como React, Angular, etc; se puede llamar a librerías vía CDN, pero hay que tener cuidado con el código que se vaya a hospedar en nuestro servidor.
- **CSS**, para definir los estilos de las páginas.
- Archivos **JSON** para almacenar el contenido de los artículos, así como los datos que se llaman para mostrarse en los mapas interactivos.

## Directorios de interés

Ahora se describen los directorios relevantes que componen al repositorio del proyecto, tomando a /PaginaWeb como directorio raíz:

- **/PaginaWeb**: almacena los archivos **HTML** utilizados; algunos de estos han sido descontinuados y no pueden accederse en el sitio por medio de ligas, pero se han preservado por si se ocupan.
  - **/assets**: aquí se guardan las **imágenes** utilizadas por el sitio en la página de inicio y los artículos, así como la carpeta los archivos JSON.
    - **assets/data**: aquí se encuentran los archivos **JSON**, que se utilizan para guardar el texto de los **artículos** y para almacenar los datos son llamados por los **mapas**.
  - **/css**: almacena los archivos **CSS** que definen los estilos de las páginas; algunos de estos son compartidos por diferentes páginas.
  - **/js**: aquí guardamos los **scripts** de JS que son llamados por las páginas HTML.

Cualquier directorio no mencionado en esta lista no es usado en el día a día del desarrollo y puede ignorarse tranquilamente.

# Cómo actualizar artículos

Una de las actividades de desarrollo más comunes en este proyecto es la actualización del contenido escrito de la página, para lo cual se sigue el siguiente proceso:

## 1. Copiar las imágenes asociadas al artículo a la carpeta /assets

Estas se se envían a los desarrolladores junto con la redacción de los artículos que se van a subir.

## 2. Agregar la información del artículo al archivo JSON correspondiente
   
Cada sección cuenta con su propio JSON, pero tienen una estructura similar. Todos son esencialmente **arreglos** que contienen objetos, donde **cada objeto representa un artículo**.

Los valores contenidos en estos objetos corresponden a los diferentes datos del artículo (título, fecha, autor, cuerpo del texto <sup>*</sup>, imágenes utilizadas <sup>†</sup>, etc.)

Entonces, el agregar un artículo nuevo al JSON consiste solo en agregar un nuevo objeto al arreglo con los valores necesarios, y llenar los valores con la información correspondiente.

\* *Nótese que el cuerpo del texto, que corresponde al valor de "parrafos" en estos archivos, es en sí un **arreglo**, cuyos elementos son cadenas y **cada cadena corresponde a un párrafo** de redacción.*

† *Existen 3 campos en los que se puede agregar una imagen:*
- ***imagen, imagen2**: imágenes que aparecen en el cuerpo del texto.*
- ***imagenb**: imagen de fondo para la página del artículo.*

## 3. Se edita la página HTML de enlistado que corresponda a la sección del artículo

Las limitaciones en el hosting del proyecto nos obligan a trabajar con **páginas HTML estáticas**, por lo que estas deben **editarse manualmente** para que se muestre la tarjeta del artículo nuevo y se pueda ingresar a este por medio de una liga.

El código que corresponde a estas tarjetas se encuentra comentado en los HTML que lo usan, se puede copiar y pegar para agregar la tarjeta nueva, solo con **cuidado de actualzar la línea con la etiqueta \<a>**, de manera que los identificadores *"N-id=i"* (donde *i* denota el número de artículo, empezando desde cero) vayan incrementando en uno. También debe cuidarse que las etiquetas HTML llamen al título, subtítulo e imagen correctos.

**Nota: las tarjetas de los artículos se ordenan de más reciente a menos reciente.**

# Sobre las páginas de "Detalle"

Los archivos HTML cuyo nombre comienza con "Detalle" son los encargados de visualizar un artículo en concreto y existe uno por cada sección, en caso los artículos de esta requieran un formato en particular, de manera que pueda editarse sin afectar la presentación de otros artículos de diferente género.

| Sección                | Página de visualización  |
|------------------------|--------------------------|
| Noticias y divulgación | Detalle.html             |
| Ciencia y tecnología   | Detalle-sabias-que.html  |
| Artes y humanidades    | Detalle-artes.html       |
| Entrevistas            | Detalle-entrevistas.html |
| Historia y leyendas    | Detalle-historias.html   |

Supongamos, por ejemplo, que queremos leer el artículo *La hora mágica de la fotografía*, que se encuentra en la sección de Artes y humanidades. Para esto ingresamos primero a la página de esta sección, en https://culturasolar.org/artes.html.

Una vez ahí, veremos la tarjeta que corresponde a este artículo y un enlace llamado *"Ver más..."*, que nos redirige a al URL https://culturasolar.org/Detalle-artes.html?N-id=0. Hay dos observaciones importantes que hacer aquí:

1. La página que va a cargarse corresponde al archivo HTML de *Detalle-artes.html*.
2. La dirección contiene la cadena de consulta *?N-id=0*, que nos indica que se la página de *Detalle-artes.html* se va a cargar mostrando el contenido que corresponde al elemento cero del archivo *artes.json*.

Cuando en un futuro se agregue un nuevo artículo a esta sección, la manera en que se enlazará a este será por medio del mismo HTML, pero con el contador *N-id* incrementado en uno. De manera que tendremos el URL https://culturasolar.org/Detalle-artes.html?N-id=1.


# Sobre las fotos y videos

Las páginas de *fotos.html* y *videos.html* utilizan un carrusel en el cual se agregan los elementos por mostrar, que en este caso se toman ya sea de la cuenta Instagram o de Youtube de Cultura Solar. Cabe mencionar que, *debido a la naturaleza estática del sitio*, es necesario actualizar el contenido de estos **manualmente**, accediendo a los enlaces que se encuentran en el footer y de ahí tomando la información necesaria de la publicación o video que se quiera embeber.

# Sobre los mapas

El desarrollo de los mapas interactivos se considera hasta la fecha como concluido, pero se presenta una explicación rápida en caso de que necesite modificarse.

El propósito de los mapas es visualizar la trayectoria y magnitud de los eclipses pronosticados en México, incluyendo información específica sobre las condiciones del eclipse en diferentes ciudades del país (capitales de estados y otros puntos de interés).

Los mapas son visualizados por las páginas *map2023.html* y *map2024.html*. Utilizan la librería *Leaflet.js* de Javascript, que es llamada por medio de CDN. Debido a esto, el código correspondiente al script del mapa se incluye en el mismo HTML, sin hacer uso de un archivo *.js* aparte<sup>†</sup>.

La forma en que estos funcionan es llamando a información de sus respectivos archivos JSON:

1. ***datos2023.geojson* y *datos2024.geojson***: contienen la información de la trayectoria que sigue cada eclipse (*curvas de igual magnitud*). Esta fue obtenida de datos de la NASA y convertida a un formato legible para Leaflet; no debería haber necesidad de editar estos, pero en caso de requerirse, se puede utilizar un editor de archivos GeoJSON como https://geojson.io.
2. ***ciudades2023.json* y *ciudades2024.json***: contienen información sobre las condiciones del eclipse en ciudades específicas del país, como magnitud del eclipse, horas de inicio y final, etc. Estos datos fueron tomados de los mapas encontrados en https://www.timeanddate.com/eclipse/map/2023-october-14 y https://www.timeanddate.com/eclipse/map/2024-april-8; salvo que se indique realizarse alguna corrección, no hace falta modificarse.

La cuenta de Github del Departamento cuenta también con otro repositorio, https://github.com/DepAstroFCFM/DepAstroFCFM.github.io, en el que se encuentra una versión "widget" parcialmente terminada, en caso de que se requieran mapas embebibles para otros proyectos. Esta versión se encuentra hosteada por Github en https://depastrofcfm.github.io/ *.


† *La carpeta */js* contiene un script llamado *DESC-map-ol.js*, que corresponde a una implementación pasada del mapa, utilizando Node.js. Fue descontinuada debido a las limitaciones de hosting antes mencionadas.*

\* *Actualmente este widget carga únicamente los datos que corresponden al eclipse de 2023. Si quisiera hacerse posible visualizar el eclipse de 2024 en la misma página, se podría añadir un toggle al archivo index.html y programar la lógica necesaria para que, dependiendo del estado del toggle, se cargue la información de uno u otro eclipse.*

# Sobre la carpeta /css/originales

Debido a la deuda técnica acumulada en los archivos CSS, se decidió hacer uso de herramientas automatizadas para eliminar el contenido no utilizado en estas, que se espera los haga más legibles. En caso de que se requiriera consultar o restaurar los archivos originales, se han movido al directorio antes mencionado.