## Datos de usuario a guardar

- email: *identificador de cuenta*
- contraseña: *herramienta de inicio de sesión. Encriptada en la base de datos.*
- libería del usuario: *lista de planos de distrubición de supermercados asociados/guardados por el usuario en su librería personal.*
    *se incluyen: planos creados por el usuario, planos importados de otros usuarios por el propio a su librería*
- lista de la compra: *lista de objetos/productos creada y guardada por el usuario*
- datos estadísticos de compra del usuario: *datos a usar por el sistema de recomendación*
    *se incluyen: nombres de productos comprados, precio de productos comprados...*

## Estructura de datos

### Planos de distribución portables {#planos}

#### Descripción {#planos-descripcion}

Un plano de distribución se entiende como una semejanza esquemática de la distribución de productos de un supermercado con el objetivo de enseñar de forma visual la localización de o objetos, alimentos u otros dentro de este. Un plano deberá de distinguir entre las principales secciones lógicas que se entiende que existen en un supermercado. A priori estas secciones son:

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

Para cumplir los anteriores requisitos se debe conseguir una estructura para el formato que sea sólida. Entonces, la estructura de formato será en matriz (atributos 'posx' y 'posy' para saber desde qué posición del esquema crecen), su anchura y altura, dirección derecha y abajo (atributos 'width' y 'height' para saber cuánto crece la sección y hacia donde), con cada valor de esta un objeto (objeto JSON), que identifice que tipo de sección (atritbuto 'id') y que permita añadir productos en caso de que sea una zona de productos (atributo de valor vector 'prods' en caso de que el identificador sea válido para zona de productos).

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
- prods: atributo de valor vector de texto que sirve para listar los alimentos, productos, objetos encontrados en una sección 02.

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
  "prods":["carne", "pollo"]
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
  "prods":["carne", "pollo"]
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
