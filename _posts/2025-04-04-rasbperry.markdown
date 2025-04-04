---
layout: post
title: "Controlando la pierna de un robot humanoide con Raspberry Pi y C++"
date: 2025-04-04
categories: robotics raspberrypi c++
---

En este artículo, exploraremos cómo escribir un programa en C++ para mover la pierna de un robot humanoide utilizando una Raspberry Pi. Este ejemplo asume que el robot utiliza servomotores controlados mediante PWM.

## Código en C++

A continuación, se presenta un ejemplo básico:

```cpp
#include <wiringPi.h>
#include <softPwm.h>
#include <iostream>

#define SERVO_PIN 1 // Pin GPIO conectado al servomotor

void moveLeg(int angle) {
    if (angle < 0 || angle > 180) {
        std::cerr << "Ángulo fuera de rango (0-180 grados)." << std::endl;
        return;
    }
    int pulseWidth = (angle * 2000 / 180) + 500; // Convertir ángulo a ancho de pulso
    softPwmWrite(SERVO_PIN, pulseWidth / 100);  // Enviar señal PWM
}

int main() {
    if (wiringPiSetup() == -1) {
        std::cerr << "Error al inicializar WiringPi." << std::endl;
        return 1;
    }

    if (softPwmCreate(SERVO_PIN, 0, 200)) {
        std::cerr << "Error al configurar PWM." << std::endl;
        return 1;
    }

    std::cout << "Moviendo la pierna del robot..." << std::endl;
    moveLeg(90); // Mover a posición inicial
    delay(1000); // Esperar 1 segundo

    moveLeg(45); // Mover a 45 grados
    delay(1000);

    moveLeg(135); // Mover a 135 grados
    delay(1000);

    moveLeg(90); // Volver a posición inicial
    delay(1000);

    std::cout << "Movimiento completado." << std::endl;
    return 0;
}
```

## Explicación del Código

1. **Librerías**: Usamos `wiringPi` para controlar los pines GPIO de la Raspberry Pi.
2. **Configuración**: Configuramos el pin GPIO como salida PWM utilizando `softPwmCreate`.
3. **Función `moveLeg`**: Convierte un ángulo en un ancho de pulso adecuado para el servomotor.
4. **Secuencia de Movimiento**: Movemos la pierna a diferentes ángulos con pausas entre cada movimiento.

## Requisitos

- Raspberry Pi con `wiringPi` instalado.
- Servomotor conectado al pin GPIO especificado.
- Fuente de alimentación adecuada para el servomotor.

¡Prueba este código y ajusta los ángulos según las necesidades de tu robot humanoide!


