# ADRC

## ¿QUÉ ES ADRC?

+ Una alternativa "reciente" al control PID, para rechazar perturbaciones activamente.
+ No depende de un modelo exacto de la planta (Función de transferencia), solo necesita conocer el orden del sistema y la ganacia nominal.
+ Habla del concepto de ***Perturbación total*** que incluye incertidumbres del modelo más perturbaciones externas

### Componentes del ADRC

1. ***Generador de trayectorias***: Crea perfiles de movimiento deseado.
2. ***Observador de Estado Extendido (ESO)***: Estima estados del sistema + perturbaciones.
3. ***Controlador de retroalimentación de estados***: Aplica una ley de control para corregir el sistema.

![Componentes ADRC](/Imagenes/componentesADRC.png)

## Enfoque (Gao, 2014)

* Estima dinámicas desconocidas y perturbaciones en una sola señal.
* Induce al sistema a comportarse como una planta nominal más fácil de controlar.
* Existen variantes como LADRC (lineal) y NADRC (no lineal), dependiendo de la complejidad del sistema.

### Tipos de ADRC

1. LADRC (Lineal)
    * Usa observadores y leyes de control **lineales**
    * Es más fácil de implementar en sistemas que se pueden linealizar.

2. NADRC (No Lineal)
    * Se usan cuando el sistema es inherentemente no lineal.
    * Se modela la perturbación como un estado adicional.

## Observador de estado Extendido (ESO)

* Estima no solo los estados normales del sistema, sino también las perturbaciones.

* Se usa un **Observador tipo Luenberger** y se ubican los polos en el semiplano izquierdo (criterio de estabilidad de Hurwitz).

## Comparación con PID

Según las pruebas de desempeño comparando ADRC con PID se encuentra que:

### PID
![Comparación 1 PID](/Imagenes/pruebas1PID.png)
![Comparación 1 PID](/Imagenes/pruebas2PID.png)

### ADRC
![Comparación 1 ADRC](/Imagenes/pruebas1ADRC.png)
![Comparación 1 ADRC](/Imagenes/pruebas2ADRC.png)

* **ADRC tiene mejor rechazo a perturbaciones y robustez** ante cambios de parámetros.
*  ADRC puede manejar entradas complejas (rampa, senoidal, etc.) y perturbaciones diversas.


## Conclusiones

* ADRC mejora la robustez del control al estimar y cancelar perturbaciones.
*  No requiere conocer exactamente el modelo del sistema.
*  Es especialmente útil en sistemas no lineales, ruidosos o sujetos a incertidumbres.

## Bibliografía

 + Cote, J. E. (2024). CONTROL DE MOVIMIENTO [Presentación]. Electiva de profundización 2 control de Movimiento, Universidad ECCI.