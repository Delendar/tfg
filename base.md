# Documento-guía base de Trabajo de Fin de Grado

## Descripción

### Objeto general

Plataforma web para la localización de artículos o productos disponibles para compra en tiendas locales cercanas mediante las aportaciones de otros usuarios y/o propietarios de una tienda.
Las tiendas cercanas se identificarán mediante la ubicación de un usuario o en su defecto la ubicación que el usuario desee determinar.

### Funcionalidad general

- Subida de información sobre un producto:
  - El usuario debe tener la capacidad de añadir a la base de datos de la aplicación un producto y la ubicación para su compra.
  - El usuario debe tener la capacidad de borrar un producto y su ubicación de la base de datos que haya sido añadido por él mismo.
- Búsqueda de productos:
  - El usuario debe tener la capacidad de acceder a la información de productos disponibles en una zona cercana a su ubicación o en caso contrario en una ubicación que él desee.
  - El usuario debe tener la capacidad de filtrar la búsqueda de un producto por información descriptiva del mismo (i.e. nombre de producto).
- Valoración de anuncios:
  - El usuario debe tener la capacidad de valorar positivamente o negativamente en caso de que un anuncio en la plataforma sea útil o no.

### Funcionalidades

1. Usuario sin registro:
    1. Creación de cuenta de usuario cliente.
    2. Creación de cuenta de usuario propietario.
2. Usuario cliente:
    1. Borrado de cuenta de usuario.
    2. Modificación de credenciales y/o datos de usuario.
    3. Subida de un producto de venta asociado a una ubicación de compra. A un post hecho por un usuario cliente sobre un producto llamaremos un `PRODUCTO`.
       - Información:
          1. Nombre de producto.
          2. Tienda.
          3. Ubicación.
          4. Precio (opcional).
          5. Fecha de compra (predefinido a momento de creación del `PRODUCTO`).
          6. Observaciones?
    4. Borrado de un producto de venta asociado a una ubicación de compra si y solo si este ha sido subido por el mismo usuario.
    5. Modificación de información asociada a un `PRODUCTO`.
       - Información modificable:
         1. Nombre de producto.
         2. Tienda.
         3. Ubicación.
         4. Precio.
         5. Observaciones?
    6. Búsqueda para acceder a productos de venta de una zona cercana al usuario o en una ubicación deseada.
    7. Filtrar búsqueda de productos por información relevante de un producto a encontrar (i.e. nombre de producto).
    8. Votar positivamente en un `PRODUCTO` con el objetivo de que otros usuarios sepan si es útil. Existiendo exclusividad entre votación positiva y negativa.
    9. Votar negativamente en un `PRODUCTO` con el objetivo de que otros usuarios sepan si no es útil. Existiendo exclusividad entre votación positiva y negativa.
       1. En caso de votar negativamente en un `PRODUCTO` se dará la opción de poner un comentario para dar información adicional.
    10. Borrado de el comentario sobre una votación negativa de un `PRODUCTO`.
    11. Modificación en un `PRODUCTO` una votación positiva a una negativa y viceversa. En caso de tener una votación negativa con comentario y se quiera cambiar a votación positiva se eliminará el comentario también.
3. Usuario propietario (usuario que tenga una tienda de productos propia):
    1. Vinculación de cuenta con la tienda propietaria, restricciones de funcionalidades hasta que no se vincule.
    2. Borrado de cuenta de usuario.
    3. Modificación de credenciales, datos de usuario y/o datos de tienda.
    4. Subida de un producto de venta asociado a la ubicación de la propia tienda. Lo llamaremos un `PRODUCTO DE TIENDA`.
    5. Borrado de un producto de venta asociado a la ubicación de la propia tienda.
    6. Modificación de información asociada a un `PRODUCTO DE TIENDA`.
    7. Acceso a un listado de todos los `PRODUCTO DE TIENDA` que estén asociados por la cuenta de usuario.
    8. Filtrar el listado de todos los `PRODUCTO DE TIENDA` de la cuenta por información relevante (i.e. nombre de producto).
    9. Acceso a un `PRODUCTO DE TIENDA` específico mediante el listado.

### TODO

- [X] Elegir framework plataforma -> ASP.NET
- [ ] Elegir framework DB -> SQL Server?
- [X] Elegir host -> Microsot Azure Cloud



Producto: Tijeras de cocina
Tienda: Manolo Vende
Ubicación: Rúa Camiño Verde 23

### Dudas

- Tiene google maps un identificador único para todos los marcadores que existen?
  - Si lo tiene, es público? Es decir, sirve para que el usuario busque un marcador en el mapa y lo marque para vincular el objeto?
- Puedes crear un mapa personalizado para marcadores es Google Maps?
  - Puedes duplicar marcadores de Maps normal a la versión personalizada para el proyecto?