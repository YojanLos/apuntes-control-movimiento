# Elementos de Transmisión 

## Introducción a los Elementos de Transmisión

Los elementos de transmisión son componentes escenciales en sistemas mecánicos que permiten la transferencia de potencia y movimiento entre distintos mecanismos o partes de una máquina. 

### Diseño de transmisión 
![Diseño de transmisión](/Imagenes/diseñoTransmision.png)

## Requerimientos del Diseño

+ Asegurar que el torque ***a máxima velocidad*** del motor sea superior al requerido por la aplicación. Se recominenda usar un margen de seguridad.
+ Asegurar que se cumpla la inercia apropiada entre el motor y la carga.
+ Cumplir con cualquier criterio adicional como costo, precisión, ciclos de tiempo, etc.

## Posibles problemas de Diseño

| Tipo | Dado por | Encontrar / Dimensionar |
|------|----------|-------------------------|
|  1   | Movimiento de carga deseado | Transmisión y motor |
|  2   | Motor y transmisión existentes | Movimiento de carga resultante |
|  3   | Motor existente, movimiento de carga deseado | Transmisión |
|  4   | Movimiento de carga deseado, transmisión | Motor |

## Inercia y Torque reflejado 
+ Inercia **J** se define como la propiedad de un objeto de resistirse a cambios en su velocidad angular.
+ Por leyes de Newton  su comportamiento es $\sum T= J\alpha$
+ Por leyes de newton es posible concluir que la inercia es la contraparte rotacional de la masa.
+ El control de movimiento se acostumbra a denominar inercia para cualquier caso, rotacional o translación.

## Conceptos de transmisión ***Engranajes***

Los engranajes son fundamentales cuando se requiere precisión y control. Se clasifican según la orientación de sus dientes y el tipo de movimiento que transmiten:
+ **Cilíndros rectos:** Ejes paralelos.
+ **Helicoidales:** Transmisión más suave.
+ **Cónicos:** ejes que se cortan.
+ **Hipoide:** Para grandes reducciones de velocidad.

### Cálculo de Engranajes

![Relación de Engranes](/Imagenes/relacionEngranes.png)

#### Relación de transmisión

La relacion de transmisión $N_GB$ en un sistema de engranes compara la velociodad del motor con la velocidad de la carga:

+ **$\omega_m$:** Velocidad angular del motor
+ **$\omega_l$:** Velocidad angular de la carga

#### Velocidad Tangencial

Ambos engranes están en contacto, por lo tanto comparten la ***misma velocidad tangencial***:

$V_tangencial = \omega_m * r_m = \omega_l * r_l => \frac{\omega_m}{\omega_l} = \frac{r_l}{r_m}$

También puede expresarse en términos de número de dientes:

$\frac{n_l}{n_m} = \frac{r_l}{r_m} => N_GB = \frac{n_l}{n_m}$

#### Torque

Se utiliza la fórmula de potencia mecánica:

$P = T_m * \omega_m = T_l * \omega_l => \frac{\omega_m}{\omega_l} = \frac{T_l}{T_m}$

#### En conclusión

La relación de transmision puede expresarse de varias formas equivalentes:

$N_GB = \frac{\omega_m}{\omega_l} = \frac{r_l}{r_m} = \frac{n_l}{n_m} = \frac{T_l}{T_m}$

#### Ejemplo aplicado a SIM SCAPE

##### Modelamiento en SimScape
![Simulación SimScape Engranes](/Imagenes/simpscapeEngranes.jpg)

##### Resultado Simulación SimScape
![Resultado Simulación SimScape Engranes](/Imagenes/resultadoEngranes.jpg)

#### Cálculo de Inercia Reflejada $J_r$

La incercia reflejada es la cantidad de inercia que se le suma al motor debido a los componentes mecánicos conectados a él.

$ J_r = J_load * N_GB^2 donde NGB = \frac{\omega_m}{\omega_l}$

### Transmision Por Polea-Correas

Es un mecanismo que convierte movimiento rotacional en movimiento rotacional. Consta de dos ruedas y una correa que las conecta. La diferencia de radio de las ruedas determina la transformación de energía.
Se pueden encontrar diferentes tipos de poleas:

+ **Planas:** Para distancias grandes.
+ **Trapezoidales:** Mayor capacidad de transmisión
+ **Dentadas:** Evitan deslizamiento

#### Relación de transmisión 

#### Sistema por Banda entre dos Poleas
![Relación Transmisión Polea](/Imagenes/relacionTransmisionPolea.png)

+ Una Polea impulsora *Izquierda* de radio $r_ip$ y velocidad angular $\omega_ip$
+ Una polea impulsada *Derecha* de radio $r_lp$ y velocidad angular de $\omega_lp$

#### Velocidad Tangencial

Ambas estan unidad por una banda, por lo tanto, la ***velocidad tangencial*** en el punto de contacto debe ser la misma:

$V_tangencial = \omega_ip * r_ip = \omega_lp * r_lp$

#### Relación de Transmisión

A partir de la igualdad de velocidades tangenciales, se obtiene la ***relación de transmisión del sistema por banda (NBP):

$NBP = \frac{\omega_ip}{\omega_lp} = \frac{r_lp}{r_ip}$

La relación entre las velocidades angulares es **inversa** al radio de las poleas. Es decir, si la polea impulsora es mas pequeña que la impulsada, esta última girará mas lento.

#### Ejemplo aplicado en SimScape

##### Modelamiento en SimScape
![Simulación SimScape Poleas](/Imagenes/simpscapePoleas.jpg)

##### Resultado Simulación SimScape
![Resultado Simulación SimScape Poleas](/Imagenes/resultadoPoleas.jpg)

#### Cálculo de Inercia Reflejada $J_r$

$ J_r = J_load * N_GB^2 donde NGB = \frac{r_carga}{r_motor}$

### Transmisión por Cadenas

Alternativa entre correas y engranajes. Sin deslizamiento para alta potencia.

### Transmisión Tornillo Guía 

Este mecanismo convierte el **movimiento rotacional en lineal**.

#### Tipos 

+ **Tornillo ACME:** Mayor fricción, eficiencia entre **35% y 85%**
+ **Tornillo de bolas** *ball screw*: Reduce el backlash *juego mecánico* y fricción, eficiencia alta: **85% a 95%

#### Conversión de movimiento

Convierte **torque** del motor en fuerza sobre la carga

Está definido por dos parámetros:
+ Pitch *Cabeceo*: Revoluciones necesarias para mover 1 metro.
+ Lead *Paso*: Desplazamiento lineal por revolución.

#### Relación de transmisión:

$\frac{d\theta}{dx} = 2\pip y \frac{\.{\theta}}{x} = 2\pip

Donde $p$ es el paso del tornillo.


#### Cálculo de Inercia Reflejada $J_r$

$ J_r = m * (2\pip)^2 con p = pitch(revs/m)$

También puede incluir la inercia del tornillo mismo si tiene masa significativa.

### Transmisión Piñón - Cremallera

Sistema que convierte en ***traslación lineal*** mediante el acoplamiento de un engranaje *piñon* con una barra dentada *cremallera*

#### Transmisión 
$x = r_p * \theta_p => \.{x} = r_p * \omega_p$

Donde:
+ **$x:$** Desplazamiento lineal
+ **$r_p :$** Radio del piñón
+ **$\theta_p :$** Ángulo rotacional del piñón

#### Ventajas 
+ Alta rigidez
+ Presición para movimientos lineales largos


#### Cálculo de Inercia Reflejada $J_r$

$ J_r = m * r_p^2 donde r_p = radio del piñón$

### Banda Trasnportadora

Sistema para mover objetos mediante una banda sin fin conectada a un motor.

+ Movimiento lineal controlado por el rodillo conductor:
$x = r_b * \theta_b => \.{x} = r_b * \theta_b * \omega_b$
+ A menudo modelado igual que una **polea**, pero se considera la carga distribuida *peso* sobre la banda como parte de la inercia.


#### Cálculo de Inercia Reflejada $J_r$

$ J_r = m * r_b^2 donde r_b = radio del tambor/rodillo $

### Conclusión

Los sistemas de transmisión como **engranajes, poleas, tornillos, guía, piñón-cremallera** y **bandas transportadoras** permiten adaptar el movimiento del motor a las necesidades mecánicas de una carga.

Además del tipo de movimiento *rotacional o lineal*, se debe considerar la **inercia reflejada**, ya que esta afecta directamente el **demanda de torque del motor** y su **respuesta dinámica**. Un diseño mal dimensionado puede provocar sobrecalentamiento, vibraciones o errores de posicionamiento.
