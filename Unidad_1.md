# 🧩 Contenido del Portafolio – Matemáticas Discretas

---
 <h2>📘 1. Resumen Teórico</h2>

<p>✍️ <i>Elaborado por el estudiante</i></p>

<details>
<summary><b>🔹 Definición de proposición</b></summary>
<blockquote>
 Una proposición lógica es una afirmación o frase que expresa una idea con un valor de verdad definido: puede ser verdadera o falsa, pero nunca ambas al mismo tiempo. Son fundamentales en la lógica matemática porque permiten analizar argumentos, construir tablas de verdad y aplicar reglas de inferencia. En la vida cotidiana también aparecen constantemente, aunque muchas veces no se reconozcan como tales; por ejemplo, cuando alguien dice “Hoy llueve” está formulando una proposición, ya que esa frase puede evaluarse como verdadera o falsa según la realidad.

 **Definición**:Una proposición lógica se define como un enunciado o oración que tiene la propiedad de ser falsa (0) o verdadera (1), pero que no puede poseer ambos valores de verdad de manera simultánea. Se considera el elemento fundamental y básico de la lógica matemática 

Ejemplo: “El número 5 es impar” → Verdadero.
</blockquote>
</details>

<details>
<summary><b>🔹 Tipos de proposiciones</b></summary>
<blockquote>

 Las proposiciones lógicas se clasifican principalmente en dos grandes tipos: simples y compuestas. Las simples expresan una sola idea sin conectores, mientras que las compuestas se forman al unir proposiciones simples mediante operadores lógicos como la conjunción (∧), disyunción (∨), negación (¬), condicional (→) y bicondicional (↔), parece complicada verdad, pero lo bueno es que existen juegos donde se pueden identificar y poner en practica esas proposiciones, lo cual uno puede aprender mucho, solo que hay que buscar las maneras.
 
-Proposiciones Simples (Atómicas)
Definición: Enunciados que expresan una única idea y no contienen conectores lógicos.
Ejemplo:

“La Tierra gira alrededor del Sol” → Verdadero.

“2 + 2 = 5” → Falso.

Proposiciones Compuestas (Moleculares)
Definición: Se forman a partir de proposiciones simples unidas por conectores lógicos.

Ejemplos:

Conjunción (∧): “Hoy es lunes ∧ hace frío”.

Disyunción (∨): “Voy al cine ∨ me quedo en casa”.

Negación (¬): “¬(Está lloviendo)”.

Condicional (→): “Si estudias → apruebas”.

Bicondicional (↔): “Un número es par ↔ divisible entre 2”.
</blockquote>
</details>

<details>
<summary><b>🔹 Conectores lógicos (∧, ∨, ¬, →, ↔)</b></summary>
<blockquote>
 Los conectores lógicos son símbolos que permiten unir proposiciones simples para formar proposiciones compuestas y analizar su valor de verdad. Cada conector tiene una función específica en la lógica proposicional:

- Conjunción (∧): Une dos proposiciones y solo es verdadera si ambas lo son. Ejemplo: “Hoy es viernes ∧ hace sol”.

- Disyunción (∨): Es verdadera si al menos una de las proposiciones lo es. Ejemplo: “Estudio ∨ descanso”.

- Negación (¬): Invierte el valor de verdad de una proposición. Ejemplo: “¬(Está lloviendo)”.

- Condicional (→): Representa una relación de causa o implicación: si la primera proposición es verdadera, la segunda debe serlo. Ejemplo: “Si estudio → apruebo”.

- Bicondicional (↔): Es verdadera cuando ambas proposiciones tienen el mismo valor de verdad. Ejemplo: “Un número es par ↔ divisible entre 2”.
## 🔗 Conectores Lógicos

Los conectores permiten unir proposiciones simples para formar expresiones más complejas y analizar su valor de verdad.

| Conector | Símbolo | Definición | Ejemplo |
|----------|---------|------------|---------|
| **Conjunción** | ∧ | Es verdadera solo si ambas proposiciones lo son. | “Hoy es viernes ∧ hace sol” |
| **Disyunción** | ∨ | Es verdadera si al menos una proposición lo es. | “Estudio ∨ descanso” |
| **Negación** | ¬ | Invierte el valor de verdad de una proposición. | “¬(Está lloviendo)” |
| **Condicional** | → | Si la primera proposición es verdadera, la segunda debe serlo. | “Si estudio → apruebo” |
| **Bicondicional** | ↔ | Es verdadera cuando ambas proposiciones tienen el mismo valor de verdad. | “Un número es par ↔ divisible entre 2” |

---

📘 Estos conectores son la base para construir **tablas de verdad**, aplicar **reglas de inferencia** y diseñar **circuitos lógicos** en Matemáticas Discretas.

  
</blockquote>
</details>

<details>
<summary><b>🔹 Explicación de tablas de verdad</b></summary>
<blockquote> 
 Una tabla de verdad es una descripción organizada de todos los posibles valores de verdad que puede adoptar una proposición compuesta, considerando todas las combinaciones posibles de sus variables proposicionales. Según el resultado final, las proposiciones se clasifican en:

•	Tautología: Cuando la proposición es verdadera para todas las asignaciones posibles de valores.

•	Contradicción: Cuando la proposición es siempre falsa en todos los casos de su tabla de verdad.

•	Contingencia: Cuando la proposición puede ser tanto verdadera como falsa (una mezcla de ambos), dependiendo de los valores de las proposiciones que la integran.
 
**Nota**: Quiero a dar a conocer que la primera vez que vi este tema mi cabeza voló por los cielos ya que no entendía nada, y me esforzaba mucho para no quedarme atrás, pero después de esa clase observe un tutorial y la verdad se me hizo muy sencillo a tal punto que me sabia las reglas al derecho y al revés, el principal problema no fue el maestro si no fui yo, debido a que tenia que pedir ayuda pero no lo hice.

## 📊 Tablas de Verdad de Conectores Lógicos

### 1. Negación (¬p)
| p | ¬p |
|:-:|:-:|
| V | F |
| F | V |

---

### 2. Conjunción (p ∧ q)
| p | q | p ∧ q |
|:-:|:-:|:-----:|
| V | V | V |
| V | F | F |
| F | V | F |
| F | F | F |

---

### 3. Disyunción (p ∨ q)
| p | q | p ∨ q |
|:-:|:-:|:-----:|
| V | V | V |
| V | F | V |
| F | V | V |
| F | F | F |

---

### 4. Condicional (p → q)
| p | q | p → q |
|:-:|:-:|:-----:|
| V | V | V |
| V | F | F |
| F | V | V |
| F | F | V |

---

### 5. Bicondicional (p ↔ q)
| p | q | p ↔ q |
|:-:|:-:|:-----:|
| V | V | V |
| V | F | F |
| F | V | F |
| F | F | V |

 
</blockquote>
</details>

<details>
<summary><b>🔹 Principales leyes lógicas</b></summary>
<blockquote>
 También llamadas "Leyes de las proposiciones" o "Teoremas", se utilizan para simplificar expresiones complejas. Las más destacadas son:

 ## 📑 Principales Leyes Lógicas

| Ley | Expresión | Ejemplo |
|-----|-----------|---------|
| **Identidad** | p ∧ V = p ; p ∨ F = p | “Estudio ∧ verdadero = estudio” |
| **Dominio (Anulación)** | p ∨ V = V ; p ∧ F = F | “Estudio ∨ verdadero = verdadero” |
| **Idempotencia** | p ∨ p = p ; p ∧ p = p | “Estudio ∨ estudio = estudio” |
| **Doble Negación** | ¬(¬p) = p | “No es falso que estudio = estudio” |
| **Conmutativa** | p ∨ q = q ∨ p ; p ∧ q = q ∧ p | “Estudio ∨ descanso = descanso ∨ estudio” |
| **Asociativa** | (p ∨ q) ∨ r = p ∨ (q ∨ r) | “(Estudio ∨ descanso) ∨ juego = Estudio ∨ (descanso ∨ juego)” |
| **Distributiva** | p ∨ (q ∧ r) = (p ∨ q) ∧ (p ∨ r) | “Estudio ∨ (descanso ∧ juego)” |
| **De Morgan** | ¬(p ∧ q) = ¬p ∨ ¬q ; ¬(p ∨ q) = ¬p ∧ ¬q | “No (estudio ∧ descanso) = No estudio ∨ no descanso” |
| **Absorción** | p ∨ (p ∧ q) = p ; p ∧ (p ∨ q) = p | “Estudio ∨ (estudio ∧ descanso) = estudio” |
| **Complemento** | p ∨ ¬p = V ; p ∧ ¬p = F | “Estudio ∨ no estudio = verdadero” |


</blockquote>
</details>

<details>
<summary><b>🔹 Reglas de inferencia</b></summary>
<blockquote>
Las reglas de inferencia son principios que permiten obtener conclusiones válidas a partir de premisas dadas, garantizando que el razonamiento sea correcto y coherente. 

 ## 📑 Reglas de Inferencia

| Regla | Forma | Ejemplo |
|-------|-------|---------|
| **Modus Ponendo Ponens** | p → q ; p ; ∴ q | “Si estudio → apruebo; estudio; ∴ apruebo” |
| **Modus Tollendo Tollens** | p → q ; ¬q ; ∴ ¬p | “Si estudio → apruebo; no apruebo; ∴ no estudié” |
| **Silogismo Hipotético** | p → q ; q → r ; ∴ p → r | “Si estudio → apruebo; si apruebo → me gradúo; ∴ si estudio → me gradúo” |
| **Modus Tollendo Ponens** | p ∨ q ; ¬p ; ∴ q | “Estudio ∨ descanso; no estudio; ∴ descanso” |
| **Dilema Constructivo** | (p → q) ∧ (r → s) ; p ∨ r ; ∴ q ∨ s | “Si estudio → apruebo; si descanso → me relajo; estudio ∨ descanso; ∴ apruebo ∨ me relajo” |
| **Dilema Destructivo** | (p → q) ∧ (r → s) ; ¬q ∨ ¬s ; ∴ ¬p ∨ ¬r | “Si estudio → apruebo; si descanso → me relajo; no apruebo ∨ no me relajo; ∴ no estudio ∨ no descanso” |
| **Simplificación** | p ∧ q ; ∴ p | “Estudio ∧ descanso; ∴ estudio” |
| **Conjunción** | p ; q ; ∴ p ∧ q | “Estudio; descanso; ∴ estudio ∧ descanso” |
| **Adición** | p ; ∴ p ∨ q | “Estudio; ∴ estudio ∨ descanso” |
| **Conmutación** | p ∨ q ; ∴ q ∨ p | “Estudio ∨ descanso; ∴ descanso ∨ estudio” |
| **Ley de Absorción** | p → q ; ∴ p → (p ∧ q) | “Si estudio → apruebo; ∴ estudio → (estudio ∧ apruebo)” |

</blockquote>
</details>

 ## 📘 Ejercicios Resueltos (mínimo 5)

### 🔣 Ejercicio 1: Traducción de lenguaje natural a simbólico
 
 🏠 Ejercicio 1: Clima
  
  ![Ejercicio 1](https://github.com/user-attachments/assets/4f85d261-6cc5-4a30-b69d-42c9b536c7ce)
 
  📚 Ejercicio 2: Estudios
  
  ![Ejercicio 2](https://github.com/user-attachments/assets/e946c52b-9820-44ae-9848-c48a72a5b508 )

  🚗 Ejercicio 3: Transporte
  
  ![Ejercicio 3](https://github.com/user-attachments/assets/6b08e8cb-5c00-4536-b095-ee66c0126118)
  
  💻 Ejercicio 4: Tecnología
  
  ![Ejercicio 4](https://github.com/user-attachments/assets/7b3d08a0-e07c-4155-962b-2fbfe51c0928)

  🕒 Ejercicio 5: Rutina diaria
  
  ![Ejercicio 5](https://github.com/user-attachments/assets/9ac616e0-6973-4df6-8fd9-4ba11c9c75db )

**Procedimiento paso a paso:**
1. Identificar las proposiciones simples.  
2. Asignar letras a cada proposición.  
3. Determinar los conectores lógicos adecuados.  
4. Escribir la fórmula simbólica.  
5. Verificar la coherencia del enunciado.  

---
 
### 📊 Ejercicio 2: Tablas de verdad

🟩 Ejercicio 1:

![Ejercicio2a](https://github.com/user-attachments/assets/8ce4e2f2-f3dd-49f6-ac99-e32306125f49)

🟦 Ejercicio 2:

![Ejercicio2b](https://github.com/user-attachments/assets/c6739bb3-4b5f-4e21-b54e-e0702848c8cc)

🟥 Ejercicio 3:

![Ejercicio2c](https://github.com/user-attachments/assets/d7981ba9-280b-4b73-8e45-01325cdcb9c6)

🟧 Ejercicio 4:

![Ejercicio2d](https://github.com/user-attachments/assets/95862d4d-b3da-4a9c-987e-1b2779575f17)

🟨 Ejercicio 5:

![Ejercicio2e](https://github.com/user-attachments/assets/4f4c3ade-19a8-4941-9e43-ee05c38713dd)


**Procedimiento paso a paso:**
1. Definir las proposiciones.  
2. Construir la tabla con todas las combinaciones.  
3. Evaluar la fórmula en cada fila.  
4. Identificar patrones de verdad.  
5. Concluir si es tautología, contradicción o contingencia.  

---

### 🧮 Ejercicio 3: Tautologías y contradicciones
 

🟩 Ejercicio 1:

![Ejercicio3a](https://github.com/user-attachments/assets/ffab05a6-8560-4432-8aa2-2649844dcec9)
 
🟦 Ejercicio 2:

![Ejercicio3b](https://github.com/user-attachments/assets/01514f70-ca5c-4f95-b34a-b1b3bcd87812)

🟥 Ejercicio 3:

![Ejercicio2c](https://github.com/user-attachments/assets/1f5316e9-5231-4e38-9ee9-4f2c7fad61a3)

🟧 Ejercicio 4:

![Ejercicio2d](https://github.com/user-attachments/assets/3d0adb08-0b09-401b-9358-780520c6fc84)

🟨 Ejercicio 5:

![Ejercicio2e](https://github.com/user-attachments/assets/4a0662f7-f530-4e68-a632-3e6df103e712) 

**Procedimiento paso a paso:**
1. Seleccionar la fórmula.  
2. Construir su tabla de verdad.  
3. Revisar si siempre es verdadera o falsa.  
4. Clasificar como tautología o contradicción.  
5. Justificar la conclusión.  

---

### 🧷 Ejercicio 4: Leyes proposicionales

🟩 Ejercicio 1: 

![Ejercicio4a](https://github.com/user-attachments/assets/69c1a547-8c6f-499f-a173-d5ff4edf93b8) 

🟦 Ejercicio 2:

![Ejercicio4b](https://github.com/user-attachments/assets/c45bc3d7-e49d-4e23-893f-d0185529c6d1)
 
🟥 Ejercicio 3:

![Ejercicio4c](https://github.com/user-attachments/assets/1efabd59-149b-4de6-ac9b-b52de66e7e02)

🟧 Ejercicio 4:

![Ejercicio4d](https://github.com/user-attachments/assets/85457131-e8a7-4dc9-aa5b-f8c76fd1887b)
 
🟨 Ejercicio 5:

![Ejercicio4e](https://github.com/user-attachments/assets/6e2731d4-8206-4106-b8cd-b59988ebff4b)

**Procedimiento paso a paso:**
1. Identificar la fórmula original.  
2. Aplicar la ley lógica correspondiente.  
3. Simplificar paso a paso.  
4. Comparar con la fórmula inicial.  
5. Confirmar equivalencia.  

---

### ✅ Ejercicio 5: Validación de argumentos

🟩 Ejercicio 1: 

![Ejercicio5a](https://github.com/user-attachments/assets/6b22ace7-cd23-45bb-894b-ffb1d6a81dc4)

![Ejercicio5a](https://github.com/user-attachments/assets/47f16fbf-afa5-40fc-9744-6f214e9602eb)

🟦 Ejercicio 2:  

![Ejercicio5b](https://github.com/user-attachments/assets/e3bdb095-caaa-4afb-a552-cc4e05850d7f)

![Ejercicio5b](https://github.com/user-attachments/assets/7d4220ca-c3db-4ad6-8b54-a2082a394bb8)

 
🟥 Ejercicio 3:

![Ejercicio5c](https://github.com/user-attachments/assets/6b1ff9eb-528f-4a34-9f54-6137148d598c)

![Ejercicio5c](https://github.com/user-attachments/assets/008e8aac-8e20-4750-b401-962c74c6a2c4)

🟧 Ejercicio 4:
 
![Ejercicio5d](https://github.com/user-attachments/assets/e1d2e893-6c14-44f5-a738-2f4f9b18fcfe)

![Ejercicio5d](https://github.com/user-attachments/assets/26ac7f0e-c92c-48c1-b874-74cded75d61e)

🟨 Ejercicio 5:
 
![Ejercicio5e](https://github.com/user-attachments/assets/cc4bc9f7-bff0-4423-a3f4-7f5082f15de5)

![Ejercicio5e](https://github.com/user-attachments/assets/30eea1f0-f444-4c36-be32-b337423d0105)


**Procedimiento paso a paso:**
1. Escribir las premisas.  
2. Representarlas simbólicamente.  
3. Construir la tabla de verdad.  
4. Evaluar si la conclusión se cumple siempre que las premisas sean verdaderas.  
5. Determinar validez del a argumento.  


 ## 🧠 Ejercicio Aplicado (Caso Real)

<details open>
  <summary><b>✨ Resolución paso a paso</b></summary>

  <div style="background-color:#1e1e1e; padding:14px; border-radius:8px; color:#E0E0E0;">

  **1. 🌍 Plantear un problema cotidiano**  
  Cada mañana decides cómo llegar al campus universitario.  
  - Si el clima es favorable y tienes tiempo, prefieres ir en bicicleta 🚲.  
  - Si el clima no ayuda o estás apurado, tomas el bus 🚌.  
  Este problema refleja una decisión lógica basada en condiciones externas.

  **2. 💬 Definir proposiciones**  
  - \(p\): Está soleado  
  - \(q\): Tengo tiempo suficiente  
  - \(r\): Voy en bicicleta  
  - \(s\): Voy en bus  

 ## 🔣 Expresiones Simbólicas

| 📝 Enunciado | 🔢 Fórmula Lógica |
|--------------|------------------|
| Si está soleado y tengo tiempo, voy en bicicleta. | (p ∧ q) → r |
| Si no está soleado o no tengo tiempo, voy en bus. | (¬p ∨ ¬q) → s |
| No puedo ir en bicicleta y en bus al mismo tiempo. | ¬(r ∧ s) |

  **4. ⚙️ Analizar con lógica proposicional**  
  - Caso 1: \(p = V\), \(q = V\) → \(r = V\), \(s = F\).  
  - Caso 2: \(p = F\), \(q = V\) → \(s = V\), \(r = F\).  
  - Caso 3: \(p = V\), \(q = F\) → \(s = V\), \(r = F\).  
  - Caso 4: \(p = F\), \(q = F\) → \(s = V\), \(r = F\).  

  **5. 🧾 Concluir resultados**  
  El sistema lógico garantiza que **solo una opción de transporte** se cumple cada día:  
  - 🚲 Bicicleta si hay sol y tiempo.  
  - 🚌 Bus si falta cualquiera de esas condiciones.  
  - Nunca se cumplen ambas a la vez, lo que asegura consistencia en la decisión.

  **6. 📊 Tabla de verdad resumida**

  | p (sol) | q (tiempo) | r (bicicleta) | s (bus) |
  |---------|------------|---------------|---------|
  | V       | V          | V             | F       |
  | F       | V          | F             | V       |
  | V       | F          | F             | V       |
  | F       | F          | F             | V       |

  </div>
</details>

---

## 4. 🔍 Reflexión Personal
Responde:

- 🤔 **¿Qué fue lo más difícil de entender?**:
  
Desde mi perspectiva, lo más complicado ha sido enfrentar el miedo a preguntar cuando no entiendo algún tema, pues siento vergüenza de que otros puedan burlarse de mí por no comprender. Aunque la teoría me resulta sencilla y accesible, la práctica se vuelve más difícil porque aún no logro desarrollar la lógica necesaria para resolver los ejercicios. En particular, las tablas de verdad me generaron confusión al inicio, ya que desconocía cómo aplicar sus reglas, y las reglas de inferencia se convirtieron en un verdadero reto al ser un mundo completamente nuevo para mí. Además, las leyes lógicas me parecieron abrumadoras, pues al resolverlas existen múltiples posibilidades que pueden llevar fácilmente a errores y dificultar alcanzar el resultado esperado. Sin embargo, reconozco que estas dificultades forman parte del proceso de aprendizaje y me motivan a seguir practicando para fortalecer mi razonamiento lógico y superar mis temores.
  
- 💡 **¿Qué tema comprendí mejor?**:
  
Lo que comprendí con mayor facilidad fueron las tablas de verdad, ya que me permitieron visualizar de manera clara cómo se comportan las proposiciones según los diferentes conectores lógicos. Al organizar los valores de verdad en filas y columnas, pude identificar rápidamente cuándo una expresión resulta verdadera, falsa, una tautología, contradicción o contingencia. Este método me pareció muy práctico porque convierte la teoría en un esquema ordenado y fácil de seguir, lo que me ayudó a fortalecer mi razonamiento lógico y a tener más seguridad al resolver ejercicios; incluso cuando resolvimos la lección de dos ejercicios, lo que realice primero fue la tabla de verdad ya que me tarde un minuto, no se me complico debido a que ese tema es muy sencillo. 
  
- 🚀 **¿Cómo puedo aplicar la lógica en mi carrera?**:
  
En mi carrera de Ingeniería en Computación la lógica se convierte en una herramienta esencial, porque me permite estructurar algoritmos de manera ordenada, diseñar circuitos digitales a partir de tablas de verdad y aplicar reglas de inferencia para validar procesos. También la utilizo en programación, ya que los condicionales y bucles dependen directamente de razonamientos lógicos, y en bases de datos, donde los operadores lógicos ayudan a filtrar información con precisión. Además, la lógica es clave en áreas como inteligencia artificial y seguridad informática, pues garantiza que los sistemas funcionen de forma coherente y confiable. En conclusión, la lógica no es solo teoría, sino el puente que conecta mi razonamiento con la máquina y me ayuda a transformar ideas en soluciones prácticas.

---
 
## 📁 Anexos: Aprendizaje Práctico Experimental (APE)

A continuación se presentan los enlaces a las actividades prácticas desarrolladas.  
Todos los archivos se encuentran alojados en el repositorio de **Google Drive** de la asignatura:

| 🧩 **Actividad** | 📘 **Recurso** | 🔗 **Enlace Directo** |
|------------------|----------------|------------------------|
| 📂 Carpeta General | Todos los APE (1 al 5) | [📁 Acceder a Drive](https://drive.google.com/drive/folders/1QxW70n9aSkWdld3s3loON6Rw6OObadYJ?usp=drive_link) |


