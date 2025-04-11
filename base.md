# Documento-guía base de Trabajo de Fin de Grado

## Descripción

### Anteproyecto

1. Nome
Alan Xes
1. Apelidos
López Fernández
1. DNI
33558938Y
1. E-mail
alan.lfernandez@udc.es
1. Teléfono
666980964
1. Título Galego
Celga 4
1. Título castelán
4A
1. Título inglés
B2
1. Directores (un por liña)
Marcos Gestal Pose
1. Mención
Enxeñaría do Software
1. Tipo de proxecto
Clásico de enxeñaría
1. Breve descripción
Aplicación web para a creación e visualización de esquemas distributivos de productos en supermercados ademáis de encontrar a mellor oferta.
1. Obxectivos concretos
    - Rexistro de usuarios.
    - Ofrecer ó usuario unha interfaz que lle permita crear, gardar e compartir distribucións de produtos de un supermercado.
    - Ofrecer ó usuario unha interfaz que lle permita crear e gardar listas de compra con productos que desexe.
    - Ofrecer ó usuario a posibilidade de escanear catálogos web de supermercados co obxectivo de encontrar as mellore ofertas.
1. Método de traballo
Traballar en sprints de unha semana con os seguintes obxectivos:
    - Metas de traballo claras.
    - Seguementos rápidos e constantes no desenvolvemento do proxecto coma o cumplimento de metas ou xurdimento de problemas.
    - Flexibilidade á hora de ataxar solucións e restructurar o traballo se he necesario.
    - Versatilidade para cambiar a priorización das tareas.
1. Fases principais
    - Planificación de uso e preparación do proxecto: planificar o entorno de traballo, preparar as ferramentas e servicios necesarios, determinar funcionalidades, requisitos e alcance da aplicación.
    - Deseño: deseño de base de datos, creación de casos de uso, prototipado da interfaz de usuario, fluxos de navegación, usabilidad.
    - Implementación: codificación, integración, pruebas unitarias, pruebas de integración, despliegue y documentación.
    - Probas: de sistema, usabilidad, aceptación del usuario, seguimiento y registro de errores.
2. Material e medios necesarios
Inclúense ordenador persoal de escritorio e un portátil para o desenvolvemento. Entre os medios necesarios contarase co entorno de desenvolvemento Microsoft Visual Studio Community 2022 e ferramentas de p. Outros aspectos inclúen un servidor de bases de datos e un framework para integración da conexión da BBDD, procesamento de datos, lóxica de negocio e a implementación dunha RESTful API para a conexión da interfaz web accesible ó usuario.
1. Modalidade
Traballo a proposta do alumno

### Objetivos personales

Coma obxectivos persoais: mellorar no uso do marco de desenvolvemento ASP.NET así coma introducirme e aprender sobre TypeScript, Angular e a integración máis interacción entre os lenguaxes e frameworks.

### Materiales, medios y tecnologías

Inclúense ordenador persoal de escritorio e un portátil para desenvolvemento. Entre as ferramentas de sofware: Microsoft Visual Studio Community Edition 2022 coma IDE e Git + GitHub para control de versións. Nas utilidades de desenvolvemento: PostgreSQL para o diseño e implementación de a base de datos, ASP.NET como framework encargado do backend e Angular como framework para frontend. En caso de librerías externas destacadas: Gridstack para desenvolvemento da interfaz de usuario e HTMLAgilityPack para análise e recollida de datos. Todas as ferramentas software, utilidades de desenvolvemento e librerías externas están rexistradas baixo licencias que permiten o uso de individual e/ou estudantil.

### Licencias

MS Visual Studio Community 2022:

    Visual Studio Community 2022 is free for:

    Individual developers.   
    Students.  
    Open-source contributors.  
    Academic research.   

Git + GitHub - GNU General Public License version 2:

    Git is open-source, licensed under the GNU General Public License version 2.
    GitHub offers free accounts for students and academic projects, with ample storage and features.
    You're free to use both Git and GitHub for your project.

PostgreSQL - PostgreSQL License:

    PostgreSQL is released under the PostgreSQL License, which is a very permissive open-source license.
    It allows you to use, modify, and distribute the software for any purpose, including academic, commercial, and personal.
    Therefore, you can use it without any restrictions.

Angular - MIT:

    Angular is released under the MIT License, which is another very permissive open-source license.
    You can freely use Angular in your project.

ASP.NET - MIT:

    ASP.NET (specifically ASP.NET Core) is open-source, licensed under the MIT License.
    You have complete freedom to use it for your project.

Gridstack TS library - MIT:

    Gridstack is licensed under the MIT License.
    This license is very permissive, allowing you to use it for any purpose, including academic.

HTMLAgilityPack - MIT:

    HTMLAgilityPack is licensed under the MIT License.
    This means it is free to use for any purpose.

### Objeto general

Plataforma web que permita la creación de esquemas visuales de distribución interna de supermercados e permita a análise de ofertas sobre productos de unha lista da compra en base a información dos catálogos online dos supermercados.

### Funcionalidad general

- Registro de usuarios.
- Creación de esquemas internos de supermercados y distribución de productos. Mediante uso de Gridstack.
- Creación de listas de la compra.
- Análisis de productos en lista de la compra con precios de distintos supermercados (2 de ejemplo) para ofrecer el mejor precio encontrado (o un rango). Mediante uso de Web-Scraping.
- [Dependiendo del tiempo] Creación de recorridos siguiendo los esquemas de distribución de supermercado y listas de la compra. Mediante conversión de los esquemas a grafos y grafos en recorridos.
- [Dependiendo del tiempo] Mostrado de los recorridos visualmente mediante esquemas generados por las listas de la compra, esquemas de distribución y análisis de recorridos.

### Funcionalidades

### TODO

- [X] Elegir framework backend -> ASP.NET
- [X] Elegir framework frontend -> Angular
- [X] Elegir framework DB -> PostgreSQL

### Notas

Grafos
QuickGraph (MIT Licensed):
    
    A popular and well-established .NET library for graph data structures and algorithms.
    Provides a wide range of graph algorithms, including shortest path algorithms.
    It is mature and well documented.
    It is open source.

Microsoft Automatic Graph Layout (MSAGL) (MIT Licensed):

    Originally developed by Microsoft Research.
    Provides graph layout and manipulation capabilities.
    Can be used for pathfinding and graph analysis.
    It is open source.
### Dudas