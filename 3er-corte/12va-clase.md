# Continuación elementos de transmisión 

## Polea - Correa
Transmite movimiento rotacional entre dos ejes.

* ***Componentes***: Dos reudas (poleas) conectadas por una correa.
* ***Tipos***: Correas lisas o dentadas.
### Relación de Transmisión

La velocidad lineal de la correa es la misma en ambas poleas.

$r_1 * \omega_1 = r_2 * \omega_2$

### Inercia Reflejada

$J = \frac{W_{belt}}{g * \eta} * r^{2}_{ip}$

Donde:

* **$W_{belt}$**: Peso de la correa.
* **$\eta$**: Eficiencia.  
* **$r_{ip}**: radio de la polea impulsora.

### Torque de carga reflejado al motor

$T_{motor} = \frac{T_{carga}}{N*\eta}$

### Ventajas

* Simplicidad y económia.
* Fácil de montar y manterner
* Buena absorción de vibraciones.

### Desventajas

* Pérdidas por deslizamiento si no es dentada.
* Menor precisión que otros mecanismos.
* Menor eficiencia energética.

## Tornillo guía

Convierte movimiento rotacional en lineal.

### Tipos

* **Tonillo ACME** (más fricción).
    Eficiencia $35 - 85%$
* **Tornillo de Esfera** (más eficientes).
    Eficiencia $85 - 95%$

### Relación de transmisión

$\frac{d\theta}{dx} = \frac{2\pi}{p} y \frac{\dot{\theta}}{\dot{x}} = \frac{2\pi}{p}$

Donde $p$ es el paso (distancia lineal por revolución)

### Inercia Reflejada

$J_ref = m * (\frac{9}{2\pi})^2$

Donde $m$ es la masa de la carga.

### Torque de carga

$T = \frac{F * p}{2\pi*\eta}$

Donde: 
* **$F$**: Fuerza Lineal.
* **$p$**: Paso.
* **$\eta$**: Eficiencia.

### Ventajas

* Alta presición de posicionamiento.
* Puede soportar cargas pesadas.
* Buen control en desplazamientos lentos.

### Desventajas
* Alta fricción en tornillos ACME.
* Menor eficiencia si no es de bolas.
* Puede presentar desgaste con el tiempo.

## Piñón - Cremallera

Convierte la rotación del piñón en desplazamiente lineal de la cremallera.

### Relación de transmisión

$V_{rack} = r_{piñón} * \omega_{piñón} = N = \frac{\omega_{motor}}{v_{carga}}$

### Inercia reflejada

$J_ref = m * r^{2}$

### Torque de Carga

$T = \frac{F*r}{\eta}$

### Ventajas
* Alta rigidez y precisión.
* Ideal para movimientos largos.
* No hay deslizamiento como en las correas.

### Desventajas
* Puede tener juego mecánico (backlash).
* Requiere lubricación y mantenimiento.
* Costo más alto que polea-correa.

## Banda Transportadora

Genera movimiento lineal conitnuo a parti de una fuente rotacional (motor), mediante una banda apoyada sobre poleas.

### Relación de transmisión

$v_{belt} = r*\omega$
$N = \frac{\omega_{motor}}{v_{carga}} $

### Inercia reflejada
$J = (\frac{W_{belt}}{g*\eta})^{2}$

### Torque de carga
$T = \frac{F*r}{\eta}$

### Ventajas

* Excelente para transporte continuo.
* Bajo mantenimiento.
* Admite múltiples configuraciones.

### Desventajas

* No sirve para posicionamiento preciso.
* Se estiran con el tiempo (requieren tensado).
* Pueden presentar patinamiento.

## Conclusiones

1. La elección del mecanismo depende del tipo de movimiento que se requiere (rotacional o lineal) y de si se prioriza precisión, eficiencia o economía.

2. 
* **Polea-correa** es ideal para soluciones económicas con baja exigencia de precisión.
* **Tornillo guía** ofrece alta precisión para cargas pesadas pero con menor eficiencia.
* **Piñon-cremallera** combina precisión y alcance, pero a mayor costo.
* **Banda transportadora** es excelente para mover productors sin necesidad de control exacto de posición.

3. La inercia reflejada y el torque reflejado son claves para seleccionar el motor adecuado e ignorar esos factores pueden llevar a sobredimensionamiento o fallas en la aplicación.

4. Cada sistema tiene diferencias entre eficiencia, precisión y costo, por lo que su elección debe basarse en los requerimientos específicos del proyecto.

## Bibliografía

 + Cote, J. E. (2024). CONTROL DE MOVIMIENTO [Presentación]. Electiva de profundización 2 control de Movimiento, Universidad ECCI.