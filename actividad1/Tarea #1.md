# Tarea #1
## Tipos de Kernel
Existen diferentes tipos de kernel para diferentes sistemas operativos y dispositivos finales. Conforme a sus características, pueden dividirse en tres grupos:

- Kernel monolítico
- Microkernel
- Kernel híbrido.

### Kernel monolítico
Este tipo de núcleo es aquel que facilita la abstracción del hardware subyacente sin importar su grado de potencia o variedad. Para realizar una comparación objetiva, estos núcleos son bastante complejos en cuanto a su manejo, siendo comparados con los próximos que vamos a observar. Hace más de veinte años, estos núcleos eran los principales en ser catalogados como obsoletos e inservibles, además de innecesarios. Sin embargo, con el tiempo han sido catalogados como mejorados e importantes, aunque no precisamente los mejores.

![Kernel monolitico](https://universodigital.org/wp-content/uploads/Kernel-monolitico.png, "Kernel Monolitico")

Algunos de los sistemas que usan este tipo de kernel son: 
- Linux
- Unix
- BSD
- DR-DOS
- MS-DOS


### Micro-Kernel
Un microkernel es una de las clasificaciones del kernel. Al ser un kernel, administra todos los recursos del sistema. Pero en un microkernel, los servicios de usuario y los servicios del kernel se implementan en diferentes espacios de direcciones. Los servicios de usuario se mantienen en el espacio de direcciones del usuario, y los servicios del núcleo se mantienen en el espacio de direcciones del núcleo, por lo que también se reduce el tamaño del núcleo y el tamaño de un sistema operativo.

![Microkernel image](https://upload.wikimedia.org/wikipedia/commons/thumb/6/67/OS-structure.svg/1200px-OS-structure.svg.png)

Proporciona servicios mínimos de gestión de procesos y memoria. La comunicación entre el programa/aplicación cliente y los servicios que se ejecutan en el espacio de direcciones de usuario se establece mediante el paso de mensajes, lo que reduce la velocidad de ejecución del micronúcleo. El sistema operativo no se ve afectado, ya que los servicios de usuario y los servicios del núcleo están aislados, de modo que si falla algún servicio de usuario no afecta al servicio del núcleo. De este modo se añade una de las ventajas de un micronúcleo. Es fácilmente ampliable, es decir, si hay que añadir nuevos servicios, se añaden al espacio de direcciones del usuario y, por tanto, no requieren modificaciones en el espacio del núcleo. También es portátil, seguro y fiable. 

##### Arquitectura del micronúcleo
Dado que el kernel es la parte central del sistema operativo, está diseñado para gestionar únicamente los servicios más importantes. Por lo tanto, en esta arquitectura, sólo los servicios más importantes están dentro del núcleo y el resto de los servicios del sistema operativo están presentes dentro del programa de aplicación del sistema. Así, los usuarios pueden interactuar con aquellos servicios no tan importantes dentro de la aplicación del sistema. El micronúcleo es el único responsable de los servicios más importantes del sistema operativo, que se denominan de la siguiente manera: 
 

- Comunicación entre procesos
- Gestión de memoria
- CPU-Programación

##### Ventajas del micronúcleo

- Modularidad: Dado que el núcleo y los servidores pueden desarrollarse y mantenerse de forma independiente, el diseño del micronúcleo permite una mayor modularidad. Esto puede facilitar la adición y eliminación de funciones y servicios del sistema.

- Aislamiento de fallos: El diseño del micronúcleo ayuda a aislar los fallos y a evitar que afecten a todo el sistema. Si falla un servidor u otro componente, puede reiniciarse o sustituirse sin causar interrupciones al resto del sistema.

- Rendimiento: Dado que el núcleo sólo contiene las funciones esenciales necesarias para gestionar el sistema, el diseño del micronúcleo puede mejorar el rendimiento. Esto puede hacer que el sistema sea más rápido y eficiente.

- Seguridad: El diseño del micronúcleo puede mejorar la seguridad al reducir la superficie de ataque del sistema limitando las funciones proporcionadas por el núcleo. El software malicioso puede encontrar más difícil comprometer el sistema como resultado de esto.

### Kernel híbrido
Este tipo de kernel, es aquel que se considera una gran modificación del microkernel, que si bien son bastante similares en cuanto a diversas características, se diferencian debido a que este cuenta con un espacio adicional que cumple la función de permitir que el mismo se ejecute de forma mucho más rápida y funcional. Sin embargo, cualquiera de estos dos núcleos es bastante funcional, incluso los micronúcleos comunes, los cuales tienen un excelente rendimiento. Muchos de los sistemas operativos que se aplican hoy en día, cuentan con estos dos tipos de núcleos ya que ambos funcionan muy bien.


### User Mode vs Kernel Mode

#### User mode
Cuando se inicia un programa en un sistema operativo, por ejemplo Windows, el programa se ejecuta en modo usuario. Y cuando un programa en modo usuario solicita ejecutarse, windows crea para él un proceso y un espacio de direcciones virtual (espacio de direcciones para ese proceso). Los programas en modo usuario tienen menos privilegios que las aplicaciones en modo usuario y no pueden acceder directamente a los recursos del sistema. Por ejemplo, si una aplicación en modo usuario quiere acceder a los recursos del sistema, tendrá que pasar primero por el núcleo del sistema operativo utilizando syscalls.

#### Kernel mode
El núcleo es el programa central en el que se basan todos los demás componentes del sistema operativo, se utiliza para acceder a los componentes de hardware y programar qué procesos deben ejecutarse en un sistema informático y cuándo, y también gestiona el software de aplicación y la interacción con el hardware. De ahí que sea el programa más privilegiado, ya que, a diferencia de otros programas, puede interactuar directamente con el hardware. Cuando los programas que se ejecutan en modo usuario necesitan acceder al hardware, por ejemplo la webcam, primero tienen que pasar por el kernel mediante una syscall, y para llevar a cabo estas peticiones la CPU cambia de modo usuario a modo kernel en el momento de la ejecución. Después de completar la ejecución del proceso, la CPU vuelve al modo usuario.


