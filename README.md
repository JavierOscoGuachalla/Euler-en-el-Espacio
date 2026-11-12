# Desafío «Euler en el espacio» — Lanzamiento de un cohete (1962)

Proyecto de la asignatura **Métodos Numéricos**.
**Estudiante:** Javier Osco Guachalla

Simulación educativa de los primeros 20 segundos de ascenso vertical de un cohete, inspirada en el contexto de la película *Talentos ocultos* (*Hidden Figures*) y los primeros programas espaciales de la NASA. El problema se resuelve con el método de Euler y se compara con la solución analítica exacta.

> **Aviso:** es un modelo didáctico simplificado. No pretende reproducir el modelo que la NASA usó en lanzamientos reales.

## Contenido

| Archivo | Descripción |
|---|---|
| `index.html` | Aplicación web interactiva (HTML, CSS y JavaScript en un solo archivo). |
| `Desafio_Euler_Cohete.docx` | Documento académico con el desarrollo matemático, tablas y gráficas. |
| `README.md` | Este archivo. |

## Modelo matemático

Con tres fuerzas (empuje, peso y resistencia del aire) y la segunda ley de Newton:

    m·dv/dt = T − m·g − k·v
    dy/dt = v

Con los valores iniciales queda el sistema:

    v' = 5.19 − 0.1·v
    y' = v
    v(0) = 0,  y(0) = 0

**Solución analítica exacta:**

    v(t) = 51.9·(1 − e^(−0.1t))
    y(t) = 51.9·t − 519·(1 − e^(−0.1t))

### Parámetros iniciales

| Parámetro | Valor |
|---|---:|
| Masa (m) | 1000 kg |
| Empuje (T) | 15000 N |
| Gravedad (g) | 9.81 m/s² |
| Coeficiente de resistencia (k) | 100 N·s/m |
| Velocidad inicial | 0 m/s |
| Altura inicial | 0 m |
| Tiempo de simulación | 20 s |
| Paso inicial (h) | 2 s |

## Métodos implementados

Todos integran el sistema completo (velocidad y altura):

- **Euler** (orden 1)
- **Heun** (orden 2) — ampliación
- **Runge-Kutta de 4.º orden, RK4** (orden 4) — ampliación
- **Solución analítica exacta** (referencia para calcular errores)

El error absoluto se calcula como |valor exacto − valor aproximado|.

## Resultados de referencia (t = 20 s)

Solución exacta: **v = 44.87609880 m/s**, **y = 589.23901200 m**

| Método (h = 2 s) | Velocidad (m/s) | Altura (m) | Error v (m/s) | Error y (m) |
|---|---:|---:|---:|---:|
| Euler | 46.32727993 | 574.72720067 | 1.451181 | 14.511811 |
| Heun | 44.76644717 | 590.33552826 | 0.109652 | 1.096516 |
| RK4 | 44.87587744 | 589.24122564 | 0.000221 | 0.002214 |

Valores de Euler a los 20 s según el paso:

| h (s) | Velocidad (m/s) | Altura (m) |
|---:|---:|---:|
| 2 | 46.32727993 | 574.72720067 |
| 1 | 45.59017163 | 582.09828373 |
| 0.5 | 45.23021907 | 585.69780926 |

Al dividir h entre 2, el error de Euler se reduce aproximadamente a la mitad, el de Heun a la cuarta parte y el de RK4 a la dieciseisava parte.

## Aplicación web

Para usarla, abre `index.html` con doble clic en cualquier navegador moderno. No requiere instalación ni conexión a internet.

Funciones:

- Parámetros editables (masa, empuje, gravedad, resistencia, velocidad y altura iniciales, tiempo y paso) con validación de entradas.
- Botones para ejecutar la simulación y restablecer los valores originales.
- Selección de los métodos que se quieren mostrar u ocultar.
- Tarjetas de resultados: velocidad y altura finales, errores absolutos, tiempo final e iteraciones.
- Tabla de iteraciones por instante (soluciones y errores).
- Gráficas de velocidad, altura y error absoluto contra el tiempo, con valores al pasar el cursor.
- Comparación de los métodos con h = 2, 1 y 0.5, con el orden de convergencia observado.
- Exportación de resultados a CSV.
- Diseño adaptable a escritorio y móvil.

## Limitaciones del modelo

- Masa, empuje, gravedad y resistencia se consideran constantes.
- Un cohete real consume combustible (la masa cambia), su empuje puede variar y su resistencia aerodinámica es más compleja.
- La resistencia es lineal (k·v) y el movimiento es solo vertical.

## Autor

Javier Osco Guachalla — Métodos Numéricos, gestión 2026.
