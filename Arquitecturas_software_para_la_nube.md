# Arquitecturas software para la nube

### 1º Ejercicio:

***Buscar una aplicación de ejemplo, preferiblemente propia, y deducir qué patrón es el que usa. ¿Qué habría que hacer para evolucionar a un patrón tipo microservicios?***

En la asignatura de Tecnologías Web hicimos entre dos compañeros una aplicación consistente en una página web musical, dicha app dirigida por eventos consistía en la promoción de un grupo de música así como de venta de artículos y entradas a conciertos. Contenía una BBDD MySQL y el código desarrollado en HTML, CSS, PHP y JavaScript.

Podríamos transformar nuestra arquitectura por una basada en microservicios, tenemos ya identificado cada evento y cada uno de ellos pasaría a ser un microservicio, como por ejemplo la gestión de usuarios, ventas, contenidos…

### 2º Ejercicio:

***En la aplicación que se ha usado como ejemplo en el ejercicio anterior, ¿podría usar diferentes lenguajes? ¿Qué almacenes de datos serían los más convenientes?***

Podríamos usar diferentes lenguajes, en cada microservicio el que más útil sea.

El almacén de datos mas conveniente dependerá si la estructura del contenido es estática o dinámica, así que podríamos usar una BBDD Sql para los datos de usuarios y una BBDD NoSql para el contenido de la web que es dinámico dependiendo del progreso del grupo musical.