# Servomotores

El término **servo** proviene del latín *servus*, que significa esclavo. Un **servomecanismo** es un sistema de control de movimiento que ajusta automáticamente una variable a un valor deseado o sigue un objetivo en el tiempo. Estos sistemas responden a:

- **Posición**
- **Velocidad**
- **Torque**

## Variables a Controlar
Las principales variables que regulan los servomecanismos son:
- **Posición**: Control de orientación o desplazamiento angular/lineal.
- **Velocidad**: Regulación del ritmo de movimiento.
- **Torque**: Ajuste de la fuerza de giro aplicada.

### Componentes del Servomecanismo
Un servomecanismo está compuesto por:
- **Controlador**: Implementa un sistema en cascada para gestionar la respuesta.
- **Driver de potencia**: Modula la señal PWM para excitar el motor.
- **Servomotor**: Actuador que convierte la señal eléctrica en movimiento mecánico.

---

## Tipos de Motores
Los motores utilizados en servomecanismos pueden clasificarse en:

- **Motores de Corriente Continua (DC)**
- **Motores de Corriente Alterna (AC)**
  - **Motores de Inducción**
  - **Motores Síncronos**

---

## Motores de Corriente Continua (DC)
### Partes Principales
- **Estator**: Parte fija que contiene el devanado inductor, encargado de generar el campo magnético de excitación.
- **Rotor**: Parte móvil con un embobinado en el que circula corriente para inducir un campo magnético.
- **Colector de delgas**: Laminas de cobre conectadas al devanado inducido, permitiendo la conmutación de corriente.

### Aplicaciones
Los motores DC son ideales para aplicaciones donde se requiere un control preciso de velocidad y torque. Ejemplos:
- **Cintas transportadoras** (350kW)
- **Molienda de caña de azúcar** (746kW)

---

## Motores de Corriente Alterna (AC)
### **Motores Síncronos**
Los motores síncronos giran a una velocidad fija determinada por la frecuencia de la red de alimentación. 

#### Características:
- Utilizan un bobinado trifásico en el **estator** para generar un campo magnético giratorio.
- El **rotor** puede ser de imanes permanentes o bobinas excitadas con corriente continua.
- Funcionan con alimentación trifásica.
- No presentan desgaste por roce debido a la ausencia de escobillas.

#### Aplicaciones:
- **Bombas industriales** (2500 HP, 6600V)
- **Laminación siderúrgica** (3000 kW)

### **Motores Asíncronos** (Inducción)
En los motores asíncronos, el rotor gira a una velocidad menor que el campo magnético del estator debido al fenómeno del **deslizamiento**.

#### Características:
- El estator genera un campo magnético giratorio.
- El rotor induce corriente debido a la variación de flujo magnético.
- Existen dos tipos:
  - **Jaula de ardilla** (rotor simple y eficiente)
  - **Rotor bobinado** (mayor control de velocidad y torque)

#### Aplicaciones:
- **Bombas** (1267 HP)
- **Sopladores de aire** (630 kW)
- **Cintas transportadoras** (2788 HP)
- **Extractores de aire** (900 kW)

---

## Comparación de Motores

| Tipo de Motor | Ventajas | Desventajas |
|--------------|----------|-------------|
| **DC** | Control sencillo, Driver de potencia simple, Bajo costo en aplicaciones pequeñas | Mantenimiento constante, No apto para entornos limpios, No soporta altos torques |
| **Inducción (AC)** | Robustos, Alta velocidad y torque, Eficiencia en grandes aplicaciones | Control más complejo, Puede oxidarse con la humedad |
| **Síncrono (AC)** | Poco mantenimiento, Ligero y compacto, Alta eficiencia | Requiere driver de potencia con sincronización 1:1, Imanes pueden desmagnetizarse |

---

## Sensores en Servomecanismos
Para garantizar un funcionamiento preciso, los servomecanismos emplean sensores que miden:
- **Posición y velocidad** -> **Encoders**
- **Corriente (Torque)** -> **Sensores de efecto Hall o shunt**

### **Encoders**
- **Encoders Absolutos**: Proporcionan un código único de posición para cada giro completo.
- **Encoders Incrementales**: Generan pulsos proporcionales al movimiento angular.

**Nota:** Los encoders incrementales pueden convertirse en absolutos mediante software.

### **Resolver**
- Sensor analógico de posición angular.
- Funciona como un transformador con dos embobinados.
- Disponible con y sin escobillas.
- Voltajes de operación entre **2V RMS y 40V RMS**.
- Frecuencias entre **50 Hz y 20 kHz**.

---

### **Servomotores en Aerogeneradores**
En los aerogeneradores modernos, los servomotores son esenciales para optimizar la eficiencia en la generación de energía. Se utilizan para ajustar la orientación de las palas (control de paso) y la dirección de la góndola (control de guiñada), permitiendo que las turbinas se alineen correctamente con el viento y mantengan una velocidad de rotación adecuada. Este ajuste preciso maximiza la captación de energía y protege la estructura de condiciones adversas.

[**Referencia**](https://www.generaldrivermotor.com/motores/gdm-en-permanente-evolucion-en-permanente-adaptacion/)

### **Servomotores en Telescopios Robóticos**
Los telescopios robóticos utilizan servomotores para automatizar el seguimiento de objetos celestes, permitiendo observaciones precisas sin intervención humana constante. Estos sistemas ajustan la orientación del telescopio en tiempo real, compensando la rotación terrestre y otros factores, lo que es esencial para la investigación astronómica y la vigilancia espacial.

[**Referencia**](https://es.wikipedia.org/wiki/Telescopio_rob%C3%B3tico)
