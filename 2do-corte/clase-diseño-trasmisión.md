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