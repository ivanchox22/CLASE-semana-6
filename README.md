# APUNTES SEMANA 7

# 1. Definición de Movimiento de Perfil

Un perfil de movimiento se define como la representación detallada del desplazamiento que realiza un sistema mecánico, o uno de sus componentes, desde un punto inicial (comúnmente denominado punto A) hasta un punto final (punto B). Esta representación incluye no solo la distancia recorrida, sino también cómo evolucionan en el tiempo los parámetros asociados al movimiento, tales como la posición, la velocidad y la aceleración. El diseño del perfil es crucial porque de él depende la eficiencia del sistema, la vida útil de los componentes mecánicos, y el cumplimiento de tareas específicas dentro de un proceso automatizado.

Dependiendo del tipo de sistema y de la aplicación, el perfil de movimiento puede involucrar desde un solo eje de desplazamiento hasta múltiples ejes que actúan de manera simultánea y coordinada. En el caso de un solo eje en movimiento, el perfil resulta sencillo de analizar y controlar, ya que la trayectoria es lineal y las variaciones cinemáticas afectan a un único componente. Este tipo de perfil se conoce como **movimiento uniaxial**, y es ideal para aplicaciones básicas donde se requiere un desplazamiento simple y directo.

Por otro lado, existen escenarios más complejos en los cuales se deben controlar varios ejes al mismo tiempo para lograr desplazamientos en múltiples direcciones o seguir trayectorias específicas. Este tipo de desplazamiento se denomina **movimiento multiaxial**. En estos casos, la complejidad del perfil de movimiento aumenta considerablemente, ya que es necesario evaluar las variaciones simultáneas de posición, velocidad y aceleración en cada uno de los ejes involucrados. El correcto diseño de estos perfiles es vital para evitar colisiones, maximizar la precisión y garantizar un comportamiento fluido del sistema.

# 2. Fundamentos de la Cinemática Aplicada al Movimiento

Para entender cómo se generan y analizan los perfiles de movimiento, es imprescindible dominar los conceptos básicos de la **cinemática**, que es la rama de la mecánica que estudia el movimiento sin considerar las fuerzas que lo causan. En este contexto, los tres parámetros más importantes son: **la posición, la velocidad y la aceleración**, cada uno con un papel específico en la descripción del comportamiento dinámico de un sistema.

**La posición** \( x(t) \) representa la localización de un punto específico del sistema (como el extremo de un brazo robótico o el centro de masa de una plataforma móvil) en función del tiempo. Es el parámetro más intuitivo y fundamental, ya que define "dónde" se encuentra el sistema en cada instante.

**La velocidad** se define como la derivada de la posición con respecto al tiempo, es decir, indica la rapidez con la que cambia la posición en un intervalo temporal dado. Matemáticamente, se expresa como:

```
v(τ) = dχ / dτ
```

Donde \( χ \) representa la posición y \( τ \) el tiempo. La velocidad permite calcular la distancia total recorrida a lo largo del tiempo integrando su valor:

```
s = ∫ v(τ) dτ
```

**La aceleración** representa el cambio de la velocidad con respecto al tiempo y se expresa como:

```
a(τ) = dv / dτ
```

Cuando se tiene una función de aceleración en el tiempo, se puede calcular indirectamente la posición integrando dos veces, primero para obtener la velocidad y luego para obtener la posición. Esto es muy útil en escenarios donde se controla directamente la aceleración, como en sistemas de control de motores.

La interpretación gráfica de estos conceptos también es esencial: el **área bajo la curva de velocidad** en una gráfica representa el **desplazamiento total**; mientras que la **pendiente de la curva de velocidad** en un punto dado indica el valor de la **aceleración en ese instante**.

![Image](https://github.com/user-attachments/assets/4bf5b949-b4a1-4dd7-a591-54e74619cd19)

***Fig 1. Grafica posicion, velocidad y aceleraciòn***

# 3. Principios Geométricos y Ecuaciones de Movimiento

En el diseño y análisis de perfiles de movimiento, existen ciertos principios geométricos que deben respetarse para asegurar un comportamiento mecánico coherente y predecible. Entre estos principios se destaca que el área bajo la curva de velocidad siempre representa el desplazamiento neto de un sistema en un intervalo de tiempo determinado. Asimismo, la aceleración se puede visualizar como la pendiente de la curva de velocidad en una gráfica velocidad-tiempo, lo cual facilita su interpretación visual.

Las ecuaciones fundamentales que describen el movimiento en sistemas con aceleración constante son:

```
v = v₀ + a(t - t₀)
s = s₀ + ½(t - t₀)(v₀ + a(t - t₀))
```

Aquí, \( t₀ \) representa el tiempo inicial, \( v₀ \) la velocidad inicial y \( s₀ \) la posición inicial del sistema. Estas expresiones permiten calcular la velocidad final y la posición final de un objeto en función del tiempo y la aceleración, y son ampliamente utilizadas tanto en simulaciones como en cálculos manuales.

---
💡 ***EJEMPLO 1***

* Encuentre a posicion y la aceleraciòn en t= 5s, para esto tener en cuenta la figura 2.

![Image](https://github.com/user-attachments/assets/33e490ef-ed86-473f-98a7-3875390ef21c)

***Fig 2. Encontrar la posiciòn y aceleraciòn***

***SOLUCION***

* La aceleración sería la pendiente de la velocidad como se muestra en la siguiente ecuacion:

```
a = 10/5
a = 2in/s^2
```

* El área bajo la curva de velocidad es hasta t=5 s es la posición alcanzada en t=5 s

```
s = ½(10*5)
s = 25in/s
```
  
---

---
💡***EJEMPLO 2***

* Un eje está viajando a una velocidad de 10 cm/s. En t=5 s empieza a disminuir la velocidad como se ve en el perfil. Cual es la posición del eje cuando se detiene? Asuma que empieza a desacelerar a 25 cm

![Image](https://github.com/user-attachments/assets/3bdf018d-65af-43e5-90c7-cfedbd7703bd)

***Fig 3. Encontrar la posiciòn y aceleraciòn***

***SOLUCION***

* La pendiente de la velocidad es la aceleración como se muestra en la siguiente ecuacion:

$a=\frac{-10cm/s * (1m/100cm)}{15s - 5s}$

$a=\frac{-0.1m/s}{10s}$

$a=\frac{-0.1m/s}{10s^2}$

* El área bajo la curva de velocidad es hasta t=5 s es la posición alcanzada en t=5 s

```
s = ½(15s-5s)*0.1m/s = 0.5m

```
  
---

# 4. Tipos de Perfiles de Movimiento

En la práctica, los sistemas mecatrónicos emplean diferentes tipos de perfiles de movimiento, dependiendo del tipo de tarea a ejecutar y del grado de suavidad o rapidez requerido. Entre los perfiles más comunes destacan el **perfil trapezoidal** y el **perfil en S**.

## Perfil Trapezoidal

Este perfil recibe su nombre debido a la forma trapezoidal que adopta su gráfica de velocidad respecto al tiempo. Se compone de tres fases principales:

1. Una etapa de **aceleración constante**.
2. Una etapa donde la **velocidad se mantiene constante**.
3. Una etapa donde el sistema **desacelera de forma constante**.

Este tipo de perfil es bastante común en sistemas de control de motores paso a paso o servomotores debido a su simplicidad de implementación. Aunque no es el más suave desde el punto de vista dinámico, ofrece un buen equilibrio entre rapidez y control, lo que lo convierte en una opción eficiente para múltiples aplicaciones industriales.

***PERFIL TRAPEZOIDAL***
![image](https://github.com/user-attachments/assets/b782815d-90bc-4b90-a637-f116d8cbd46f)
***Fig 4. Grafica de perfil trapezoidal***

---
💡***EJEMPLO 3***
* El eje x de un robot Gantry debe moverse 10 cm. La máxima aceleración permitida en este eje es 1 cm/s^2. Si se desea mover el eje a una velocidad máxima de 2 cm/s, cuanto tiempo tomará hacer este movimiento

![image](https://github.com/user-attachments/assets/d0a860f7-c048-40b7-97bb-086e54114acb)
***Fig 5. ejemplo perfil trapezoidal***

```
Ta = Td = Vm/a = (2cm/s)/(1 cm/s^2) = 2s
Tm = L/Vm - Ta = (10cm / 2cm/s) -2s = 3s

```

---


## Perfil en S

El perfil en S es una evolución del perfil trapezoidal, diseñado para minimizar los cambios bruscos en la aceleración, los cuales pueden generar vibraciones, esfuerzos mecánicos innecesarios o desgaste prematuro de componentes. Este perfil introduce transiciones suaves en la aceleración y la desaceleración mediante rampas progresivas, lo que da lugar a una curva con forma de "S" en la gráfica de velocidad.

Este tipo de perfil puede representarse mediante funciones polinómicas, siendo una expresión común:

```
v(t) = C₁t² + C₂t + C₃
```

Donde los coeficientes \( C₁, C₂ \) y \( C₃ \) se determinan a partir de las condiciones iniciales y finales del sistema. El perfil en S es ideal para aplicaciones que requieren movimientos muy suaves, como sistemas de transporte automatizado, robots colaborativos o máquinas de alta precisión.

# 5. Movimiento Multieje Coordinado

En muchas aplicaciones modernas, los sistemas requieren desplazamientos que no pueden ser logrados con un solo eje en movimiento. Es aquí donde entra en juego el **movimiento multieje**, el cual consiste en la sincronización de dos o más ejes para ejecutar trayectorias complejas en el espacio tridimensional.

## Tipos de Movimiento Multieje

- **Movimiento Secuencial:** Cada eje realiza su desplazamiento de forma independiente y en un orden específico. Este tipo de movimiento es fácil de programar y controlar, aunque suele ser lento debido a la falta de simultaneidad.

- **Movimiento Coordinado:** Varios ejes se mueven al mismo tiempo siguiendo una trayectoria conjunta. Este tipo de movimiento permite una mayor eficiencia, ya que reduce el tiempo de ejecución y mejora la fluidez del desplazamiento.

- **Interpolación Multieje:** En este caso, el sistema calcula puntos intermedios a lo largo de una trayectoria deseada. Existen diferentes tipos de interpolación:
  - **Lineal**, que sigue trayectorias rectas.
  - **Circular**, usada en trayectorias curvadas.
  - **Helicoidal**, que combina un movimiento circular con traslación.
  - **Spline**, que utiliza curvas suaves polinómicas para trayectorias complejas.

Este tipo de movimiento es ampliamente utilizado en maquinaria CNC, robots industriales, impresoras 3D y sistemas de automatización avanzada.

# 6. Ejercicios

---
***Ejercicio 1***

* Encuentre a posicion y la aceleraciòn en t= 6s

***SOLUCION***

* La aceleración sería la pendiente de la velocidad como se muestra en la siguiente ecuacion:

```
a = 12/6
a = 2in/s^2
```

* El área bajo la curva de velocidad es hasta t=5 s es la posición alcanzada en t=5 s

```
s = ½(12*6)
s = 36in/s
```
  
---

---
***Ejercicio 2***

* Un eje está viajando a una velocidad de 15 cm/s. En t=3 s empieza a disminuir la velocidad como se ve en el perfil.
\

***SOLUCION***

* La pendiente de la velocidad es la aceleración como se muestra en la siguiente ecuacion:

$a=\frac{-15cm/s * (1m/100cm)}{9s - 3s}$

$a=\frac{-0.15m/s}{6s}$

a= -0.025m/s^2

* El área bajo la curva de velocidad:

```
s = ½(9s-5s)*0.15m/s = 0.45m

```
  
---

# 7. Conclusiones

El análisis y diseño de perfiles de movimiento representa una competencia clave dentro del campo de la ingeniería mecatrónica, ya que permite comprender cómo se desplazan, aceleran y detienen los sistemas automatizados en diversas condiciones. Más allá de una simple representación gráfica, los perfiles de movimiento constituyen herramientas esenciales para garantizar la seguridad operativa, la precisión funcional y la eficiencia energética de los mecanismos en movimiento.

A lo largo del estudio realizado, se evidenció que el dominio de conceptos como posición, velocidad y aceleración no solo permite describir matemáticamente un movimiento, sino también predecir su comportamiento ante cambios en las condiciones iniciales o en la configuración de los sistemas. Esto cobra especial importancia cuando se abordan perfiles complejos, como los de tipo multieje, donde la sincronización entre componentes se convierte en un factor crítico de éxito.

Por otra parte, la simulación mediante herramientas como Simscape proporciona un entorno seguro, versátil y altamente visual para experimentar con diferentes configuraciones de movimiento, facilitando la identificación de errores, la optimización de trayectorias y la toma de decisiones de diseño. Esta capacidad de previsualización aporta un valor significativo al proceso de ingeniería, al reducir tiempos de prueba y aumentar la confianza en los resultados obtenidos.

Finalmente, este conocimiento no solo fortalece la formación académica, sino que habilita al estudiante para enfrentar retos del mundo real, desde la programación de trayectorias en robots industriales hasta el desarrollo de sistemas de automatización de alta precisión. Comprender y dominar los perfiles de movimiento es, en esencia, dar un paso firme hacia la innovación tecnológica con base en principios científicos y herramientas digitales de vanguardia.

# 8. Referencias

### Referencias

1. Groover, M. P. (2016). *Automation, Production Systems, and Computer-Integrated Manufacturing* (4th ed.). Pearson Education.  
   [ISBN: 9780133499612]

2. Craig, J. J. (2005). *Introduction to Robotics: Mechanics and Control* (3rd ed.). Pearson Prentice Hall.  
   [ISBN: 9780201543612]

3. Bolton, W. (2015). *Mechatronics: Electronic Control Systems in Mechanical and Electrical Engineering* (6th ed.). Pearson Education.  
   [ISBN: 9781292076683]

4. Zatsiorsky, V. M. (1998). *Kinetics of Human Motion*. Human Kinetics.  
   [ISBN: 9780880116761]
