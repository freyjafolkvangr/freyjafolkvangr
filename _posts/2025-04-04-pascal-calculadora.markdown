---
layout: post
title: "Calculadora en Pascal"
date: 2025-04-04
categories: programming pascal
---
 
# Calculadora Gráfica en Pascal

Este es un ejemplo de código en Pascal para una calculadora que utiliza gráficos. Asegúrate de tener configurado el entorno para trabajar con gráficos en Pascal.

```pascal
program CalculadoraGrafica;
uses Graph, Crt;

var
    gd, gm: Integer;
    num1, num2, resultado: Real;
    operacion: Char;

procedure DibujarInterfaz;
begin
    SetColor(White);
    OutTextXY(100, 50, 'Calculadora Grafica');
    OutTextXY(50, 100, 'Ingrese el primer numero:');
    OutTextXY(50, 150, 'Ingrese la operacion (+, -, *, /):');
    OutTextXY(50, 200, 'Ingrese el segundo numero:');
    OutTextXY(50, 300, 'Resultado:');
end;

procedure MostrarResultado(res: Real);
var
    resStr: String;
begin
    Str(res:0:2, resStr);
    OutTextXY(150, 300, resStr);
end;

begin
    gd := Detect;
    InitGraph(gd, gm, '');

    if GraphResult <> grOk then
    begin
        WriteLn('Error al inicializar el modo grafico.');
        Halt(1);
    end;

    DibujarInterfaz;

    { Simulación de entrada de datos }
    num1 := 10; { Ejemplo: primer número }
    operacion := '+'; { Ejemplo: operación }
    num2 := 5; { Ejemplo: segundo número }

    case operacion of
        '+': resultado := num1 + num2;
        '-': resultado := num1 - num2;
        '*': resultado := num1 * num2;
        '/': if num2 <> 0 then
                     resultado := num1 / num2
                 else
                 begin
                     OutTextXY(150, 300, 'Error: Division por cero');
                     ReadLn;
                     CloseGraph;
                     Halt(1);
                 end;
    else
        OutTextXY(150, 300, 'Operacion no valida');
        ReadLn;
        CloseGraph;
        Halt(1);
    end;

    MostrarResultado(resultado);

    ReadLn;
    CloseGraph;
end.
```

Este programa utiliza la unidad `Graph` para crear una interfaz gráfica básica. Puedes modificarlo para aceptar entradas dinámicas o mejorar la interfaz.
