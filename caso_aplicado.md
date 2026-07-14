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
