# Escenarios de uso

## Glosario

[Tu Biblioteca]: espacio personal del usuario que hace referencia a la información sobre sus datos guardados persistentes en el sistema que no hacen referencia a datos de usuario como contraseña, nombre, correo... sino que hacen referencia a planos, listas de la compra...

## Datos de usuario

### Creación de usuario

### Modificación de datos del usuario (datos del perfil)

### Eliminación del usuario

### Inicio de sesión

### Cierre de sesión

## Planos

### Creación de un plano

Pre-condiciones:

1. el usuario tiene una sesión iniciada

Flujo:

Post-condiciones:

### Edición de un plano propio

Pre-condiciones: se ha iniciado sesión + se ha accedido a un plano guardado A

Flujo directo:
Se accederá a la interfaz de edición de un plano en la cual el plano base de la interfaz será el plano A accedido por el usuario.

Post-condiciones:

1. el plano en al que se realizaron modificaciones se guardará actualizado en la biblioteca del usuario.
2. si el plano estaba registrado en las bases de datos en la nube como un plano guardado y accesible a otros usuarios, entonces al modificarlo y guardarlo también se actualizará en los registro de la nube con las nuevas modificaciones

### Edición de un plano de terceros (fork de un plano en la nube)

### Guardado de un plano a [Tu Biblioteca]

### Subida de un plano al repositorio público en la nube

### Acceso a [Tu Biblioteca]

Pre-condiciones:

1. se ha iniciado sesión

Flujo directo:
Mediante una acción (i.e. click) se accederá a una pantalla en la cual se expongan los planos guardados por el usuario, tanto propios como de terceros. En esa lista se podrá acceder a: visualización, modificación, guardado en nube (registro de un plano en las bases de datos de la nube para acceso a otros), o eliminación.

Post-condiciones:

1. se presenta al usuario una pantalla en la cual sea capaz de ver la lista de planos con las acciones posibles descritas

### Acceso/visualizacion de un plano

Pre-condiciones:

1. se ha iniciado sesión

Flujo directo:
Con la lista de planos guardados accesibles por el usuario se permitirá acceder mediante una acción (como un click) a la visualización del plano.

Post-condiciones:

1. se presenta al usuario una pantalla en la cual sea capaz de visualizar el plano

### Creación de un plano (Acceso a [Tu Biblioteca] + Acceso a interfaz de )

Pre-condiciones: se ha iniciado sesión + se ha accedido a [Tu Biblioteca]

Flujo directo:
Se accederá a la interfaz de edición de un plano en la cual el plano base será un plano vacío.
