# Control en Cascada

## ¿Qué es el Control en Cascada?

El control en cascada es una estrategia de control en la que se utilizan múltiples lazos de control anidados para mejorar el rechazo a perturbaciones y la estabilidad del sistema. 

### Características principales:
- Se usa cuando un solo lazo de control no es suficiente para estabilizar un proceso.
- El lazo interno controla una variable rápida y generalmente usa un controlador PI para evitar ralentización por acción derivativa.
- El lazo externo puede utilizar un controlador PI o PID, según la necesidad del sistema.
- Requiere la medición de más de una variable del proceso.
- Se usa en sistemas donde las perturbaciones afectan la salida.

---
## Métodos de Sintonización

### Metodologías disponibles:
- **Empíricas en lazo abierto**
- **Empíricas en lazo cerrado**
- **Basadas en modelos rigurosos**
- **Basadas en inteligencia computacional**

### Sintonización en Lazo Abierto

- Se realiza modelado de las variables principales y perturbaciones.
- El lazo interno trabaja de manera independiente y se comporta como un único bloque.
- El error en estado estacionario se elimina cuando la relación salida/entrada es 1.
- El retardo total del sistema se obtiene sumando los retardos individuales de los lazos.

#### Método de Austin (1986)
- Primero se sintoniza el lazo más rápido.
- Usa métodos convencionales de sintonización de PI y PID.
- Se determinan ecuaciones según el tipo de controlador deseado.
- Se obtiene la función de transferencia a partir de curvas de reacción.
- Durante la estabilización, el sistema opera por debajo del setpoint.

### Sintonización en Lazo Cerrado

#### Método de Relé
- Se usan el **período último** y la **ganancia última**.
- Se genera una oscilación con una señal cuadrada en el lazo secundario.
- Se miden el período de oscilación y la ganancia obtenida.
- Se ajusta el controlador secundario primero, luego el primario.

#### Método de Hang (1994)
- Usa pruebas en lazo cerrado con relé para sintonizar el sistema en cascada.
- Primero se sintoniza el lazo secundario y luego el primario.
- Se ajusta usando parámetros identificados en la oscilación inducida.

---
## Conclusiones

1. El control en cascada permite un mejor rechazo a perturbaciones y una respuesta más rápida en comparación con un solo lazo de control, lo que mejora la estabilidad y precisión del proceso.  
2. Para implementar un sistema de control en cascada, es necesario medir más de una variable del proceso, lo que puede aumentar la complejidad del sistema. 
3. Es fundamental que el lazo interno sea más rápido que el externo. Generalmente, el lazo interno usa un controlador PI o P para evitar retardos de la acción derivativa, mientras que el lazo externo puede utilizar un PI o PID según las necesidades del proceso.   

---

### Ejemplo: Control de Dosis de Cloro en un Tanque de Contacto

En un sistema de tratamiento de agua, el control de la dosis de cloro es esencial para garantizar la desinfección adecuada del agua. Un control cascada puede ser implementado de la siguiente manera:

- **Lazo Primario (Externo):** Control del nivel de cloro residual en la salida del tanque de contacto. Este lazo recibe una señal del monitor de calidad del agua en la salida del tanque y la compara con el punto de ajuste ingresado por el operador.
- **Lazo Secundario (Interno):** Control de la tasa de dosis de cloro en la entrada al tanque de contacto. Este lazo ajusta la bomba dosificadora o la válvula reguladora para mantener el punto de ajuste interno, medido por un monitor de calidad del agua en la entrada.

El lazo primario varía el punto de ajuste del lazo secundario, que a su vez ajusta la dosis de cloro para mantener los niveles deseados tanto en la entrada como en la salida del tanque de contacto. Este método es particularmente útil en procesos con tiempos de bucle largos, como en el tratamiento de agua, donde se pueden esperar tiempos superiores a 30 minutos.

[**Referencia**](https://www.sciencedirect.com/topics/engineering/cascade-control)

### Ejemplo: Control en Cascada de un Motor de Corriente Directa (DC)

En el control de posición de un motor de corriente directa (DC) con carga, se utiliza un sistema de control en cascada con tres lazos de control:

- **Lazo Interno (Rápido):** Control de corriente (torque). Este lazo mide la corriente del motor y ajusta el voltaje para mantener el torque deseado. La corriente se establece en cuestión de milisegundos, lo que permite eliminar perturbaciones rápidas.
- **Lazo Intermedio:** Control de velocidad. Este lazo mide la velocidad del motor, que es afectada por el torque de carga. El control de velocidad actúa en cuestión de segundos para rechazar perturbaciones de carga y ajusta el setpoint del lazo de corriente.
- **Lazo Externo (Lento):** Control de posición. Este lazo mide la posición del motor y ajusta el setpoint del lazo de velocidad para llevar el motor a la posición deseada. La posición es la variable más lenta del sistema.

Este sistema es típico en la industria para el accionamiento de máquinas modernas, donde se requiere un control preciso de corriente, velocidad y posición. Aunque en sistemas comerciales el controlador interno de corriente suele ser inaccesible para el usuario, es posible configurar los controladores de velocidad y posición a través de un computador.

[**Referencia**](https://controlautomaticoeducacion.com/control-realimentado/control-en-cascada/)
