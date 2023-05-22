# Laboratorio-5-Microcontroladores
Archivo README.md que describe el funcionamiento del programa, la manera en que compila y un diagrama que muestra como se configuró el hardware.

Este programa en ensamblador ARM de gnu hace funcionar un contador binario conformado por una tabla de desarrollo blue-pill stm32, 10 leds los cuales representaran la cuenta de nuestro programa en binario, y dos botones, los cuales al presionar uno la cuenta deberá aumentar en 1, al presionar el otro la cuenta deberá decrecer en 1 su valor y al presionar los 2 la cuenta deberá reiniciarse.

En la parte de set-up del codigo se habilita el reloj en el puerto A, se configuran los puertos 0 y 1 del puerto A como input para conectar los botones al sistema y se configuran los pines del 2 al 11 como output para conectar los leds al sistema.

El programa crea una variable para la almacenar el numero de la cuenta del sistema, despues en el ciclo "loop" el programa lee el estado de los botones y los pasa por una mascara para obtener el estado de cada boton por separado. almacena en los registros r1 y r2 el valor del estado de los botones.

Despues vienen las comparaciones con los registros r1 y r2 que almacenan el valor de los botones para determinar que debe hacer el sistema, primero compara si ambos botones estan presionados, si es asi, carga el contador y reinicia la cuenta; de caso contrario salta a la siguiente comparacion, si esta presionado el boton 1 carga el contador y aumenta la cuenta en 1; en caso contrario salta a la siguiente comparacion donde si fue presionado el boton 2 decrementa la cuenta en 1. al final de cada ciclo del loop se actualiza el estado de los leds con la cuenta del programa, se almacena el valor del contador con un desplazamiento de 2 bits en el registro GPIOA_ODR y se iluminan los leds correspondientes.

El codigo se compila y se transforma a un archivo.bin mediante los comandos arm-as2 blink.s -o blink.o y arm-objcopy2 -O binary blink.o blink.bin y se descarga el codigo en el microcontrolador con ayuda del programa STM32CubeProgrammer y la usb ST-LINK v2.

DIAGRAMA DE LA CONFIGURACION DEL HARDWARE:


