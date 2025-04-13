# Perfiles de Movimiento 

Un perfil de movimiento describe la trayectoria que debe seguir un punto **"A"** hasta un punto **"B"**. Estos perfiles son fundamentales en sistemas automatizados y robóticos, ya que permiten controlar con precisión la posición, velocidad aceleración de los actuadores a lo largo del tiempo. Aunque el caso más simple implica el movimiento sobre un solo eje, en la práctica suelen coordinar múltiples ejes para ejecutar tareas complejas.

## Conceptos de Cinemática

La cinemática es el estudio del movimiento sin considerar las fuerzas que los causan. Se basan en tres variables principales: **Posición** *s(t)*, **Velocida** *v(t)* y **Aceleración** *a(t)*, todas como funciones del tiempo. Estas se realacionan mediante derivadas e integrales: la velocidad es la derivada de la posición y la aceleración es la derivada de la velocidad. Alternativamenete, la posición se puede obtener integrando la velocidad y la velocidad se obtiene integrando la aceleración.

### Fomulas Cinemática
![Fomulas Cinemática](/Imagenes/Formulas.png)

## Reglas Geométricas para el Cálculo de Movimiento

En perfiles de velocidad, el área bajo la curva representa la posición alcanzada, mientras que la pendiente de la curva de velocidad indica la aceleración. Estas relaciones geométricas permiten analizar el movimiento gráficamente y sirven como herramientas útiles para resolver problemas prácticos sin recurrir directamente a integrales o derivadas.

### Fomulas sin Derivadas/Integrales
![Fomulas sin Derivadas/Integrales](/Imagenes/ReglasGeometricas1.png)

## Perfiles de Movimiento Comunes

Existen dos perfiles ampliamente utilizados: el perfil trapezoidal y el perfil en S (curva sigmoidal). El perfil trapezoidal consta de tres etapas: aceleración constante, velocidad constante y desaceleración constante. Por su parte, el perfil en S suaviza los cambios entre etapas usando funciones cuadráticas, lo que reduce vibraciones y permite un control más suave del movimiento, siendo ideal para el movimiento precisos y sensibles.

## Análisis Analítico y Geométrico del Perfil Trapezoidal

Para analizar el perfil trapezoidal se utilizan fórmulas integrales que permiten calcular la posición en cada tramo del movimiento. Estas fórmulas varían segun el intervalo de tiempo analizado (aceleración, velocidad constante o desaceleración).

### Perfil Trapezoidal
![Perfil Trapezoidal](/Imagenes/PerfilTrapezoidal.png)

 También es posible obtener el tiempo total de movimiento y las distancias recorridas en cada etapa aplicando reglas geométricas sobre el gráfico de velocidad.

 ## Perfil Curva en S 

 El Perfil en S se modela mediante polinomios de segundo orden, con coeficientes ajustados a las condiciones de frontera. Este perfil mejora la suavidad del movimiento y es útil en aplicaciones donde se desea minimizar el impacto y desgaste mecánico. La obtención de la posición se realiza integrando la función de velocidad resultante del modelo cuadrático en cada segmento del perfil.

 ### Perfil Curva en S
 ![Perfil Curva en S](/Imagenes/PerfilCurvaS.png)

 ## Movimiento Multi-Eje

 En sistemas donde intervienen varios ejes, es fundamental coordinar sus movimientos. Existen tres estrategias principales: mover un eje a la vez, mover ambos ejes en paralelo ***slew motion***, o ajustar los movimientos para que inicien y terminen simultáneamente ***interpolated motion***. Esta última requiere calcular velocidades específicas para cada eje, en función del tiempo que toma el eje mas lento.

## Ejemplo

Se hizo el calculo un Perfil ***Curva en S*** a partir de los datos obtenidos en un efector final de un yugo escocés, los resultados obtenidos en 5 segundos fueron:

### Ejemplo Curva en S
![Ejemplo Curva en S](/Imagenes/ejemploCurvaS.png)

El movimiento empieza con una aceleración baja, luego acelera más rápido en la parte media, y finalmente desacelera suavemente al llegar a su destino.

La velocidad y la aceleración cambian de forma continua. Por lo que no muestra ningún quiebre o punto abrupto.

Se utilizo:
+ Desplazamiento máximo: ~0.1 m
+ Duración total del movimiento: ~4.8 s

El sistema se desplaza 10 cm en 5 segundos.


 ## Conclusión 

 El diseño y análisis de perfiles de movimiento es una herramienta escencial en el campo del control de movimiento. Permite garantizar trayectorias eficientes, suaves y seguras, tanto para movimientos simpes como complejos y multi-eje. El conocimiento de la cinemámtica es clave para el desarrollo de soluciones efectivas.
 