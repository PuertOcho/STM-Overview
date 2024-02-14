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

El pequeño tamaño, el bajo consumo y el bajo costo hacen de ARM un procesador ideal para aplicaciones
integradas. Los procesadores ARM se basan en un conjunto de instrucciones llamado **Thumb**. Con un diseño
inteligente, este conjunto de instrucciones toma instrucciones de 32 bits y las comprime a 16 bits, lo que reduce el
tamaño del hardware, lo que también reduce el costo general. Los procesadores ARM se basan en la
arquitectura RISC (Computadora con conjunto de instrucciones reducidas) y están disponibles como estructuras
multinúcleo de 32 o 64 bits. Los procesadores RISC, a diferencia de los procesadores CISC (computadora con
conjunto de instrucciones complejas), tienen una menor cantidad de instrucciones y menos transistores (por lo
tanto, un tamaño de matriz más pequeño), como resultado, pueden operar a velocidades más altas. Se eliminan las
instrucciones sin importancia o que no se utilizan con frecuencia y las rutas se optimizan para dar como resultado
un rendimiento superior.


