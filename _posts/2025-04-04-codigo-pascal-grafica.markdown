---
layout: post
title: "Código Pascal: Dividir Imagen PNG en Cinco Partes y Mostrar Intermitentemente"
date: 2025-04-04
categories: pascal graphics
---

En este artículo, exploraremos cómo escribir un programa en Pascal que cargue una imagen PNG desde un directorio, la divida en cinco partes verticales y las muestre intermitentemente cada 0.2 segundos.

### Código en Pascal

A continuación, se presenta el código:

```pascal
program DividirImagen;

uses
    Graph, SysUtils, Crt;

const
    DelayTime = 200; // Tiempo de espera en milisegundos

var
    gd, gm: Integer;
    ImagePath: String;
    ImgWidth, ImgHeight, PartWidth: Integer;
    i: Integer;
    Image: Pointer;

begin
    // Inicializar gráficos
    gd := Detect;
    InitGraph(gd, gm, '');

    if GraphResult <> grOk then
    begin
        Writeln('Error al inicializar el modo gráfico.');
        Halt(1);
    end;

    // Ruta de la imagen
    ImagePath := 'imagen.png';

    // Cargar la imagen
    if not FileExists(ImagePath) then
    begin
        Writeln('La imagen no existe en el directorio especificado.');
        CloseGraph;
        Halt(1);
    end;

    // Simulación de carga de imagen (reemplazar con librerías específicas si es necesario)
    ImgWidth := GetMaxX; // Ancho de la imagen
    ImgHeight := GetMaxY; // Alto de la imagen
    PartWidth := ImgWidth div 5; // Ancho de cada parte

    // Bucle para mostrar las partes intermitentemente
    for i := 0 to 4 do
    begin
        ClearDevice;
        // Simulación de recorte y visualización de cada parte
        Rectangle(i * PartWidth, 0, (i + 1) * PartWidth, ImgHeight);
        Delay(DelayTime);
    end;

    // Finalizar gráficos
    CloseGraph;
end.
```

### Explicación del Código

1. **Inicialización de gráficos**: Se utiliza la unidad `Graph` para trabajar con gráficos en Pascal.
2. **Carga de la imagen**: El programa simula la carga de una imagen PNG. Para trabajar con imágenes reales, se necesitaría una biblioteca adicional como `GraphiX` o `SDL`.
3. **División de la imagen**: La imagen se divide en cinco partes verticales calculando el ancho de cada sección.
4. **Bucle de visualización**: Se recorre cada parte de la imagen y se muestra intermitentemente con un retraso de 0.2 segundos.

### Notas

- Este código es una simulación básica. Para trabajar con imágenes PNG reales, se recomienda usar bibliotecas externas compatibles con Pascal.
- Asegúrate de tener configurado el entorno gráfico correctamente antes de ejecutar el programa.

¡Espero que este ejemplo te sea útil!
