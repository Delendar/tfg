<!-- markdownlint-configure-file { "sibling_only": true } -->
# Diseño?

## Conceptos

### Puntos de venta

En este documento se hará referencia a puntos de venta por los siguientes términos o similar concepción pero no limitados a:

- Punto de venta
- Supermercados: ya que la conceptualización de la plataforma no esencialmente se restringe a supermercados, su rango de desarrollo inicial sí está definido dentro del concepto de uso sobre un supermercado.
- Tiendas
- Ubicación de venta

Una aclaración conceptual sobre los puntos de venta y sus tipos. En el funcionamiento del sistema no necesariamente requiere diferenciación en la estructura de datos:

1. Puntos de venta compatibles con el sistema de escaneo de precios o puntos de venta compatibles del sistema.
   1. Hace referencia a los puntos de venta (i.e. supermercados Gadis, Carrefour...) para los que el sistema implementa escaneo de precios.
2. Puntos de venta accesibles.
   1. Hace referencia a toda ubicación identificable e identificada como punto de interés mediante la API de Google Maps. I.e. supermercados que son puntos de interés en Google Maps pero para los que el sistema no tiene implementado un escaneo de precios.
3. Puntos de venta personalizados.
   1. Hacen referencia a todas las ubicaciones identificables mediante la API de Google Maps pero no identificada como punto de interés.

Como son terminos conceptuales no son excluyentes:

- Un punto de venta compatible, es decir, que tenga escaneo de precios podría ser un punto de venta accesible (i.e. el sistema de web-scraping está implementado para Gadis y Gadis es un punto de interés en Google Maps)
- Incluso un punto de venta personalizado podría ser considerado accesible y compatible. Ejemplo: un supermercado Gadis, del cual el sistema tiene escaneo de precios podría ser percibido por el usuario como un punto de venta personalizado ya que, por la razón que sea, temporalmente ese supermercado Gadis no es un punto de interés en Google Maps.

### Plano

En este documento se hará referencia a un plano por los siguientes términos:

- Plano
- Plano de punto de venta
- Plano de supermercado
- Plano de distribución

Un plano es un esquema visual creado por los usuarios de la plataforma mediante, inicialmente, las herramientas de interfaz de la plataforma para que esquematiza la estructura interna de la ubicación de los productos dentro de un punto de venta. Esto es en principio, en el caso de un supermercado, la entrada, los pasillos, las cajas de pago y las estanterias (zonas donde están los productos ubicados).

#### Vinculación

La vinculación de un plano se define por la creación de una relación entre el propio "plano" y el "punto de venta" que esquematiza. Para la vinculación se hará uso de preferiblemente puntos de venta identificados en Google Maps, como por ejemplo supermercados, o en su defecto si no se hallan identificados, coordenadas aproximadas.

Ejemplo: si un plano hace referencia al supermercado Carrefour de la Avenida Alfonso Molina, la vinculación se entiende como el hecho de relacionar dicho plano con el edificio real mediante uso de Google Maps para su identificación.

## Funcionalidades de usuario {#funcionalidades-usuario}

### Cuenta {#funcionalidades-usuario-cuenta}

`Registro`: registrar un nuevo usuario en el sistema.
`Inicio de sesión`: iniciar sesión con un usuario existente en el sistema.
`Acceder a datos de perfil`: visualizar los datos de un usuario perteneciente al sistema. Nombre, correo...
`Modificar contraseña`: cambio de contraseña
`Visualizar puntos de venta compatibles del sistema`: permite al usuario ver las opciones existentes y compatibles del sistema con escaneo de precios.
  i.e. Gadis, Carrefour, Mercadona...
`Visualizar puntos de venta suscritos por el usuario`: permite al usuario ver las opciones de puntos de venta a las que está suscrito para el escaneo de precios.
`Suscribirse a un punto de venta disponible`: permitir al usuario suscribirse a 0+ opciones disponibles y compatibles del sistema con escaneo de precios.
`Desuscribirse de un punto de venta`: permitir al usuario inutilizar la suscripción previa a un punto de venta.

### Planos {#funcionalidades-usuario-planos}

`Acceso a los planos del usuario`: acceder a la lista de los planos guardados, tanto los creados como los importados de otros usuarios.
`Creación de un nuevo plano`: acceder a una interfaz que permita la creación de un nuevo plano.
  Ver: W.I.P [Planos]
`Subida al repositorio de un plano creado por el usuario`: permitir al usuario la subida al sistema un plano creado por el para que sea accesible por otros usuarios.
  Será necesaria la vinculación de ese plano con una ubicación real, sea preferiblemente de un punto de venta existente o coordenadas en su defecto (Google Maps). Ver [`Vincular plano`]
`Vincular plano`: permitir al usuario vincular un plano creado con una ubicación que haga referncia a un punto de venta o coordenadas.
`Borrado de un plano`: borrar un plano de la biblioteca de planos del usuario.
  PENDIENTE: GESTION DE UN PLANO BORRADO POR EL USUARIO - SE ELIMINA DEL SISTEMA?
`Acceso a planos disponibles subidos por otros usuarios`: permitir al usuario, mediante una interfaz, ver los planos accesibles ofrecidos por el sistema y subidos por usuarios del mismo.
`Interfaz importar nuevo plano`: permitir al usuario importar a su biblioteca personal un plano subido por otro usuario.

### Listas de la compra {#funcionalidades-usuario-listas}

`Crear una lista de la compra`: permitir al usuario crear listas de la compra.
`Acceder a lista de la compra`: permitir al usuario acceder y modificar listas de la compra.
Modificar lista de la compra: permitir al usuario añadir, borrar y modificar los productos de una lista de la compra originalmente vacía. Las listas tendrán un corportamiento de `Checklist`, los productos pueden estar marcados o no. Una lista de la compra tendrá, de forma visual, originalmente una sola lista vacía a la que se pueden añadir productos pero a la hora de marcar un producto este no será eliminado sino que se moverá a otra lista, la cual de forma visual será consecutiva a la lista de productos no marcados en caso de querer desmarcarlos.
  `Añadir producto`: se añadirá un nuevo producto vacío con entrada para escribir el nombre del producto.
  `Borrar producto`
  `Modificar producto`: se podrá modificar el nombre del producto.
  `Marcar producto`
  `Desmarcar producto`
`Borrar una lista de la compra`: permitir al usuario borrar una lista de la compra, y todos sus productos, creada por él mismo.
`Escanear precios de una lista de la compra en relación a los puntos de venta suscritos por el usuario`: permitir al usuario observar una comparativa que le ofrezca los precios más baratos sobre cada producto de una lista de la compra y el punto de venta que ofrece el mejor precio.
`Crear listas de la compra con los productos más baratos encontrados según su punto de venta`: permitir al usuario, una vez se ha realizado el escaneo de precios, si quiere crear nuevas listas de la compra en base a los más baratos y el precio de compra.
  Ejemplo: una lista de la compra escaneada por un usuario suscrito a Gadis y Carrefour permitirá al usuario automatizar la creación de dos listas distintas "Nombre_Lista_Compra(Gadis)" y "Nombre_Lista_Compra(Carrefour)" con los productos de menor precio de la lista de la compra original.
`Sugerir recetas`: permitir al usuario la opción de hacer uso de una IA que le ofrezca, en función de los productos de una lista de la compra, recetas de cocina que incluyan total o parcialmente los productos de una lista de la compra.
`Recomendación de productos`: ofrecer al usuario mediante un sistema recomendador productos que otros usuarios hayan comprado en listas de la compra similares.
`Vincular lista de la compra a un plano de supermercado`: permitir al usuario relacionar una lista de la compra con un plano de la librería del usuario.

### Relacion planos-listas {#funcionalidades-usuario-listas}

`Mostrar ubicación de la compra`: permitir al usuario visualizar una modificación estética del plano vinculado a una lista de la compra en el que se resaltan las zonas donde se encuentran ubicados los productos.
`Enrutar compra`: permitir al usuario visualizar una modificación estética del plano vinculado a una lista de la compra en la que se resalta el camino a realizar por los pasillos del supermercado para la obtención de los productos de la lista.

Las funcionalidades de los usuarios registrados serán todas las descritas en los apartados anteriores.

Las funcionalidades de los usuarios no registrados serán:

- Registrarse.

Sistema:

- Implementación de IA para sugerencia de recetas.
- Recomendador de productos.
- Algoritmo web-scraping para por lo menos 2 catálogos de productos de puntos de venta diferentes.
- Interfaz de creación de planos, interfaz de dibujo de planos.
- Conversión de planos a grafos para optimización de rutas.

## Funcionalidades internas {#funcionalidades-sistema}

En este apartado se explicará la aproximación interna del sistema para el correcto desarrollo de las funcionalidades del usuario.

### Datos de usuario

Registro, inicio de sesión, perfil y datos será un sistema estándar de gestión de usuarios.

### Escaneo de precios

Mediante Web-Scraping el sistema debe de ser capaz de sacar información sobre productos y su precio de los catálogos pertinentes de los puntos de ventas compatibles. Inicialmente catálogos de sus portales web.

### Puntos de venta

Debido a que el sistema ha de implementar funcionalidades de escaneo de precios y estas en un principio se llevarán a cabo mediante web-scraping de portales web de supermercados
`Visualizar puntos de venta compatibles del sistema`
  Es funcionalidad necesaria que el sistema ofrezca información de los posibles puntos de venta de los que el sistema tiene integrado un escaneo de precios, el cual será hecho por web-scraping.

`Suscribirse a un punto de venta disponible`
  El sistema debe de guardar registro de los puntos de venta compatibles con el sistema que el usuario está interesado en que se escaneen siendo estos un subconjunto de los puntos de venta compatibles con el sistema. De esta forma el sistema sabrá qué información deberá de ofrecer al usuario de la obtenida mediante el escaneo de precios.

`Visualizar puntos de venta suscritos por el usuario`
  El sistema debe ofrecerle una interfaz al usuario que le permita ver qué suscripciones tiene a puntos de ventas compatibles con el sistema.

`Desuscribirse de un punto de venta`
  El sistema debe de permitir al usuario eliminar una suscripción para que así permitirle el optimizar precios según los puntos de venta que le convengan.

## Funcionalidades de usuario - prototipo de secuencia

`[Registrarse] > nombre de usuario + email + contraseña > fallo:error | correcto:sesión iniciada`
`[Iniciar sesión] > email + contraseña > correcto:sesión iniciada | fallo:error`
`[Foto de perfil] > pantalla de datos de usuario`
`[Modificar contraseña] > contraseña antigua + contraseña nueva + repetir contraseña nueva > correcto:contraseña cambiada | fallo:error`
`[Botón de librería en el menú] > pantalla de librería de planos`
`Lista de planos añadidos a la librería (creados + importados) + [Crear nuevo plano] + [Importar nuevo plano]`
`[Vincular plano] > Widget Google Maps + Seleccionar el punto de venta deseado > [Vincular]`
`Pantalla de librería de planos > [Importar nuevo plano] > Widget Google Maps + Seleccionar el punto de venta deseado > Pantalla de lista de planos disponibles`
`Lista con elementos: nombre de la ubicación + usuario autor del plano + [Importar plano]`
`[Botón de compra en el menú] > pantalla de lista de la compra`

## Estructura de datos

### Planos de distribución portables {#planos-dto}

#### Descripción {#planos-descripcion}

Un plano de distribución se define como una semejanza esquemática de la distribución de productos de un supermercado con el objetivo de mostrar de forma visual la localización de productos. Un plano deberá de distinguir entre las principales secciones lógicas que se entiende que existen en un supermercado. A priori estas secciones son:

1. Entrada: entrada a la zona de compras.
2. Pasillo: espacio físico por el cual andar y comunicar las zonas en las que se exponen productos a los clientes.
3. Zona de productos: espacio en el cual se exponen productos a los clientes para que realicen la compra. Se incluyen: estanterías de productos, zonas bajas, verdulería, carnicería, neveras, congelados, etc.
4. No transitable: espacio que referencia una zona física por la que no se puede pasar. Bien para usar para límites, obras, inaccesible, etc.
5. Vacío: indica que no hay que representar nada en esa ubicación.
6. Zona de cobro*: la zona física de cajas para pagar y salir.
7. Baños*: descriptivo.

\*: no se sabe si serán implementadas

#### Características {#planos-caracteristicas}

Un plano de distribución para tener un formato y forma correcta debe de cumplir lo siguiente:

1. Portabilidad: debe de ser portable para permitir facilidad a la hora de crear, importar e exportar estos planos de distribución entre usuarios (i.e. formato JSON).
2. Dividido cuadrículas aunque no necesariamente, es decir, pueden ser 1x1, 1x3, 3x2 o lo que es lo mismo NxM.
3. Cada cuadrícula debera de distinguirse entre las secciones previamente descritas y ser exclusivas mutuamente: entrada, pasillo, zona de productos, no transitable, vacío, zona de cobro, baños.
4. La entrada funciona como un pasillo, simplemente es para visualizarla de una forma rápida en el esquema.
5. Todo pasillo debe de estar conectado a otro o bien la entrada.
6. Toda zona de productos debe de ser accesible mediante un pasillo, es decir, debe estar adyacente a un pasillo.
7. Toda zona de cobro debe de ser accesible mediante un pasillo, es decir, debe estar adyacente a un pasillo.
8. Todo baño debe de ser accesible mediante un pasillo, es decir, debe de estar adyacente a un pasillo.
9. Las zonas [no transitables] y/o [vacías] no tienen restricciones mas allá de que deben de ser exclusivas con otros tipos.
10. Una zona de productos debe de ser capaz de almacenar texto que permita identificar qué productos tiene (i.e. zanahorias, pollo, huevos, o más genérico, cereales, bebidas, bollería).

#### Estandarización {#planos-estandarizacion}

Para el dibujado de planos de distribución se hará uso de la librería de JavaScript Gridstack. Analizando el uso visual de la librería mediante sus demos será intrinsecamente necesario que estos mapas tenga una distribución cuadrada o rectangular en su totalidad dentro de la cual el comportamiento dentro de esta es como el de una cuadrícula permitiendo crear, visualizar, mover o borrar elementos con formas rectangulares.

Los elementos de la cuadrícula tienen cuatro valores clave:

1. *gs-w*: indica en valor numérico las unidades que un elemento individual en la cuadrícula crece en horizontal, dirección derecha.
2. *gs-h*: indica en valor numérico las unidades que un elemento indidual en la cuadrícula crece en vertical, dirección abajo.
3. *gs-x*: indica en valor numérico la posición inicial del elemento más pequeño posible (1x1) en la cuadrícula en el eje horizontal.
4. *gs-y*: indica en valor numérico la posición inicial del elemento más pequeño posible (1x1) en la cuadrícula en el eje vertical.

Por lo tanto a la hora de elaborar la estructura de datos para la transferencia de planos de distribución entre usuarios todos los valores anteriores deben de estar presentes. Tantos los descritos en esta sección como los necesarios para cumplir los requisitos de características de la sección anterior de este documento.

#### Estructura DTO {#planos-estructura}

Para cumplir los anteriores requisitos se debe conseguir una estructura para el formato que sea sólida. Entonces, la estructura de formato será en matriz (atributos 'posx' y 'posy' para saber desde qué posición del esquema crecen), su anchura y altura, dirección derecha y abajo (atributos 'width' y 'height' para saber cuánto crece la sección y hacia donde), con cada valor de esta un objeto (objeto JSON), que identifice que tipo de sección (atritbuto 'id') y que permita añadir productos en caso de que sea una zona de productos (atributo de valor vector 'products' en caso de que el identificador sea válido para zona de productos).

Valoramos entonces el objeto JSON como:

- id: atributo de valor numérico, por velocidad de computación, que sirve para identificar el tipo de sección del esquema con los siguientes valores.
  - 0: vacio
  - 1: entrada
  - 2: pasillo
  - 3: zona de producto
  - 4: no transitable
  - 5: zona de cobro
  - 6: baños
- posx: atributo de valor numérico que sirve para identificar la posición de la sección en la matriz, en este caso el valor N de la matriz NxM.
- posy: atributo de valor numérico que sirve para identificar la posición de la sección en la matriz, en este caso el valor M de la matriz NxM.
- width: número de unidades que la sección crece hacia la derecha.
- height: número de unidades que la sección crece hacia abajo.
- products: atributo de valor vector de texto que sirve para listar los alimentos, productos, objetos encontrados en una sección 02.

Un ejemplo de objeto sería:

```JSON
[{
  "id": 0,
  "posx": 0,
  "posy": 0,
  "width": 1,
  "height": 1
}]

[{
  "id": 3,
  "posx": 1,
  "posy": 1,
  "width": 1,
  "height": 1,
  "products":["carne", "pollo"]
}]
```

Un ejemplo de un mapa sería:

```JSON
[{
  "id": 1,
  "posx": 0,
  "posy": 0,
  "width": 1,
  "height": 1
},
{
  "id": 2,
  "posx": 0,
  "posy": 1,
  "width": 1,
  "height": 1
},
{
  "id": 0,
  "posx": 0,
  "posy": 1,
  "width": 1,
  "height": 1
},
{
  "id": 3,
  "posx": 1,
  "posy": 1,
  "width": 2,
  "height": 3,
  "products":["carne", "pollo"]
}]
```

#### Validación de la estructura de datos DTO {#planos-validacion}

Se debe de cumplir lo siguiente a la hora de dibujar o guardar un plano de distribución. Aunque no necesariamente debe de ser erróneo en caso de que no se cumplan todos los puntos gracias a la flexibilidad del formato JSON. Aún así deben de verificarse el cumplimiento de los siguientes requisitos desde las herramientas proporcionadas por la plataforma. Estos hacen referencia a los elementos rectangulares de el plano, es decir, los objetos de ejemplo descritos en la sección [Estructura](#planos-estructura):

- En todo elemento (objeto JSON) deben de existir tanto los atributos `id`, `posx`, `posy`, `width`, `height`.
- En todo elemento (objeto JSON), el atributo `id` debe no ser distinto de los posibles identificados en la sección de [Estructura](#planos-estructura).
- En todo elemento (objeto JSON), los atributos `posx` y `posy` deben de ser mayor que cero.
- Todo elemento (objeto JSON), debe de tener unos valores de `posx` y `posy` distintos a cualquier otro elemento y inclusive a su superficie, esto es que la posición no debe ser tampoco una que ya cubre otro elemento. Considerando la superficie del elemento en el esquema como:
  - Unidades de longitud de un elemento A, por ende las cuadrículas que ocupa en dirección horizontal se calculan como todos los valores en el rango `[posx, posx+width]`
  - Unidades de altura de un elemento A, por ende las cuadrículas que ocupa en dirección vertical se calculan como todos los valores en el rango `[posy, posy+height]`
- Todo elemento con identificador equivalente a 'Zona de productos' descrito en las [características](#planos-caracteristicas) y asignado en [estructura](#planos-estructura) deberá de incluir, aún con lista vacía, el atributo `products`.

#### Almacenamiento {#planos-almacenamiento}

Se almacenarán en base de datos como formato texto (varchar, text) o JSON nativo si está disponible.

### Base de datos persistente {#bbdd}

#### Datos de usuario {#bbdd-usuario}

Datos planos:

- email: *identificador de cuenta único*
- nombre de usuario
- contraseña: *herramienta de inicio de sesión. Encriptada en la base de datos.*

#### Listas de la compra {#bbdd-listas}

- id único de lista de la compra: `PK`
- id usuario creador de la lista de la compra: `FK -> Usuario`
- producto perteneciente a la lista de la compra: 

#### Planos de distribución {#bbdd-planos}

- id único de plano de distribución: `PK`
- id usuario autor del plano de distribución: `FK -> Usuario`
- id de Google Maps de punto de venta físico vinculado al plano: `puede ser null`
- plano de distribución en formato JSON: `varchar, text, JSON nativo`

#### Productos {#bbdd-productos}

Todavía a valorar si se implementa. Habría que importar una gran cantidad de datos no muy voluminosos para rellenar la base de datos previamente.

- id único de producto: `PK`
- nombre de producto: `text`

#### Estadísticas de compra {#bbdd-estadisticas}

Normalizar posibles datos estadísticos a guardar de un usuario posteriormente.

- id único de tipo de dato: `PK`
- nombre del tipo de dato: `text`

#### Frecuencia de compra de productos por usuario {#bbdd-frecuencia-compra}

Esta tabla servirá para almacenar datos sobre las compras de usuarios para a posteriori conseguir sacar información y refinarla con el sistema recomendador.

- id usuario: `FK -> Usuario`
- id estadística: `FK -> Estadisticas`
- valor de estadistica: `numeric`

Ambos `id usuario` y `id estadistica` formarán juntos la `PK`.

## Sistema recomendador de productos {#sistema-recomendador}

Para el desarrollo de el sistema recomendador de productos necesitamos saber qué productos compran los usuarios pero como la plataforma no es de compra de productos hemos de usar alguna otra forma, en este caso haremos uso de los productos de las listas de la compra de los usuarios.

Opciones:

1. Etiquetado de productos. De forma manual se podrían etiquetar la forma genérica de los productos para a posteriori hacer un sistema recomendador en base a un filtrado basado en contenido.
   - Contras: implementación manual de etiquetado de productos, falta de interacción entre usuarios, coste alto de etiquetado.
   - Pros: posiblemente el más efectivo a la hora de recomendar productos similares.
2. Basándose en listas de la compra. Incentivar al usuario a crear listas de la compra únicas para cada compra con el objetivo de guardarlas. De esta forma recomendar con uso de filtrado de interacciones de usuario que tengan productos similares en la lista de la compra.
   - Contras: en algo tan específico como comprar en un supermercado y que puede ser común hacerlo mucho, las listas de la compra la desviación entre listas puede ser muy acrecentada y la recomendación mala.
3. Basándose en 'usualmente comprado con'. Haciendo uso de las listas de la compra obtener productos que se compren comunmente junto con otros.
   - Contras: pobre, las listas de la compra suelen incluir productos muy diferentes.
   - Pros: podría recomendar productos que se compren juntos para, por ejemplo, recetas.
4. Basándose en ingredientes de recetas. Recomendar productos que sean comunes de usar en recetas que incluyan los ya añadidos.
   - Contras: muchos productos básicos serían recomendados muy a menudo, ejemplo ajo, cebolla, aceite, etc.
5. Basándose en perfiles de usuario. Haciendo uso de listas de la compra de los usuarios, buscar usuarios con perfiles similares para recomendar productos que unos compran y otros no. ++ (Lo más parecido a hacer recomendaciones por 'dietas' similares). Sería un sistema recomendados basado en interacciones de usuario, en el caso, frecuencia de compra de productos. Dada una lista de la compra con X productos se buscarían otros usuarios con perfiles similares de compra, es decir que compren cosas parecidas y se recomendarían otros productos de estos terceros perfiles dandole más valor a aquellos perfiles con mayor frecuencia de compra de productos comunes.
   - Para esto es necesario mantener como mínimo un contador para saber con qué frecuencia se compran ciertos productos. Como la compra no forma parte de la plataforma se valorará como 'compra' cuando un producto aparece en una lista de la compra y este posteriormente se marca en la lista. Una vez por lista.
   - También se pueden almacenar las listas de la compra de forma íntegra para en caso de necesitar esa información en un futuro, tenerla.

La opción escogida será la 5.
