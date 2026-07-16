# Ejercicio Aplicado — Sistema de Control de Acceso a un Laboratorio

## Planteamiento del problema

Un laboratorio universitario cuenta con un sistema de acceso automatizado que debe permitir el ingreso (`F = 1`) únicamente bajo ciertas condiciones de seguridad. Se definen las siguientes proposiciones:

- `A`: el usuario tiene tarjeta de acceso válida.
- `B`: el usuario ha registrado su huella digital correctamente.
- `C`: es horario laboral autorizado (7:00 a.m. a 9:00 p.m.).

La política de acceso establece: *"Se permite el ingreso si el usuario presenta tarjeta válida y huella correcta, o si es horario laboral y presenta al menos la tarjeta válida."*

## Expresión booleana

`F = A·B + C·A`

## Tabla de verdad

| A | B | C | F |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

## Simplificación algebraica

1. `F = A·B + C·A`
2. Factorizando `A`: `F = A·(B + C)`

**Expresión simplificada:** `F = A·(B + C)`

## Implementación con compuertas

- Una compuerta **OR** de 2 entradas recibe `B` y `C`, produciendo `B + C`.
- Una compuerta **AND** de 2 entradas recibe `A` y la salida de la compuerta OR anterior, produciendo `F`.
  
## Análisis de resultados

La simplificación demuestra que, sin importar cómo se redactó originalmente la política de acceso, el sistema físico solo necesita **una compuerta OR y una compuerta AND**, en lugar de las dos compuertas AND y una OR que sugeriría la expresión original sin simplificar. Esto reduce el costo del circuito y el tiempo de respuesta del sistema de acceso, sin alterar en absoluto su comportamiento lógico (ambas expresiones producen exactamente la misma tabla de verdad).

## Conclusión

Este caso demuestra que el álgebra de Boole no es un ejercicio abstracto: permite tomar una política de seguridad redactada en lenguaje natural, formalizarla, verificarla mediante una tabla de verdad y optimizar directamente el hardware que la implementa.

**<strong><a href="Unidad_2.md">🏠 INICIO</a></strong>**
