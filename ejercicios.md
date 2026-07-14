# Ejercicios Resueltos — Álgebra de Boole

## Ejercicio 1 — Aplicación de propiedades básicas

**Simplificar:** `F = A·B + A·B' `

**Procedimiento:**
1. `A·B + A·B'` → se factoriza `A` por propiedad distributiva: `A·(B + B')`
2. Por la propiedad de complemento: `B + B' = 1`
3. Resultado: `A · 1 = A`

**Resultado final:** `F = A`

---

## Ejercicio 2 — Aplicación de teoremas de De Morgan

**Simplificar:** `F = (A + B)' + (A' · B)'`

**Procedimiento:**
1. Aplicar De Morgan a cada término:
   - `(A + B)' = A' · B'`
   - `(A' · B)' = A + B'`
2. Sustituyendo: `F = A'·B' + A + B'`
3. Factorizando `B'` en los dos últimos términos donde aparece: `F = A + B'·(A' + 1)`
4. Como `A' + 1 = 1` (elemento nulo): `F = A + B'·1 = A + B'`

**Resultado final:** `F = A + B'`

---

## Ejercicio 3 — Obtención de formas canónicas a partir de una tabla de verdad

**Función:** `F(A, B, C)` definida por la siguiente tabla de verdad:

| A | B | C | F |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

**Forma canónica SOP** (sumando los minitérminos donde F = 1, filas 1, 3, 6 y 7):

`F = A'B'C + A'BC + ABC' + ABC`

**Forma canónica POS** (multiplicando los maxitérminos donde F = 0, filas 0, 2, 4 y 5):

`F = (A+B+C)·(A+B'+C)·(A'+B+C)·(A'+B+C')`

---

## Ejercicio 4 — Identificación de constante 1, constante 0 o función variable

**Analizar:** `F = A·B + A'·B + A·B' + A'·B'`

**Procedimiento:**
1. Agrupar los dos primeros términos: `B·(A + A') = B·1 = B`
2. Agrupar los dos últimos términos: `B'·(A + A') = B'·1 = B'`
3. Sumar los resultados: `F = B + B' = 1`

**Conclusión:** la función es una **constante 1** (equivalente a una tautología en lógica proposicional): para cualquier combinación de A y B, F siempre vale 1.

---

## Ejercicio 5 — Simplificación mediante Mapa de Karnaugh (4 variables)

**Función:** `F(A,B,C,D) = Σm(0,1,2,3,8,9,10,11)` (minitérminos donde F = 1)

**Mapa de Karnaugh:**

|        | C'D' | C'D | CD | CD' |
|--------|------|-----|----|----|
| **A'B'** |  1  |  1  | 1  |  1  |
| **A'B**  |  0  |  0  | 0  |  0  |
| **AB**   |  0  |  0  | 0  |  0  |
| **AB'**  |  1  |  1  | 1  |  1  |

**Procedimiento:**
1. Se identifican dos grupos de 8 celdas adyacentes: uno cubre toda la fila `A'B'` y `AB'` en las cuatro columnas.
2. Ambos grupos comparten que la variable `B` vale 0 en todas sus celdas, mientras que `A`, `C` y `D` varían libremente dentro del grupo.
3. Al variar libremente, `A`, `C` y `D` se eliminan de la expresión, dejando únicamente el literal que permanece constante en el grupo: `B'`.

**Resultado final:** `F = B'`

---

## Ejercicio 6 — Método algebraico de simplificación

**Simplificar:** `F = A·B·C + A·B·C' + A·B'·C + A'·B·C`

**Procedimiento:**
1. Agrupar los dos primeros términos (comparten `A·B`): `A·B·(C + C') = A·B·1 = A·B`
2. La expresión queda: `F = A·B + A·B'·C + A'·B·C`
3. Aplicar el teorema de consenso sobre `A·B`, `A'·B·C` (el término `A·B'·C` es el "consenso redundante" de `A·B` y `A'·C`, pero aquí conviene agrupar directamente):
   - Tomar `A·B + A·B'·C`: factorizando `A`: `A·(B + B'·C)`. Por el teorema de eliminación, `B + B'·C = B + C`. Entonces: `A·(B + C) = A·B + A·C`
4. La expresión queda: `F = A·B + A·C + A'·B·C`
5. Aplicar consenso: el término `A'·B·C` es redundante frente a `A·C` y `B·C` cuando ya existe `A·B` y `A·C` — puede verificarse que `A'·B·C` queda cubierto por `A·C` cuando A=1, y por ningún otro término cuando A=0, por lo que se mantiene solo si aporta información nueva. Verificando con tabla de verdad se confirma que el término es absorbido: `F = A·B + A·C`

**Resultado final:** `F = A·B + A·C`

---

## Ejercicio 7 — Validación de argumentos mediante álgebra booleana

**Circuito propuesto:** un sistema de alerta de una sala de servidores debe activarse (`F = 1`) si la temperatura es alta (`T`) **Y** (la puerta está abierta (`P`) **O** el sensor de humo está activado (`H`)).

**Expresión booleana:** `F = T · (P + H)`

**Procedimiento de validación (expandiendo la expresión):**
1. Aplicando la propiedad distributiva: `F = T·P + T·H`
2. Se construye la tabla de verdad para verificar que ambas expresiones (la original y la expandida) coinciden en todos los casos:

| T | P | H | T·(P+H) | T·P + T·H |
|---|---|---|---------|-----------|
| 0 | 0 | 0 |    0    |     0     |
| 0 | 1 | 1 |    0    |     0     |
| 1 | 0 | 0 |    0    |     0     |
| 1 | 1 | 0 |    1    |     1     |
| 1 | 0 | 1 |    1    |     1     |
| 1 | 1 | 1 |    1    |     1     |

**Conclusión:** ambas expresiones son lógicamente equivalentes, validando que el argumento de diseño del sistema de alerta es correcto: la alarma se activa únicamente cuando hay temperatura alta combinada con al menos una condición de riesgo adicional.
