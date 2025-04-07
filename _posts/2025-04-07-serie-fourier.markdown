## Serie de Fourier en MATLAB

En esta página, mostramos cómo graficar una serie de Fourier utilizando MATLAB. A continuación, se presenta el código y el resultado esperado.

### Código MATLAB

```matlab
% Parámetros
L = pi; % Longitud del intervalo
n_terms = 10; % Número de términos de la serie
x = linspace(-L, L, 1000); % Puntos en el eje x

% Función original (onda cuadrada)
f = @(x) square(x);

% Serie de Fourier
a0 = 0; % Coeficiente a0
fourier_series = a0 / 2; % Inicialización de la serie

for n = 1:n_terms
    an = 0; % Coeficientes an (en este caso, 0 para onda cuadrada)
    bn = (2 / (n * pi)) * (1 - cos(n * pi)); % Coeficientes bn
    fourier_series = fourier_series + an * cos(n * pi * x / L) + bn * sin(n * pi * x / L);
end

% Graficar
figure;
plot(x, f(x), 'r', 'LineWidth', 1.5); hold on;
plot(x, fourier_series, 'b--', 'LineWidth', 1.5);
legend('Función original', 'Serie de Fourier');
title('Aproximación de una serie de Fourier');
xlabel('x');
ylabel('f(x)');
grid on;
```

### Resultado Esperado

La gráfica muestra la función original (onda cuadrada) en color rojo y la aproximación de la serie de Fourier en color azul con líneas discontinuas. A medida que se incrementa el número de términos `n_terms`, la aproximación mejora.

### Notas

- Este ejemplo utiliza una onda cuadrada como función base.
- Puedes modificar la función `f` y los parámetros para adaptarlo a tus necesidades.
- Asegúrate de tener MATLAB instalado para ejecutar este código.

