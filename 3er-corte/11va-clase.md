# Presentación, integración a Matlab y uso de entorno de gemelo digital Quanser Interactive Labs

Quanser Interactive Labs es una plataforma escalable que ofrece experiencias de laboratorio interactivas y de alta fidelidad para estudiantes de ingeniería a distancia. Basada en hardware líder en la industria para control, robótica y mecatrónica, permite a los estudiantes trabajar con plantas virtuales realistas en múltiples dispositivos (Windows, MacOS, iOS y Android). Además de actividades de laboratorio, se integra con otros materiales del curso para aumentar la interacción y el compromiso. Incluye un plan de estudios completo con verificación de conocimientos, preguntas de evaluación e informes de laboratorio.

## Uso en Matlab

![Integración de Quanser en Matlab](/Imagenes/Qmatlab.png)

Quanser se presenta en matlab como un paquete descargable, se puede descargar en zip e integrarlo manualmente o con el gestor de paquetes de Matlab descargarlo e instalarlo con menos clicks.
Una vez hecho esto se empieza con la instalación del laboratorio virtual donde se encuentran los módelos a trabajar.
Primero se usa el comando $QLabs.setup$ para instalar todo lo necesario para la ejecución.
Luego con el comando $QLabs.launch$ se descargan actualizaciones (si hay) y se abre la ventana del laboratorio, el cual según los modelos que se hayan adquirido se mostrarán para su elección.
Todos los modelos se trabajan con la herramienta Simulink porque ahí se encuentran los bloques para la configuración, lectura, escritura de las diferentes funciones y sensores que estos modelos tienen según su proceso.

También es posible conectarse a la planta física de 3 posibles maneras de diferentes.

+ Simulink
+ LabView
+ Sistema embebido externo

## Modelos a usar

### QUBE-Servo 3

![Quanser Servo 3](/Imagenes/Qservo-3.jpg)

El primer y principal módelo con el que se va a trabajar es el Servo 3, este tiene su parte física en labotario, donde todas las simulaciones exitosas serán probadas, se adquirio el QUBE-Servo 2 simulado y físico el QUBE-Servo 3, según el fabricante no debe haber problema con la compatibilidad entre versiones ya que el principal cambio es el método de energía usado, en la version 2 hay un cable para suministrar energía con la característica de que si no se utiliza, el motor no encendera y en la 3 se cambio a una entrada USB tipo C.

El dispositivo físico viene con las siguiestes características:
+ Motor DC 5400 RPM
    + Sin carga 16 mA
+ Fuente 24V 
+ Tarjeta de adquisición de datos
    * Driver de potencia
    * Sensor de corriente
    * 2 encoders
        + 720 CPR
    * Microcontorlador para gestionar la comunicación

Para la conexión virutal en simulink se busca el bloque `HILInicialize` este aparecerá una vez intalado el complento en la sección `QUARC Targets`.
El bloque tendra los campos: 
+ ***Board Name***: Se pone un nombre cualquera
+ ***Board Type***: Se escoge `Qube_servo2` para simulación, cuando se vaya a probar de manera física se elige `Qube_servo3`.
+ ***Board Identifier***: Cuando se usa de manera física este campo no se modifica, pero al hacerlo de manera digital se le asigna una ruta `@pspip://localhost:18920`.

Pasadas las configuraciones de conexión se debe cambiar el tiempo de simulación a infinito para no tener límite en el proceso de ejecución. 

Luego en la interfaz (laboratorio) de Quanser se elige la imagen del motor.
Aparecerá el modelo de la planta del motor en 3D, se sabrá si esta bien conectado cuando en Simulink se incie la simulación y la banda de leds superior en el motor se cambia a `Verde`.

Una vez conectado correctamente en simulink se buscara el bloque `HIL write Analog` este tiene los siguientes campos: 
+ ***Board Name***: Se debe asignar el mismo nombre que en el bloque anterior.
+ ***Channels***: Para el motor DC solo hay una entrada de voltaje, para activarla se selecciona y se le da al botón `>>`.
+ ***Sample line (Seconds)***: Por defecto tiene el valor de $-1$, no se modifíca.
~~~
Nota: Simulink por defecto trae un tiempo de muestreo variable que busca hacer mas corta las solución de las ecuaciones que hace la simulación. Lo recomendable es cambiarlo porque al simular dispositivos lo deseado es que sea en tiempo real. 

Para configurarl:
- Pestaña de "Model"
- Model Settings
- Solver
- Type se cambia a "Fixed-step"
- Fundamental sample time se le asigna el valor de 0.002
~~~

**32:21 video :c**


Se usa para enviar ordenes al motor en voltaje, se puede enviar señales PWM con `HIL write PWM`, también esta `HIL Read Analog` que se usa para leer información.


## Bibliografía
Quanser. (2025). Quanser Interactive Labs for MATLAB. [Archivo]. Recuperado de https://www.mathworks.com/matlabcentral/fileexchange/123860-quanser-interactive-labs-for-matlab

Quanser. (2023). Qube-Servo 3. https://www.quanser.com/products/qube-servo-3/