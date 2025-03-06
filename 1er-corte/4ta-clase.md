# Servomotores

Servo -> Esclavo
Servomecanismo -> Control de movimiento 

Posición, velocidad, torque (responde a)

## Variable a Controlar
    * Posición
    * Velocidad
    * Torque

Controlador -> Sistema Cascada
Driver de potencia -> Señal PWM
Servomotores -> Actuador

## Motores

    * DC
    * AC Inducción
    * AC Sincronos

## Corriente Continua (DC)
    Estator         rotor
    Parte fija      Parte Móvil 
    Rotor -> embobinado -> corriente y campo magnetico

### Aplicaciones
    * Motor DC -> Elementos Pequeños por el gran costo de potencia
    * En motores antiguos los cables de potencia eran gigantes.

## Motor AC Sincrono
    * Sistema de varios embobinados, en el rotor
    * En el estatro se usa embobinados o imanes
    * Modo de funcionamiento por imanes, se busca invertir la polaridad de estos y usando como alimentación señal trifasia.
    * Carros electricos usan este tipo de motores
    * Al no haber roce el desgaste es menor junto con las escobillas.
    * Para generar torques altos se requieren embobinados pequeños.

## Motor AC Asincrono (descarga)
    * Tanto rotor como estator tienen embobinados.
    * Menos eficiente y mas costoso que los sincronos.
    * Mas conocidos como motor de jaula de ardilla.
    * Según la forma del embobinado puede cambiar el valor de torque que puede generar.

## Ventajas y desventajas

### Motor DC 
#### Ventajas
    * Solo PWM
    * Driver de potencia simple
    * Precio bajo (Proyectos pequeños)

#### Desventajas
    * Mantenimiento Permanente
    * En entornos higienicos no es recomendado

### Motor de Inducción 
#### Ventajas
    * Robustos (Pares de embobinados)
    * Altas velocidades y torques

#### Desventajas
    * Motores grandes
    * Fuerza miníma 1 caballo de fuerza
    * Control mas complicado que un motor DC
    * Temperaturas y condiciones de humedad pueden oxidar el embobinado

### Motor Sincrono
#### Ventajas
    * Poco mantenimiento 
    * Ligero
    * Alta eficiencia

#### Desventajas
    * Dificultad intermedia
    * Necesidad de driver de potencia con respuesta 1:1
    * Los imanes se pueden desmagnetizar

wr -> Velocidad Nominal

## Sensores
* Posición y velocidad (encoder)
* Corrente (Torque)

### Encoder
    * Absoluto
    * Incremental

Nota: Todos los encoder incrementales pueden volverse absoluto por software.

### Resolver
    * Mantenimiento
    * Posible error en medición por razones mecánicas 

Nota: Efecto hall es cuando a un campo magnetico se le acercan ciertos elementos los cuales inducen una corriente y por consiguiente voltaje.