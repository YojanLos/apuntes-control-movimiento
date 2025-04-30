# Presentación, integración a Matlab y uso de entorno de gemelo digital Quanser Interactive Labs

Quanser Interactive Labs es una plataforma escalable que ofrece experiencias de laboratorio interactivas y de alta fidelidad para estudiantes de ingeniería a distancia. Basada en hardware líder en la industria para control, robótica y mecatrónica, permite a los estudiantes trabajar con plantas virtuales realistas en múltiples dispositivos (Windows, MacOS, iOS y Android). Además de actividades de laboratorio, se integra con otros materiales del curso para aumentar la interacción y el compromiso. Incluye un plan de estudios completo con verificación de conocimientos, preguntas de evaluación e informes de laboratorio.

## Uso en Matlab

![Integración de Quanser en Matlab](/Imagenes/Qmatlab.png)

Quanser se presenta en Matlab como un paquete descargable, se puede descargar en zip e integrarlo manualmente o con el gestor de paquetes de Matlab descargarlo e instalarlo con menos clics.
Una vez hecho esto se empieza con la instalación del laboratorio virtual donde se encuentran los modelos a trabajar.
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

El primer y principal modelo con el que se va a trabajar es el Servo 3, este tiene su parte física en laboratorio, donde todas las simulaciones exitosas serán probadas, se adquirió el QUBE-Servo 2 simulado y físico el QUBE-Servo 3, según el fabricante no debe haber problema con la compatibilidad entre versiones ya que el principal cambio es el método de energía usado, en la versión 2 hay un cable para suministrar energía con la característica de que si no se utiliza, el motor no encenderá y en la 3 se cambió a una entrada USB tipo C.

El dispositivo físico viene con las siguientes características:
+ Motor DC 5400 RPM
    + Sin carga 16 mA
+ Fuente 24V 
+ Tarjeta de adquisición de datos
    * Driver de potencia
    * Sensor de corriente
    * 2 encoders
        + 720 CPR
    * Microcontrolador para gestionar la comunicación

Para la conexión virtual en Simulink se busca el bloque `HILInicialize` este aparecerá una vez instalado el complemento en la sección `QUARC Targets`.
El bloque tendrá los campos: 
+ ***Board Name***: Se pone un nombre cualquera
+ ***Board Type***: Se escoge `Qube_servo2` para simulación, cuando se vaya a probar de manera física se elige `Qube_servo3`.
+ ***Board Identifier***: Cuando se usa de manera física este campo no se modifica, pero al hacerlo de manera digital se le asigna una ruta `@pspip://localhost:18920`.

Pasadas las configuraciones de conexión se debe cambiar el tiempo de simulación a infinito para no tener límite en el proceso de ejecución. 

Luego en la interfaz (laboratorio) de Quanser se elige la imagen del motor.
Aparecerá el modelo de la planta del motor en 3D, se sabrá si está bien conectado cuando en Simulink se inicie la simulación y la banda de leds superior en el motor se cambia a `Verde`.

Una vez conectado correctamente en Simulink se buscará el bloque `HIL write Analog`, se usa para enviar ordenes al motor en voltaje, se puede enviar señales PWM con `HIL write PWM`, también esta `HIL Read Analog` que se usa para leer información. El bloque tiene los siguientes campos: 
+ ***Board Name***: Se debe asignar el mismo nombre que en el bloque anterior.
+ ***Channels***: Para el motor DC solo hay una entrada de voltaje, para activarla se selecciona y se le da al botón `>>`.
+ ***Sample line (Seconds)***: Por defecto tiene el valor de $-1$, no se modifica.
~~~
Nota: Simulink por defecto trae un tiempo de muestreo variable que 
busca hacer más corta la solución de las ecuaciones que hace la 
simulación. Lo recomendable es cambiarlo porque al simular 
dispositivos lo deseado es que sea en tiempo real. 

Para configurar:
- Pestaña de "Model"
- Model Settings
- Solver
- Type se cambia a "Fixed-step"
- Fundamental sample time se le asigna el valor de 0.002
~~~

Es posible usar un bloque de `constant` para simular un valor de voltaje a la entrada del bloque `HIL write Analog`. Para la primera simulación se usaron valores de 1 y 0.3 donde la respuesta del primero es demasiado rápida y difícil de percibir, se prueba el segundo valor donde el movimiento es más ameno y fácil de evidenciar.

Cabe aclarar que estos valores funcionan en simulación, físicamente no sería suficiente para mover el motor debido al driver de potencia el cual no se conoce su ganancia ni parámetros, se recomienda para la práctica hacer un acondicionamiento para que la variación de voltaje o pwm tenga sentido cuando se ingrese.

El siguiente bloque a usar es `HIL Read TimeBase` el cual unifica el tiempo de muestreo de todas las señales de los sensores, logrando que las muestras obtenidas se rijan sobre la misma base de tiempo de muestreo facilitando el análisis, curvas, etc. Este sería el bloque más universal para la lectura.

Aunque si se quiere leer sensores puntuales están los bloques `HIL Read Analog`, `HIL Read Digital`, `HIL Read Encoder` entre otros.

La configuración del bloque `HIL Read TimeBase` se hace llenando los siguientes campos:
+ ***Board Name***: Se debe asignar el mismo nombre que en el bloque anterior.
+ ***Clock***: Si se desea una base de tiempo diferente se puede poner, este funciona como un Presscaler donde la muestra se puede tomar cada 1, 2, 3 o 4 ciclos de reloj. Pero se puede dejar en el valor que viene por defecto ya que Simulink tiene la opción de cambiar los tiempos de muestreo.
+ ***Analog Channels***: En esta planta lo único que se puede medir es la corriente mediante un sensor análogo el cual ya se encuentra acondicionado.
    + Current Sensor
+ ***Encoder Channels***: Este viene con dos opciones, al ser un encoder de cuadratura es posible saber el sentido del motor. Estos cuentan la sumatoria de los pulsos.
    + Encoder 1 
    + Encoder 2
+ ***Digital Channels***: Señales digitales (1 o 0), son señales de estatus
    + ***Amplifer Fault***: Informa si hay problemas en el driver de potencia
    + ***Motor flat Detected*** Detecta si el eje del motor se encuentra bloqueado mecánicamente
    + La última anuncia el hallazgo de un error.
+ ***Other Channels***: Se encuentra el tacómetro, este brinda la velocidad en CPS (Cuentas Por Segundo)

Si llega a ocurrir algún error Quanser recomienda para la protección del motor un bloque donde parará toda ejecución si llega a activarse. Tiene dos entradas una de control donde estará conectado el voltaje y otra de movimiento en este caso relacionada al encoder.

Una posible falla sería cuando hay energía en el motor, pero sin movimiento, puede haberse bloqueado mecánicamente aumentando la corriente y posiblemente causando daños en los elementos.

~~~
Nota: Si luego de hacer alguna modificación se genera un mensaje de error puede ser culpa del gemelo digital, se recomienda salir del entorno del motor Quanser y volverlo a abrir.
~~~

### AERO 2

![Aero 2](/Imagenes/QAero_2.jpg)

Las conexiones para el gemelo del Aero 2 son iguales a las de Servo 2 diferenciando los campos:

+ ***Board Type***: `quanser_aero2`
+ ***Board Identifier***: `0@pspip://localhost:18930`

Su funcionamiento de bloques es el mismo, pero obviamente al ser diferente del Servo 2 las señales análogas, digítales, sensores, etc. Se adecuan al modelo.

Siendo sus principales diferencias:

+ 4 Señales de encoders, 2 por cada motor.
+ En los canales digitales los mismos que en el Servo 2 pero en este caso para cada motor.
+ En el campo de `Other Channels` es donde se encuentra la mayor diferencia con:
    + 3 Tacómetros, 2 para medir la velocidad de cada motor y otro midiendo también velocidad, pero en Jaw.
    + 3 giroscopios para medir velocidades en los ejes X, Y, Z.
    + 3 Acelerómetros para medir aceleraciones en los ejes X, Y, Z.

## Conclusión 

Quanser Interactive Labs se presenta como una solución robusta y escalable para la educación en ingeniería. Ofrece experiencias de laboratorio virtuales de alta fidelidad ("gemelos digitales") basadas en hardware industrial real.

La integración con Matlab, específicamente a través de Simulink permite a los usuarios configurar conexiones, enviar comandos y leer datos de sensores tanto de los modelos virtuales como de las plantas físicas. Los ejemplos del QUBE-Servo 3 y AERO 2 y permiten una visión de la realidad configurando identificadores específicos y utilizando los bloques adecuados para interactuar con las distintas características de cada sistema (motores, encoders, sensores de corriente, giroscopios, acelerómetros).

En resumen, la combinación de Quanser Interactive Labs y Matlab/Simulink proporciona un entorno completo y realista para aprender, simular y experimentar con sistemas de control.


## Bibliografía

Quanser. (2025). Quanser Interactive Labs for MATLAB. [Archivo]. Recuperado de https://www.mathworks.com/matlabcentral/fileexchange/123860-quanser-interactive-labs-for-matlab

Quanser. (2023). Qube-Servo 3. https://www.quanser.com/products/qube-servo-3/

Quanser. (2023). Qube-Aero 2. https://www.quanser.com/products/quanser-aero/