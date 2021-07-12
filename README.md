# Servidores Web de Altas Prestaciones
Asignatura cursada en la Universidad de Granada periodo 2020-2021 en la que configuramos un servidor web usando herramientas como virtual box, balanceadores, cortafuegos, copias de seguridad y mas elementos.

## Objetivos de la asignatura
* Explicar y exponer los principales conceptos relacionados con la alta disponibilidad, redundancia y tolerancia a fallos.
* Determinar posibles problemas de escalabilidad de una instalación.
* Configurar un balanceador de carga de forma adecuada a las necesidades.
* Realizar las tareas de la administración deun sistema de alta disponibilidad.
* Señalar y describir las tecnologías hardware actuales para la instalación de granjas o agrupaciones de servidores.
* Encontrar y arpovechar la soluciones idóneas para servidores de alta disponibilidad.
* Seleccionar diferentes herramientas de seguridad y describir su uso.
* Establecer la configuración de los servidores y las estrategias para optimizar la seguridad del sistema.
* Seleccionar, instalar  y usar las herramientas de análisis y monitorización de las prestaciones del sistema.
* Diseñar y configurar un sistema web de alta disponibilidad.
* Diseñar un plan de copias de seguridad y recuperación para resolver cualquier problema en el sistema.

## Prácticas
### Practica 1
En esta práctica el objetivo es configurar las máquinas virtuales (al menos dos) para
trabajar en prácticas posteriores, asegurando la conectividad entre dichas máquinas.
Como resultado de la práctica 1 se mostrarán dos máquinas funcionando al profesor
(accesos con curl para solicitar páginas web sencillas, acceso por SSH entre ambas
máquinas, así como configuraciones de red).
Específicamente, hay que llevar a cabo las siguientes tareas:
    1. acceder por ssh de una máquina a otra
    2. acceder mediante la herramienta curl desde una máquina a la otra
    3. mostrar configuraciones de red y opciones de netplan

### Practica 2
En esta práctica el objetivo es configurar las máquinas virtuales para trabajar en modo
espejo, consiguiendo que una máquina secundaria mantenga siempre actualizada la
información que hay en la máquina servidora principal.

Hay que llevar a cabo las siguientes tareas básicas:
1. probar el funcionamiento de la copia de archivos por ssh
2. clonado de una carpeta entre las dos máquinas
3. configuración de ssh para acceder sin que solicite contraseña
4. establecer una tarea en cron que se ejecute cada hora para mantener
actualizado el contenido del directorio /var/www entre las dos máquinas
Opcionalmente, tareas más avanzadas como:
    * Varias opciones de copiar archivos por ssh y scp
    * Utilizar RSync con varias opciones y parámetros
    * Configurar ssh para evitar introducir contraseña de manera manual
    * Programar tareas con Crontab con distintas opciones


### Practica 3
En esta práctica el objetivo es configurar las máquinas virtuales de forma que dos hagan
de servidores web finales mientras que la tercera haga de balanceador de carga por
software.
* En esta práctica se llevarán a cabo las tareas básicas:
    1. Configurar una máquina e instalar nginx y haproxy como balanceadores de carga con el algoritmo round-robin
    2. Someter la granja web a una alta carga con la herramienta Apache Benchmark a través de M3, considerando 2 opciones:
        a) nginx con round-robin
        b) haproxy con round-robin
    3. Realizar un análisis comparativo de los resultados considerando el número de peticiones por unidad de tiempo
* Como opciones avanzadas:
    1. Configurar nginx y haproxy como balanceadores de carga con ponderación, suponiendo que M1 tiene el doble de capacidad que M2.
    2. Habilitar el módulo de estadísticas en HAproxy
    3. Instalar y configurar otros balanceadores de carga (Gobetween, Zevenet, Pound, etc.)
    4. Someter la granja web a una alta carga con la herramienta Apache Benchmark considerando los distintos balanceadores instalados y configurados.
    5. Realizar un análisis comparativo de los resultados considerando el número de peticiones por unidad de tiempo

### Practica 4
El objetivo de esta práctica es configurar aspectos relativos a la seguridad de la granja web. Se debe añadir usuarioUGR en las distintas configuraciones e ilustrarlo con capturas de pantalla.
* En esta práctica se llevarán a cabo las siguientes tareas básicas:
    1. Crear e instalar en la máquina M1 un certificado SSL autofirmado para configurar el acceso HTTPS al servidor. Se debe comprobar que el servidor acepta tanto el tráfico HTTP como el HTTPS.
    2. Copiar al resto de máquinas servidoras (M2) y al balanceador de carga (M3) el certificado autofirmado creado en M1 (archivos .crt y .key) y configurarlas para que acepten tráfico HTTP y HTTPS.
    3. Denegar todo el tráfico entrante a las máquinas M1, M2 y M3 a excepción de tráfico HTTP y HTTPS.
    4. Configurar y documentar las reglas del cortafuegos con IPTABLES a través de un script en cada máquina con las reglas creadas.
* **Como tareas avanzadas:**
    1. Permitir SSH, PING y DNS a las máquinas M1, M2 y M3 así como el tráfico consigo misma (localhost). El resto de servicios y/o peticiones debe denegarse.
    2. Configurar M3 estableciendo reglas de iptables para que sólo M3 sea quien acepte peticiones HTTP y HTTPS mientras que M1 y M2 no acepten peticiones a no ser que sean peticiones provenientes de M3.
    3. Hacer que la configuración del cortafuegos se ejecute al arranque del sistema en todas las máquinas.
    4. Crear, instalar y configurar un certificado SSL con Cerbot u otro.

### Practica 5
En esta práctica el objetivo es configurar las máquinas virtuales para trabajar de forma que se mantenga actualizada la información en una BD entre dos servidores (la máquina secundaria mantendrá siempre actualizada la información que hay en la máquina servidora principal).
* En esta práctica se llevarán a cabo, como tareas básicas:
    1. Crear una BD con al menos una tabla y algunos datos.
    2. Realizar la copia de seguridad de la BD completa usando mysqldump en la máquina principal y copiar el archivo de copia de seguridad a la máquina secundaria.
    3. Restaurar dicha copia de seguridad en la segunda máquina (clonado manual de la BD), de forma que en ambas máquinas esté esa BD de forma idéntica.
    4. Realizar la configuración maestro-esclavo de los servidores MySQL en M1 y M2 para que la replicación de datos se realice automáticamente. M1 (maestro) – M2 (esclavo)
    5. Añadir regla IPTABLES para permitir tráfico al puerto 3306
* Como tareas avanzadas:
    1. Además de las tareas básicas
    2. Realizar la configuración maestro-maestro entre las dos máquinas de bases de datos.

### Practica 6
En esta práctica el objetivo es configurar una máquina como servidor NFS y que las dos máquinas servidoras finales (M1 y M2) monten una carpeta exportada como clientes.
* Hay que llevar a cabo las siguientes tareas básicas:
    1. Configurar una máquina como servidor de disco NFS y exportar una carpeta a los clientes.
    2. Montar en las máquinas cliente la carpeta exportada por el servidor.
    3. Comprobar que todas las máquinas pueden acceder a los archivos almacenados en la carpeta compartida.
* Adicionalmente, y como tarea avanzada, se propone:
    1. Hacer permanente la configuración en los clientes para que monten automáticamente la carpeta compartida al arrancar el sistema
    2. Añadir configuración de seguridad a la máquina NFS, bloqueando todo el tráfico entrante y permitiendo solo el tráfico necesario para que funcione el servidor NFS en las máquinas M1 y M2.
    
