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
**Practica 1:** En esta práctica el objetivo es configurar las máquinas virtuales (al menos dos) para
trabajar en prácticas posteriores, asegurando la conectividad entre dichas máquinas.
Como resultado de la práctica 1 se mostrarán dos máquinas funcionando al profesor
(accesos con curl para solicitar páginas web sencillas, acceso por SSH entre ambas
máquinas, así como configuraciones de red).
Específicamente, hay que llevar a cabo las siguientes tareas:
    1. acceder por ssh de una máquina a otra
    2. acceder mediante la herramienta curl desde una máquina a la otra
    3. mostrar configuraciones de red y opciones de netplan

**Practica 2:** En esta práctica el objetivo es configurar las máquinas virtuales para trabajar en modo
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


**Practica 3:** En esta práctica el objetivo es configurar las máquinas virtuales de forma que dos hagan
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

**Practica 4:**

**Practica 5:**

**Practica 6:**
    
