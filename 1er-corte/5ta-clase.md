# Apuntes de la Clase sobre Simscape

## Introducción a Simscape
- **Objetivo:**
  - Simular sistemas mecánicos y de control de movimiento.
  - Complementa lo visto en clases previas (modelamiento de motores, componentes eléctricos y mecánicos).

- **Aplicaciones:**
  - Simulación de robots, vehículos, mecanismos y sistemas híbridos (mecánicos, hidráulicos, eléctricos, neumáticos).
  - Ejemplos: diseño de suspensión de vehículos, simulación de ailerones en aviones.

---

## Simscape Multibody
- **Concepto:**
  - Permite modelar en 3D cada pieza de un mecanismo y ensamblarlas para simular su comportamiento dinámico.
  - Similar al trabajo en un software CAD, donde se crean bloques (cuerpos rígidos) interconectados mediante articulaciones.

- **Ventajas:**
  - Automatiza el cálculo de ecuaciones diferenciales para obtener posición, velocidad, aceleración, fuerzas y torques.
  - Genera animaciones 3D para visualizar el sistema en funcionamiento.
  - Permite la importación de modelos CAD (SolidWorks, Inventor, etc.) siempre que se respeten los marcos de referencia.

---

## Configuración del Entorno y Solvers
- **Bloques básicos en Simscape Multibody:**
  1. **Solver Configuration:**  
     - Encargado de generar y resolver las ecuaciones diferenciales del modelo.
  2. **Bloque del Mundo ("World"):**  
     - Define el marco de referencia global (ejes y gravedad).
  3. **Bloque de Leyes Físicas:**  
     - Configura parámetros físicos como la gravedad (ejemplo: vector de aceleración; se recomienda colocar la gravedad en el eje Y para facilitar el uso de articulaciones).

- **Métodos de Integración:**
  - **Paso Variable:**  
    - Ajusta automáticamente el intervalo de integración, aunque puede generar menos muestras si el salto es grande.
  - **Paso Fijo:**  
    - Por ejemplo, 0.001 s; permite obtener más puntos de solución y una mayor precisión, pero con mayor costo computacional.
  - La elección del integrador (como métodos trapezoidales o específicos para altas frecuencias) afecta la precisión de la simulación.

---

## Ejemplo Práctico: Simulación de un Péndulo
- **Modelo del Péndulo:**
  - Se modela una barra (representada como un sólido tipo cubo alargado) que simula un péndulo.
  - **Configuración del sólido:**  
    - Dimensiones definidas en los tres ejes (por ejemplo: 0.2 m en X, 0.5 m en Y, 0.05 m en Z).
    - Se definen propiedades como la densidad para calcular automáticamente masa e inercia.
    - Ajustes gráficos: color (configurado en RGB) y opacidad para visualizar la pieza.

- **Articulación de Revolución (Revolute Joint):**
  - Permite la rotación de la barra alrededor de un eje específico.
  - **Parámetros clave:**
    - **Puertos de conexión:**  
      - Base (b): origen del movimiento.  
      - Seguidor (f): eje que se mueve.
    - Configuración de la posición inicial (por ejemplo, -60°) para que, al soltar el péndulo, se genere movimiento.
    - Posibilidad de incorporar entradas externas (torques o velocidades) para modificar el movimiento.

- **Visualización y Medición:**
  - **Scopes y Data Inspector:**  
    - Permiten visualizar señales (como la función senoidal de la posición angular).
    - El Data Inspector ofrece herramientas para comparar diferentes corridas, hacer zoom y capturar imágenes.

---

## Buenas Prácticas y Consideraciones Adicionales
- **Organización del Modelo:**
  - Nombrar y marcar claramente cada bloque, especialmente en sistemas con múltiples articulaciones.
  - Disponer los bloques de manera lógica para facilitar el seguimiento y la configuración.

- **Configuración de Marcos de Referencia (Frames):**
  - Cada sólido tiene un marco de referencia, que por defecto se ubica en su centro de masa.
  - Es posible agregar y reposicionar estos marcos para definir correctamente el punto de unión y el eje de rotación.

- **Importación de Modelos CAD:**
  - Al importar modelos desde herramientas CAD, es fundamental respetar los marcos de referencia definidos en Simscape para evitar errores en la simulación.

---

## Conclusión
- **Simscape Multibody** es una herramienta para modelar y simular la dinámica de sistemas mecánicos y electrónicos complejos.
- Una correcta configuración del solver y la organización de los bloques garantizan resultados simulados y una visualización clara.
- La integración con Simulink y herramientas de análisis, como el Data Inspector, facilita la verificación y ajuste de la simulación.

