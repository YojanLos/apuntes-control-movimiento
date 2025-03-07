# Control Cascada

## ¿Qué es el Control Cascada?

- El control cascada busca rechazar todas las perturbaciones que pueda tener la variable de proceso.
- Se utiliza en casos donde un solo lazo de control no es suficiente.
- El lazo interno siempre es la variable más rápida. Se recomienda usar un control PI, ya que el PID no es una opción debido a que la acción derivativa vuelve lenta la respuesta.
- El lazo externo puede usar un PI o PID, dependiendo de lo que se desee hacer con la carga.
- Para implementar un control cascada, es necesario medir más variables además de la variable a controlar.
- Este tipo de control se usa cuando las perturbaciones afectan directamente la salida.

## Métodos de Sintonización

- **Empíricos (Lazo Abierto)**
- **Lazo Cerrado**
- **Modelo Riguroso**
- **Inteligencia Computacional**

### Lazo Abierto

- Se realiza el modelamiento de todas las variables, tanto la principal como las variables de perturbaciones.
- El lazo secundario (interno) trabaja de manera completamente independiente.
- El lazo interno se comporta como un único bloque en el diagrama de bloques.
- Cuando se elimina el error de estado estacionario, la relación de salida/entrada es igual a 1.
- El retardo del primer lazo se suma con el segundo lazo para hallar el tiempo muerto del sistema.
- El Tau resultante es el Tau del sistema más lento.

#### Método de Austin

- El primer lazo a sintonizar es el más rápido.
- Utiliza esquemas conocidos de sintonización de PID, por lo que solo se obtienen controles PI o PID.
- En la tabla de ecuaciones, se identifica qué tipo de control se desea (PI o PID) y se toman las ecuaciones correspondientes.
- Se grafican las señales y, usando métodos de identificación de curva de reacción, se obtienen las funciones de transferencia.
- Una característica del control cascada es que suele trabajar por debajo del setpoint hasta que se estabiliza.

### Lazo Cerrado

#### Método de Rele

- Las variables utilizadas son el periodo último y la ganancia última.
- Se sintoniza el lazo secundario mediante un relé, el cual genera una señal cuadrada haciendo oscilar el sistema en rangos seguros (por ejemplo, entre 25% y 75%).
- En la gráfica, se mide el periodo (periodo último) y la ganancia de la señal (ganancia última).
- Epsilon es la amplitud que puede tener el relé.

---

### Ejemplo 7: Control de Dosis de Cloro en un Tanque de Contacto

En un sistema de tratamiento de agua, el control de la dosis de cloro es esencial para garantizar la desinfección adecuada del agua. Un control cascada puede ser implementado de la siguiente manera:

- **Lazo Primario (Externo):** Control del nivel de cloro residual en la salida del tanque de contacto. Este lazo recibe una señal del monitor de calidad del agua en la salida del tanque y la compara con el punto de ajuste ingresado por el operador.
- **Lazo Secundario (Interno):** Control de la tasa de dosis de cloro en la entrada al tanque de contacto. Este lazo ajusta la bomba dosificadora o la válvula reguladora para mantener el punto de ajuste interno, medido por un monitor de calidad del agua en la entrada.

El lazo primario varía el punto de ajuste del lazo secundario, que a su vez ajusta la dosis de cloro para mantener los niveles deseados tanto en la entrada como en la salida del tanque de contacto. Este método es particularmente útil en procesos con tiempos de bucle largos, como en el tratamiento de agua, donde se pueden esperar tiempos superiores a 30 minutos.

[**Referencia**](https://www.sciencedirect.com/topics/engineering/cascade-control)  

### Ejemplo 9: Control en Cascada de un Motor de Corriente Directa (DC)

En el control de posición de un motor de corriente directa (DC) con carga, se utiliza un sistema de control en cascada con tres lazos de control:

- **Lazo Interno (Rápido):** Control de corriente (torque). Este lazo mide la corriente del motor y ajusta el voltaje para mantener el torque deseado. La corriente se establece en cuestión de milisegundos, lo que permite eliminar perturbaciones rápidas.
- **Lazo Intermedio:** Control de velocidad. Este lazo mide la velocidad del motor, que es afectada por el torque de carga. El control de velocidad actúa en cuestión de segundos para rechazar perturbaciones de carga y ajusta el setpoint del lazo de corriente.
- **Lazo Externo (Lento):** Control de posición. Este lazo mide la posición del motor y ajusta el setpoint del lazo de velocidad para llevar el motor a la posición deseada. La posición es la variable más lenta del sistema.

Este sistema es típico en la industria para el accionamiento de máquinas modernas, donde se requiere un control preciso de corriente, velocidad y posición. Aunque en sistemas comerciales el controlador interno de corriente suele ser inaccesible para el usuario, es posible configurar los controladores de velocidad y posición a través de un computador.

#### Referencias:
- [**Referencia**](https://controlautomaticoeducacion.com/control-realimentado/control-en-cascada/)  