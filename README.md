# STM-Overview

Arquitectura interna de los procesadores STM32 Nucleo.
## Descripción general

Veremos un resumen de como es la arquitectura interna de los procesadores STM32 Nucleo, lo que nos permite desarrollar programas eficientes para nuestros proyectos. Para esta explicación se tiene como base el microcontrolador **STM-32L476RGT6**.

![](assets/20240214174745.png)

## Procesadores ARM

La elección de un microcontrolador en particular para el desarrollo de un proyecto depende de algunos factores como los siguientes:
- Costo
- Velocidad
- Consumo de energía
- Tamaño
- Número de puertos de entrada/salida digitales y analógicos
- Resolución y precisión del puerto analógico
- Tamaños de memoria del programa y datos
- Soporte de interrupciones
- soporte de temporizador
- Soporte USART
- Soporte de bus especial (por ejemplo, USB, CAN, SPI, I2C, etc.)
- Tensión de trabajo del microcontrolador

El pequeño tamaño, el bajo consumo y el bajo costo hacen de ARM un procesador ideal para aplicaciones integradas. Los procesadores ARM se basan en un conjunto de instrucciones llamado **Thumb**. Con un diseño inteligente, este conjunto de instrucciones toma instrucciones de 32 bits y las comprime a 16 bits, lo que reduce el tamaño del hardware, lo que también reduce el costo general. Los procesadores ARM se basan en la arquitectura RISC (Computadora con conjunto de instrucciones reducidas) y están disponibles como estructuras multinúcleo de 32 o 64 bits. Los procesadores RISC, a diferencia de los procesadores CISC (computadora con conjunto de instrucciones complejas), tienen una menor cantidad de instrucciones y menos transistores (por lo tanto, un tamaño de matriz más pequeño), como resultado, pueden operar a velocidades más altas. Se eliminan las instrucciones sin importancia o que no se utilizan con frecuencia y las rutas se optimizan para dar como resultado un rendimiento superior.

La familia Cortex consta de tres familias de procesadores: Cortex-M, Cortex-R y Cortex-A. Ahora veremos brevemente estas familias.
- La serie **Cortex-M** se basa en la arquitectura ARMv6-M (Cortex-M0 y Cortex-M0+) y en la ARMv7-M (Cortex-M3 y Cortex-M4), diseñadas específicamente para el mercado de microcontroladores. Estos procesadores ofrecen respuestas rápidas y deterministas a interrupciones, bajo consumo de energía, bajo costo, un rendimiento bastante alto y facilidad de uso. Los Cortex-M3 y Cortex-M4 tienen arquitecturas muy similares y comparten el mismo conjunto de instrucciones (Thumb 2), diferenciándose en que el Cortex-M4 incluye capacidades de procesamiento de señales digitales (DSP) y una unidad de punto flotante opcional (FPU).
- La serie **Cortex-R** incluye procesadores de alto rendimiento en tiempo real, superiores a los de la serie Cortex-M, algunos de los cuales están diseñados para operar a altas frecuencias de reloj de más de 1 GHz. Son comúnmente utilizados en controladores de discos duros, dispositivos de red, aplicaciones automotrices y en aplicaciones especializadas de microcontroladores de alta velocidad. Su alto consumo de energía los hacen inadecuados para dispositivos móviles alimentados por baterías.
- Los procesadores **Cortex-A** son los de mayor rendimiento de ARM, diseñados para sistemas operativos en tiempo real en aplicaciones móviles como teléfonos móviles, tabletas, dispositivos GPS, etc. Soportan características avanzadas para sistemas operativos como Android, iOS, Linux, Windows, etc., y una gestión avanzada de la memoria con memoria virtual. Los miembros más recientes ofrecen bajo consumo y muy alto rendimiento, construidas sobre la arquitectura ARMv8-A, que ofrece una operación eficiente de 64 bits y la capacidad de manejar más de 4 GB de memoria física.

### Comparación entre distintos Cortex-M

| Procesador  | Descripción                                                                                      |
|-------------|--------------------------------------------------------------------------------------------------|
| Cortex-M7   | Procesador de alto rendimiento, utilizado en aplicaciones donde el Cortex-M4 no es suficientemente rápido, soporta DSP y aritmética de precisión simple y doble. |
| Cortex-M4   | Arquitectura similar al Cortex-M3 pero incluye DSP y aritmética de punto flotante, utilizado en aplicaciones de microcontroladores de alta gama. |
| Cortex-M3   | Muy popular, bajo consumo de energía, rendimiento medio, características de depuración, utilizado en aplicaciones de tipo microcontrolador. |
| Cortex-M1   | Diseñado principalmente para aplicaciones de matriz de puertas programables.                     |
| Cortex-M0+  | Menor consumo de energía y mayor rendimiento que el Cortex-M0.                                    |
| Cortex-M0   | Bajo consumo de energía, rendimiento de bajo a medio, el procesador Arm más pequeño.              |
