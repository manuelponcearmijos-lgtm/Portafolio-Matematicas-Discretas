# Resumen Teórico — Álgebra de Boole

## 1. Propiedades del Álgebra de Boole

El álgebra de Boole es un sistema matemático que opera sobre dos únicos valores (0 y 1), y sobre el que se definen tres operaciones fundamentales: la suma lógica (OR, `+`), el producto lógico (AND, `·`) y el complemento (NOT, `'`). Sus propiedades fundamentales son:

- **Conmutativa**: `A + B = B + A` y `A · B = B · A`.
- **Asociativa**: `(A + B) + C = A + (B + C)` y `(A · B) · C = A · (B · C)`.
- **Distributiva**: `A · (B + C) = A·B + A·C` y `A + (B·C) = (A+B)·(A+C)`.
- **Identidad**: `A + 0 = A` y `A · 1 = A`.
- **Elemento nulo**: `A + 1 = 1` y `A · 0 = 0`.
- **Complemento**: `A + A' = 1` y `A · A' = 0`.
- **Idempotencia**: `A + A = A` y `A · A = A`.
- **Involución (doble complemento)**: `(A')' = A`.

Estas propiedades constituyen las reglas básicas que permiten manipular expresiones booleanas de forma equivalente sin necesidad de recurrir a una tabla de verdad completa.

## 2. Teoremas del Álgebra de Boole

A partir de las propiedades anteriores se derivan teoremas de mayor utilidad práctica para simplificar circuitos:

- **Teoremas de absorción**: `A + A·B = A` y `A · (A + B) = A`.
- **Teoremas de eliminación (redundancia)**: `A + A'·B = A + B` y `A · (A' + B) = A·B`.
- **Teoremas de consenso**: `A·B + A'·C + B·C = A·B + A'·C`.
- **Teoremas de De Morgan**:
  - `(A + B)' = A' · B'`
  - `(A · B)' = A' + B'`

Los teoremas de De Morgan son especialmente importantes porque permiten transformar sumas en productos (y viceversa) al negarlas, lo cual es indispensable al implementar circuitos que solo disponen de un tipo de compuerta (por ejemplo, únicamente NAND).

## 3. Simplificación de expresiones booleanas

Simplificar una expresión booleana consiste en encontrar una expresión equivalente (que produce exactamente los mismos resultados en su tabla de verdad) pero con menos términos, menos literales o menos operaciones. Simplificar es relevante porque una expresión más simple se traduce directamente en un circuito con menos compuertas lógicas, lo cual reduce el costo, el consumo de energía y la probabilidad de fallos del circuito físico.

Existen dos enfoques principales para simplificar:

- **Método algebraico**: aplicar sucesivamente las propiedades y teoremas del álgebra de Boole hasta no poder reducir más la expresión.
- **Mapas de Karnaugh**: un método gráfico que agrupa visualmente los términos de una tabla de verdad para encontrar la expresión mínima de forma sistemática.

## 4. Formas canónicas

Una forma canónica es una manera estandarizada de escribir una expresión booleana a partir de su tabla de verdad, sin haber aplicado todavía ninguna simplificación:

- **Suma de productos (SOP, *Sum of Products*)**: se construye sumando (OR) todos los minitérminos (productos de todas las variables, complementadas o no) correspondientes a las filas donde la función vale 1.
- **Producto de sumas (POS, *Product of Sums*)**: se construye multiplicando (AND) todos los maxitérminos (sumas de todas las variables, complementadas o no) correspondientes a las filas donde la función vale 0.

Ambas formas canónicas representan exactamente la misma función; la elección de una u otra suele depender de si conviene partir de los 1 o de los 0 de la tabla de verdad para facilitar la simplificación posterior.

## 5. Mapas de Karnaugh (K-Map)

El mapa de Karnaugh es una representación gráfica de la tabla de verdad organizada de tal forma que las celdas adyacentes (horizontal o verticalmente, nunca en diagonal) difieren en un solo bit. Esta propiedad —conocida como codificación Gray— permite identificar visualmente grupos de 1 (u 0) de tamaño 1, 2, 4, 8, etc., cada uno de los cuales corresponde a un término simplificado de la expresión final. Cuantas más celdas adyacentes se agrupen, menor será el número de literales necesarios en el término resultante.

## 6. Método algebraico de simplificación

El método algebraico consiste en partir de la forma canónica (o de cualquier expresión booleana) y aplicar repetidamente las propiedades y teoremas descritos anteriormente —principalmente absorción, eliminación y distributiva— hasta obtener una expresión que ya no pueda reducirse más. A diferencia del mapa de Karnaugh, este método no tiene un procedimiento gráfico fijo, por lo que requiere práctica para reconocer qué propiedad aplicar en cada paso, pero es el único método viable cuando el número de variables es muy alto (más de 4 o 5), donde el mapa de Karnaugh deja de ser práctico.

## 7. Implementación con compuertas

Una vez simplificada la expresión booleana, esta se traduce directamente en un circuito lógico compuesto por compuertas físicas o simuladas:

- Cada término AND (`·`) se implementa con una compuerta **AND**.
- Cada suma OR (`+`) se implementa con una compuerta **OR**.
- Cada complemento (`'`) se implementa con una compuerta **NOT** (inversor).

La cantidad de compuertas y de entradas necesarias depende directamente del nivel de simplificación alcanzado previamente: una expresión bien simplificada se traduce en un circuito con menos compuertas, menor retardo de propagación y menor costo de fabricación.
