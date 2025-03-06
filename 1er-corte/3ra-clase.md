# Control Cascada

## ¿Qué es el Control Cascada?

* El control cascada busca rechazar todas las pertubaciones que pueda tener la variable de proceso.

* El control cascada se usa en casos donde un solo lazo de control no es suficiente.

* El lazo interno siempre va a ser la varaible mas rapida, se recomientda  que el control que se use sea PI, el PID no es una opción porque la acción derivativa vuelve lenta la respuesta.

* El lazo externo puede usar un PI o PID, según lo que se desee hacer con la carga.

* Para poder hacer un control cascada debe ser posible medir mas variables además de la variable a controlar.

* El control cascada se usa cuando las perturbaciones afectan la salida.

## Métodos de sintonización

    + Empiricos lazo abierto
    + Lazo cerrado
    + Módelo Riguroso
    + Inteligencia Computacional

### Lazo Abierto

    * Hacer el modelamiento de todas las variables, la pricipal y las variables de pertubaciones 
    * El lazo secundario trabaja completamente independiente (interno)
    * El lazo interno se comporta como un único bloque (Diagrama de bloque)
    * Cuando se elimina el error de estado estacionario, la relación de salida/entrada sería igual a 1.
    * El retardo del primer lazo se suma con el segundo lazo para hallar el tiempo muerto del sistema
    * El Tau resultante es el Tau del sistema más lento

#### Método de Austin
    * El primer lazo a sintonizar es el lazo mas rápido (igual que el anterior)
    * Utiliza los esquemas conocidos de sintonización de PID, por lo que solo será PI y PID como control resultante.
    * En la tabla de ecuaciones se indentifica que se desaea hacer, si se quiere un PI se tomaran las ecuaciones que esten debajo de este, pasa lo mismo para el PID.
    * Se grafican las señales y usando métodos de indentificación de curva de reacción se obtienen las funciones de transferencia.
    * Algo característico del control cascada es que suele trabajar por debajo del setpoint hasta que se estabiliza 

### Lazo Cerrado 

#### Método de Rele
        * Las variables usadas son periodo último y ganacia última.
        * Se sintoniza el lazo secundario por medio de un rele, es genera una señal cuadrarda haciendo oscilar el sistema en rangos seguros, ejemplo 25% y 75%.
        * En gráfica se mide el periodo (periodo último) y la ganancia de la señal (ganancia última).
        *Epsilón es la amplitul que puede tener el rele