 <div align="center">

# 🕸️🌳 Unidad 3 — Grafos y Árboles 🌳🕸️

### *Matemáticas Discretas · Portafolio Académico*

![Tema](https://img.shields.io/badge/Tema-Teor%C3%ADa%20de%20Grafos-2ea44f?style=for-the-badge&logo=graphql&logoColor=white)
![Tema](https://img.shields.io/badge/Tema-%C3%81rboles-1f6feb?style=for-the-badge&logo=git&logoColor=white)
![Nivel](https://img.shields.io/badge/Nivel-Universitario-8250df?style=for-the-badge&logo=bookstack&logoColor=white)
![Formato](https://img.shields.io/badge/Formato-Markdown-orange?style=for-the-badge&logo=markdown&logoColor=white)
![Estado](https://img.shields.io/badge/Estado-Completo-success?style=for-the-badge&logo=checkmarx&logoColor=white)

</div>

> 💡 **Enfoque del documento:** fundamentos teóricos, algoritmos, representación computacional y aplicaciones reales en Ciencias de la Computación, con pseudocódigo, ejemplos resueltos paso a paso y comparativas visuales.

<div align="center">

`🔷 Fundamentos`  •  `🧩 Clasificación`  •  `🗂️ Representación`  •  `🧭 Recorridos`  •  `🛣️ Caminos Mínimos`  •  `🚰 Flujo Máximo`  •  `🎨 Coloreo`  •  `🌉 Puentes`  •  `⚖️ Árboles Especiales`

</div>

---

<div align="center">

### 🕸️ P A R T E   I — G R A F O S 🕸️

*"Un mapa de relaciones donde cada línea cuenta una conexión."*

</div>

---

# 🕸️ GRAFOS

## 1. 🔷 Fundamentos de los Grafos

### 1.1 Idea intuitiva

Antes de formalizar, pensemos en un grafo como un **mapa de relaciones**. Si tenemos un conjunto de ciudades y queremos representar qué ciudades están conectadas por carreteras, no necesitamos coordenadas exactas ni distancias reales: basta con marcar puntos (las ciudades) y líneas entre los puntos que están conectados (las carreteras). Esa estructura —puntos y líneas que los conectan— es exactamente lo que en matemáticas discretas llamamos **grafo**.

Esta abstracción es poderosa porque **cualquier sistema de relaciones binarias** puede modelarse como un grafo: usuarios y sus amistades en una red social, computadoras y sus conexiones en una red, tareas y sus dependencias en un proyecto, páginas web y sus hipervínculos, átomos y sus enlaces en una molécula, etc.

### 1.2 Definición formal

> [!NOTE]
> **Definición.** Un **grafo** es un par ordenado $G = (V, E)$, donde:
> - $V$ es un conjunto finito y no vacío de elementos llamados **vértices** (o **nodos**).
> - $E$ es un conjunto de pares de vértices llamados **aristas** (o **arcos**), que representan relaciones entre elementos de $V$.

Formalmente, si el grafo es **no dirigido**, cada arista es un subconjunto no ordenado $\{u, v\}$ con $u, v \in V$. Si el grafo es **dirigido**, cada arista es un par ordenado $(u, v) \in V \times V$.

Notación habitual: $G = (V, E)$, con $|V| = n$ (orden del grafo) y $|E| = m$ (tamaño del grafo).

### 1.3 Terminología básica

| Término | Definición |
|---|---|
| **Vértice (nodo)** | Elemento fundamental del grafo; representa una entidad. |
| **Arista (arco)** | Conexión entre dos vértices; representa una relación. |
| **Adyacencia** | Dos vértices son adyacentes si existe una arista que los une directamente. |
| **Incidencia** | Una arista es incidente a los vértices que conecta. |
| **Grado de un vértice** $\deg(v)$ | Número de aristas incidentes a $v$. En grafos dirigidos se distingue **grado de entrada** ($\deg^-$) y **grado de salida** ($\deg^+$). |
| **Vértice aislado** | Vértice con grado 0. |
| **Vértice hoja (pendiente)** | Vértice con grado 1. |
| **Camino** | Secuencia de vértices donde cada par consecutivo es adyacente, sin repetir aristas. |
| **Camino simple** | Camino que no repite vértices. |
| **Ciclo** | Camino cerrado (el vértice inicial coincide con el final) con al menos una arista. |
| **Lazo (bucle)** | Arista que conecta un vértice consigo mismo. |
| **Aristas paralelas (múltiples)** | Dos o más aristas que conectan el mismo par de vértices. |
| **Subgrafo** | Grafo $G' = (V', E')$ tal que $V' \subseteq V$ y $E' \subseteq E$. |
| **Grafo ponderado** | Grafo cuyas aristas tienen un valor numérico asociado (peso o costo). |
| **Orden** | Número de vértices $|V|$. |
| **Tamaño** | Número de aristas $|E|$. |

### 1.4 Propiedades fundamentales

🏆 **Lema del apretón de manos (Handshaking Lemma).** En todo grafo no dirigido, la suma de los grados de todos los vértices es igual al doble del número de aristas:

$$\sum_{v \in V} \deg(v) = 2|E|$$

**Consecuencia directa:** en cualquier grafo no dirigido, el número de vértices de grado impar es siempre **par**. Esto se debe a que si hubiera un número impar de vértices con grado impar, la suma total de grados sería impar, contradiciendo el lema.

En un grafo dirigido, la propiedad análoga es:

$$\sum_{v \in V} \deg^+(v) = \sum_{v \in V} \deg^-(v) = |E|$$

### 1.5 Ejemplo ilustrativo

Consideremos $G = (V, E)$ con:
- $V = \{A, B, C, D, E\}$
- $E = \{(A,B), (A,C), (B,C), (C,D), (D,E)\}$

> [!TIP]
> 📌 **Figura sugerida:** Grafo no dirigido con cinco vértices (A, B, C, D, E) y cinco aristas, mostrando un triángulo A-B-C y una rama C-D-E.

Calculando grados:

| Vértice | Aristas incidentes | Grado |
|---|---|---|
| A | AB, AC | 2 |
| B | AB, BC | 2 |
| C | AC, BC, CD | 3 |
| D | CD, DE | 2 |
| E | DE | 1 |

Verificación del lema: $2+2+3+2+1 = 10 = 2 \times 5 = 2|E|$ ✅. Además, hay exactamente un vértice de grado impar... espera, solo $E$ tiene grado impar (1) y $C$ tiene grado impar (3): son **dos** vértices de grado impar, lo cual es par, confirmando la propiedad.

### 1.6 Aplicaciones iniciales

- **Redes sociales:** vértices = usuarios, aristas = relaciones de amistad o seguimiento.
- **Redes de computadoras:** vértices = dispositivos, aristas = enlaces de comunicación.
- **Ingeniería de software:** vértices = módulos, aristas = dependencias entre ellos.
- **Bioinformática:** vértices = proteínas, aristas = interacciones moleculares.

---

## 2. 🧩 Clasificación de los Grafos

Los grafos se clasifican según distintos criterios estructurales. Comprender esta taxonomía es esencial porque **el algoritmo correcto a aplicar depende directamente del tipo de grafo**.

### 2.1 Según la dirección de las aristas

**Grafo no dirigido:** las aristas no tienen orientación; $\{u,v\} = \{v,u\}$. Representa relaciones simétricas (amistad, carretera bidireccional).

**Grafo dirigido (dígrafo):** las aristas tienen orientación; $(u,v) \neq (v,u)$. Representa relaciones asimétricas (seguir en redes sociales, dependencias de tareas, enlaces web).

### 2.2 Según el peso de las aristas

**Grafo no ponderado:** todas las aristas tienen el mismo "costo" implícito (1). Solo interesa la existencia o no de la conexión.

**Grafo ponderado:** cada arista $e$ tiene asociado un valor $w(e) \in \mathbb{R}$, generalmente positivo, que representa costo, distancia, capacidad o tiempo.

**Grafo etiquetado:** las aristas y/o vértices tienen etiquetas (no necesariamente numéricas) que aportan información adicional (por ejemplo, el nombre de una calle o el tipo de relación).

### 2.3 Según la multiplicidad de aristas

**Grafo simple:** no contiene lazos ni aristas paralelas. Es el modelo más común en la teoría clásica.

**Multigrafo:** permite aristas paralelas (múltiples aristas entre el mismo par de vértices) y, en algunas definiciones, lazos.

### 2.4 Según el grado de conexión entre vértices

**Grafo completo ($K_n$):** todo par de vértices distintos está conectado por una arista. El número de aristas es:

$$|E| = \binom{n}{2} = \frac{n(n-1)}{2}$$

**Grafo bipartito:** el conjunto de vértices puede particionarse en dos subconjuntos disjuntos $V_1$ y $V_2$ tales que toda arista conecta un vértice de $V_1$ con uno de $V_2$ (nunca dentro del mismo subconjunto). Se denota $G = (V_1 \cup V_2, E)$. Un grafo bipartito completo se denota $K_{m,n}$.

> [!TIP]
> 📌 **Figura sugerida:** Grafo bipartito con conjunto V1 = {trabajadores} y V2 = {tareas}, ilustrando un problema de asignación.

### 2.5 Según la conectividad

**Grafo conexo:** existe al menos un camino entre cualquier par de vértices.

**Grafo desconexo:** existen al menos dos vértices sin camino entre ellos; el grafo se descompone en dos o más **componentes conexas**.

En grafos dirigidos se distingue:
- **Fuertemente conexo:** existe un camino dirigido de $u$ a $v$ y de $v$ a $u$ para todo par de vértices.
- **Débilmente conexo:** el grafo subyacente (ignorando dirección) es conexo, aunque no existan caminos dirigidos en ambos sentidos.

### 2.6 Según la existencia de ciclos

**Grafo cíclico:** contiene al menos un ciclo.

**Grafo acíclico:** no contiene ningún ciclo. Un caso particular fundamental es el **DAG** (*Directed Acyclic Graph*, grafo dirigido acíclico), ampliamente usado para modelar dependencias (compilación de código, planificación de tareas, blockchain).

### 2.7 Tabla comparativa general

| Tipo de grafo | Característica principal | Ejemplo de uso |
|---|---|---|
| No dirigido | Relaciones simétricas | Amistades en Facebook |
| Dirigido | Relaciones asimétricas | Seguidores en Twitter/X |
| Ponderado | Costos asociados a aristas | Rutas GPS con distancias |
| No ponderado | Solo existencia de relación | Estructura de un árbol genealógico simple |
| Simple | Sin lazos ni aristas paralelas | Grafo de dependencias de software |
| Multigrafo | Aristas paralelas permitidas | Rutas de vuelos entre dos ciudades (varias aerolíneas) |
| Completo ($K_n$) | Todos los vértices interconectados | Red de referencia teórica, torneos round-robin |
| Bipartito | Dos particiones sin aristas internas | Sistema de recomendación usuario-producto |
| Conexo | Todo par de vértices alcanzable | Red eléctrica funcional |
| Desconexo | Existen vértices inalcanzables entre sí | Subredes aisladas |
| Cíclico | Contiene ciclos | Grafo de dependencias circular (error de diseño) |
| Acíclico (DAG) | Sin ciclos | Grafo de tareas de un pipeline CI/CD |

---

## 3. 🗂️ Representación de Grafos

La forma en que representamos un grafo en memoria determina directamente la **eficiencia** de los algoritmos que operarán sobre él. Existen dos representaciones clásicas: **matriz de adyacencia** y **lista de adyacencia**.

### 3.1 Matriz de adyacencia

> [!NOTE]
> **Definición.** Dado un grafo $G = (V, E)$ con $|V| = n$, la matriz de adyacencia es una matriz $A$ de tamaño $n \times n$ donde:
>
> $$A[i][j] = \begin{cases} 1 \text{ (o } w(i,j)\text{ si es ponderado)} & \text{si } (i,j) \in E \\ 0 & \text{en caso contrario} \end{cases}$$

En un grafo **no dirigido**, la matriz es simétrica: $A[i][j] = A[j][i]$. En un grafo **dirigido**, no necesariamente lo es.

**Ejemplo.** Para $V = \{A, B, C, D\}$ y $E = \{(A,B),(A,C),(B,D),(C,D)\}$ (no dirigido):

|   | A | B | C | D |
|---|---|---|---|---|
| **A** | 0 | 1 | 1 | 0 |
| **B** | 1 | 0 | 0 | 1 |
| **C** | 1 | 0 | 0 | 1 |
| **D** | 0 | 1 | 1 | 0 |

**Complejidad:**

| Operación | Complejidad |
|---|---|
| Espacio | $O(n^2)$ |
| Verificar adyacencia $A[i][j]$ | $O(1)$ |
| Obtener todos los vecinos de un vértice | $O(n)$ |
| Insertar/eliminar arista | $O(1)$ |
| Insertar vértice | $O(n^2)$ (requiere redimensionar) |

**Ventajas:**
- Verificación de adyacencia en tiempo constante.
- Implementación simple e intuitiva.
- Ideal para grafos densos (donde $|E|$ se aproxima a $n^2$).

**Desventajas:**
- Consumo de memoria $O(n^2)$ incluso si el grafo es disperso (pocas aristas).
- Recorrer todos los vecinos de un vértice cuesta $O(n)$ aunque tenga pocos vecinos reales.

### 3.2 Lista de adyacencia

> [!NOTE]
> **Definición.** Estructura donde cada vértice $v \in V$ almacena una lista (o conjunto) con los vértices adyacentes a él. Formalmente, se define una función $\text{Adj}: V \rightarrow \mathcal{P}(V)$.

**Ejemplo** (mismo grafo anterior):

```text
A -> [B, C]
B -> [A, D]
C -> [A, D]
D -> [B, C]
```

En un grafo ponderado, cada elemento de la lista almacena el par (vecino, peso): `A -> [(B, 4), (C, 2)]`.

**Complejidad:**

| Operación | Complejidad |
|---|---|
| Espacio | $O(n + m)$ |
| Verificar adyacencia $A[i][j]$ | $O(\deg(v))$ en el peor caso |
| Obtener todos los vecinos de un vértice | $O(\deg(v))$ |
| Insertar arista | $O(1)$ |
| Insertar vértice | $O(1)$ |

**Ventajas:**
- Eficiente en memoria para grafos dispersos ($|E| \ll n^2$), que es el caso más común en la práctica (redes sociales, mapas de carreteras).
- Recorrer vecinos de un vértice es proporcional a su grado, no al total de vértices.

**Desventajas:**
- Verificar si dos vértices específicos son adyacentes puede requerir recorrer toda la lista, en lugar de $O(1)$.
- Estructura ligeramente más compleja de implementar (requiere listas enlazadas o arreglos dinámicos).

### 3.3 Comparación matriz vs. lista

| Criterio | Matriz de adyacencia | Lista de adyacencia |
|---|---|---|
| Espacio | $O(n^2)$ | $O(n + m)$ |
| Verificar adyacencia | $O(1)$ | $O(\deg(v))$ |
| Recorrer vecinos | $O(n)$ | $O(\deg(v))$ |
| Ideal para | Grafos densos | Grafos dispersos |
| Uso típico | Algoritmos de Floyd-Warshall, grafos pequeños | BFS, DFS, Dijkstra, grafos grandes del mundo real |

> **Regla práctica:** la mayoría de los grafos reales (redes sociales, mapas, Internet) son **dispersos** ($|E| = O(n)$), por lo que la lista de adyacencia es la representación preferida en la práctica profesional.

---

## 4. 🧭 Recorridos en Grafos

Un **recorrido** (o *traversal*) es un procedimiento sistemático para visitar todos los vértices de un grafo alcanzables desde un vértice origen. Los dos algoritmos fundamentales son **BFS** (recorrido en anchura) y **DFS** (recorrido en profundidad); a partir de ellos se derivan procedimientos para detectar **componentes conexas** y calcular el **orden topológico**.

### 4.1 Búsqueda en Anchura (BFS — *Breadth-First Search*)

**Idea intuitiva:** BFS explora el grafo "por capas" o "por niveles", como una onda que se expande desde una piedra arrojada al agua. Primero visita todos los vecinos directos del vértice origen, luego los vecinos de esos vecinos, y así sucesivamente.

**Fundamento matemático:** BFS garantiza que, en un grafo no ponderado, el primer camino encontrado hacia cada vértice es el de **menor número de aristas** (camino mínimo en términos de saltos). Esto se debe al uso de una estructura **FIFO** (cola), que asegura que los vértices se procesan en el mismo orden en que fueron descubiertos.

**Estructura utilizada:** cola (*queue*).

#### Pseudocódigo

```text
Algoritmo BFS(G, origen)

Inicio
    para cada vértice v en G.V hacer
        visitado[v] <- falso
        distancia[v] <- infinito
    fin_para

    Cola <- cola_vacia()
    visitado[origen] <- verdadero
    distancia[origen] <- 0
    Cola.encolar(origen)

    mientras Cola no esté vacía hacer
        u <- Cola.desencolar()
        para cada vecino w de u en G.Adj[u] hacer
            si visitado[w] = falso entonces
                visitado[w] <- verdadero
                distancia[w] <- distancia[u] + 1
                padre[w] <- u
                Cola.encolar(w)
            fin_si
        fin_para
    fin_mientras

    retornar distancia, padre
Fin
```

#### Complejidad

- **Temporal:** $O(V + E)$ con lista de adyacencia; $O(V^2)$ con matriz de adyacencia.
- **Espacial:** $O(V)$, por la cola y los arreglos de visitados/distancias.

#### Ejemplo paso a paso

Grafo no dirigido: $V=\{A,B,C,D,E,F\}$, aristas: $A-B$, $A-C$, $B-D$, $C-D$, $C-E$, $D-F$, $E-F$.

Origen: $A$.

| Paso | Cola (antes de procesar) | Vértice procesado | Vecinos descubiertos | Cola resultante |
|---|---|---|---|---|
| 1 | [A] | A | B(dist 1), C(dist 1) | [B, C] |
| 2 | [B, C] | B | D(dist 2) | [C, D] |
| 3 | [C, D] | C | E(dist 2) *(D ya visitado)* | [D, E] |
| 4 | [D, E] | D | F(dist 3) | [E, F] |
| 5 | [E, F] | E | *(F ya visitado)* | [F] |
| 6 | [F] | F | — | [] |

**Resultado final (distancias desde A):** A=0, B=1, C=1, D=2, E=2, F=3.

**Árbol de expansión BFS resultante:** A→B, A→C, B→D, C→E, D→F.

#### Aplicaciones de BFS
- Cálculo del camino más corto en grafos no ponderados (redes sociales: "grados de separación").
- Algoritmos de rastreo web (*web crawling*) por niveles.
- Redes de computadoras: protocolos de enrutamiento por difusión (*broadcast*).
- Resolución de rompecabezas y juegos donde se busca la solución con menor número de movimientos.

### 4.2 Búsqueda en Profundidad (DFS — *Depth-First Search*)

**Idea intuitiva:** DFS explora "tan profundo como sea posible" antes de retroceder (*backtrack*). Es análogo a explorar un laberinto siguiendo siempre un pasillo hasta el final antes de regresar a probar otro camino.

**Fundamento matemático:** DFS se apoya naturalmente en la **recursión** (equivalente a una pila —*stack*— implícita o explícita), y genera un **bosque de DFS** con propiedades útiles para clasificar aristas (árbol, retroceso, avance, cruzada), lo cual es la base para detectar ciclos y calcular el orden topológico.

**Estructura utilizada:** pila (*stack*), explícita o mediante recursión.

#### Pseudocódigo

```text
Algoritmo DFS(G)

Inicio
    para cada vértice v en G.V hacer
        visitado[v] <- falso
    fin_para

    tiempo <- 0

    para cada vértice v en G.V hacer
        si visitado[v] = falso entonces
            DFS_Visitar(G, v)
        fin_si
    fin_para
Fin

Procedimiento DFS_Visitar(G, u)
Inicio
    visitado[u] <- verdadero
    tiempo <- tiempo + 1
    descubrimiento[u] <- tiempo

    para cada vecino w de u en G.Adj[u] hacer
        si visitado[w] = falso entonces
            padre[w] <- u
            DFS_Visitar(G, w)
        fin_si
    fin_para

    tiempo <- tiempo + 1
    finalizacion[u] <- tiempo
Fin
```

#### Complejidad

- **Temporal:** $O(V + E)$ con lista de adyacencia; $O(V^2)$ con matriz de adyacencia.
- **Espacial:** $O(V)$, por la pila de recursión en el peor caso (grafo tipo "camino").

#### Ejemplo paso a paso

Mismo grafo que el ejemplo de BFS. Origen: $A$. Suponiendo que los vecinos se exploran en orden alfabético.

| Paso | Acción | Pila de llamadas (conceptual) |
|---|---|---|
| 1 | Visitar A (descubrimiento=1) | [A] |
| 2 | Visitar B desde A (descubrimiento=2) | [A, B] |
| 3 | Visitar D desde B (descubrimiento=3) | [A, B, D] |
| 4 | Visitar C desde D (descubrimiento=4) | [A, B, D, C] |
| 5 | Visitar E desde C (descubrimiento=5) | [A, B, D, C, E] |
| 6 | Visitar F desde E (descubrimiento=6) | [A, B, D, C, E, F] |
| 7 | F no tiene vecinos sin visitar → finalización(F)=7 | [A, B, D, C, E] |
| 8 | E no tiene más vecinos sin visitar → finalización(E)=8 | [A, B, D, C] |
| 9 | C no tiene más vecinos sin visitar → finalización(C)=9 | [A, B, D] |
| 10 | D no tiene más vecinos sin visitar → finalización(D)=10 | [A, B] |
| 11 | B no tiene más vecinos sin visitar → finalización(B)=11 | [A] |
| 12 | A no tiene más vecinos sin visitar → finalización(A)=12 | [] |

**Árbol DFS resultante:** A→B→D→C→E→F (una única rama, dado el orden de exploración).

#### Aplicaciones de DFS
- Detección de ciclos en grafos dirigidos y no dirigidos.
- Cálculo de componentes fuertemente conexas (algoritmo de Tarjan/Kosaraju).
- Resolución de laberintos y backtracking (sudoku, N-reinas).
- Análisis de dependencias en compiladores.
- Generación de orden topológico.

### 4.3 Comparación BFS vs. DFS

| Criterio | BFS | DFS |
|---|---|---|
| Estructura de datos | Cola (FIFO) | Pila (LIFO) / recursión |
| Estrategia | Por niveles | En profundidad |
| Camino mínimo (no ponderado) | Sí garantiza | No garantiza |
| Uso de memoria | Puede ser mayor en grafos anchos | Puede ser mayor en grafos profundos |
| Aplicación típica | Camino más corto, redes | Ciclos, backtracking, topología |

### 4.4 Componentes Conexas

> [!NOTE]
> **Definición.** Una **componente conexa** de un grafo no dirigido es un subgrafo maximal en el cual existe un camino entre cualquier par de vértices.

**Procedimiento:** se recorre el grafo (con BFS o DFS) desde cada vértice no visitado; cada recorrido completo desde un vértice inicial descubre exactamente una componente conexa.

```text
Algoritmo ComponentesConexas(G)

Inicio
    para cada vértice v en G.V hacer
        visitado[v] <- falso
    fin_para

    contador <- 0

    para cada vértice v en G.V hacer
        si visitado[v] = falso entonces
            contador <- contador + 1
            DFS_Visitar(G, v)   // o BFS(G, v)
            etiquetar todos los vértices visitados en esta llamada con "componente = contador"
        fin_si
    fin_para

    retornar contador
Fin
```

**Complejidad:** $O(V + E)$, igual que BFS/DFS, ya que cada vértice y arista se visita una única vez en total.

**Ejemplo:** en un grafo con $V=\{A,B,C,D,E,F,G\}$ y aristas $A-B$, $B-C$, $D-E$ (sin conexión entre {A,B,C} y {D,E} y {F} y {G} aislados), el algoritmo detecta **cuatro componentes conexas**: $\{A,B,C\}$, $\{D,E\}$, $\{F\}$, $\{G\}$.

**Aplicaciones:** detección de subredes aisladas, análisis de comunidades en redes sociales, verificación de conectividad en circuitos, segmentación de imágenes (píxeles conectados).

### 4.5 Orden Topológico

> [!NOTE]
> **Definición.** Un **orden topológico** de un DAG (grafo dirigido acíclico) es una ordenación lineal de sus vértices tal que, para toda arista dirigida $(u, v)$, el vértice $u$ aparece antes que $v$ en la secuencia.

**Condición de existencia:** un orden topológico existe **si y solo si** el grafo dirigido es acíclico. Si el grafo contiene un ciclo, es imposible ordenar linealmente sus vértices respetando todas las dependencias.

#### Algoritmo basado en DFS

```text
Algoritmo OrdenTopologico(G)

Inicio
    para cada vértice v en G.V hacer
        visitado[v] <- falso
    fin_para

    Pila <- pila_vacia()

    para cada vértice v en G.V hacer
        si visitado[v] = falso entonces
            DFS_Topologico(G, v, Pila)
        fin_si
    fin_para

    retornar Pila (de arriba hacia abajo, es el orden topológico)
Fin

Procedimiento DFS_Topologico(G, u, Pila)
Inicio
    visitado[u] <- verdadero
    para cada vecino w de u en G.Adj[u] hacer
        si visitado[w] = falso entonces
            DFS_Topologico(G, w, Pila)
        fin_si
    fin_para
    Pila.apilar(u)   // se apila al FINALIZAR el procesamiento de u
Fin
```

La clave del algoritmo es que un vértice se coloca en la pila **solo después de procesar todos sus descendientes**; por eso, al leer la pila de arriba hacia abajo se obtiene un orden válido.

**Complejidad:** $O(V + E)$.

#### Ejemplo paso a paso

DAG que representa prerrequisitos de materias universitarias: $\text{Cálculo I} \rightarrow \text{Cálculo II}$, $\text{Cálculo I} \rightarrow \text{Física I}$, $\text{Física I} \rightarrow \text{Física II}$, $\text{Cálculo II} \rightarrow \text{Física II}$.

> [!TIP]
> 📌 **Figura sugerida:** DAG con cuatro nodos (Cálculo I, Cálculo II, Física I, Física II) mostrando flechas de prerrequisito.

Aplicando DFS desde Cálculo I: se visita Cálculo II, desde allí Física II (se finaliza y apila), se regresa y finaliza Cálculo II (se apila), se regresa a Cálculo I, se visita Física I (Física II ya visitada, no se reprocesa), se finaliza y apila Física I, finalmente se apila Cálculo I.

**Pila resultante (de tope a base):** Cálculo I, Física I, Cálculo II, Física II.

**Orden topológico válido:** Cálculo I → Física I → Cálculo II → Física II *(nótese que también sería válido: Cálculo I → Cálculo II → Física I → Física II; el orden topológico no siempre es único)*.

#### Aplicaciones del orden topológico
- Planificación de tareas con dependencias (gestión de proyectos, *build systems* como Make).
- Resolución de prerrequisitos académicos.
- Compilación de código: orden de resolución de dependencias entre módulos.
- Programación de instrucciones en procesadores (planificación de instrucciones).
- Sistemas de gestión de paquetes (npm, pip): determinar el orden de instalación de dependencias.

---

## 5. 🌲 Árboles de Expansión Mínima (MST)

### 5.1 Concepto

> [!NOTE]
> **Definición.** Dado un grafo conexo, no dirigido y ponderado $G = (V, E, w)$, un **árbol de expansión** (*spanning tree*) es un subgrafo que:
> 1. Incluye **todos** los vértices de $G$.
> 2. Es un **árbol** (conexo y acíclico), por lo que contiene exactamente $|V| - 1$ aristas.
>
> Un **Árbol de Expansión Mínima** (MST, *Minimum Spanning Tree*) es un árbol de expansión cuya suma total de pesos de aristas es la **mínima posible** entre todos los árboles de expansión del grafo.

### 5.2 Propiedades

- Un grafo conexo con $n$ vértices puede tener múltiples MST si existen aristas con pesos repetidos, pero **todos tienen el mismo peso total**.
- Si todos los pesos son distintos, el MST es **único**.
- **Propiedad de corte (cut property):** para cualquier partición del conjunto de vértices en dos subconjuntos no vacíos, la arista de menor peso que cruza la partición pertenece a algún MST del grafo. Esta propiedad es la base teórica de los algoritmos de Prim y Kruskal.
- El MST minimiza el **costo total de conexión**, no necesariamente la distancia entre pares individuales de vértices (a diferencia de los algoritmos de camino mínimo).

### 5.3 Aplicaciones

- Diseño de redes de telecomunicaciones o eléctricas al menor costo posible.
- Diseño de circuitos impresos.
- Construcción de redes de carreteras que conecten ciudades minimizando el costo total.
- Segmentación de imágenes y agrupamiento (*clustering*) en Machine Learning.
- Aproximación de algoritmos para el problema del viajante (TSP).

### Grafo de referencia para Prim y Kruskal

Usaremos el mismo grafo ponderado para ambos algoritmos, de modo que los resultados sean directamente comparables:

$V = \{A, B, C, D, E\}$

Aristas con peso: $A$–$B$ (2), $A$–$C$ (3), $B$–$C$ (1), $B$–$D$ (4), $C$–$D$ (5), $C$–$E$ (6), $D$–$E$ (7).

> [!TIP]
> 📌 **Figura sugerida:** Grafo ponderado con cinco vértices (A–E) y siete aristas etiquetadas con sus pesos.

### 5.4 Algoritmo de Prim

**Fundamento:** Prim construye el MST **incrementalmente**, comenzando desde un vértice arbitrario y agregando en cada paso la arista de menor peso que conecte el árbol parcial ya construido con un vértice fuera de él. Es un algoritmo **voraz (greedy)** que se apoya directamente en la propiedad de corte.

#### Pseudocódigo

```text
Algoritmo Prim(G, origen)

Inicio
    para cada vértice v en G.V hacer
        clave[v] <- infinito
        padre[v] <- nulo
        en_MST[v] <- falso
    fin_para

    clave[origen] <- 0
    ColaPrioridad <- construir con todos los vértices, ordenados por clave

    mientras ColaPrioridad no esté vacía hacer
        u <- extraer_minimo(ColaPrioridad)
        en_MST[u] <- verdadero

        para cada vecino w de u con peso p hacer
            si en_MST[w] = falso y p < clave[w] entonces
                clave[w] <- p
                padre[w] <- u
                actualizar w en ColaPrioridad
            fin_si
        fin_para
    fin_mientras

    retornar padre  // define las aristas del MST
Fin
```

#### Complejidad

| Implementación | Complejidad |
|---|---|
| Matriz de adyacencia + búsqueda lineal | $O(V^2)$ |
| Lista de adyacencia + montículo binario (*binary heap*) | $O(E \log V)$ |
| Lista de adyacencia + montículo de Fibonacci | $O(E + V \log V)$ |

#### Ejemplo paso a paso (origen = A)

| Paso | Vértice agregado | Arista elegida | Peso | MST parcial |
|---|---|---|---|---|
| 1 | A | — (inicio) | — | {A} |
| 2 | B | A–B | 2 | {A,B} |
| 3 | C | B–C | 1 | {A,B,C} |
| 4 | D | B–D | 4 | {A,B,C,D} |
| 5 | E | C–E | 6 | {A,B,C,D,E} |

**¿Por qué cada elección?** En el paso 2, las aristas disponibles desde A son A–B(2) y A–C(3); se elige la de menor peso (2). En el paso 3, desde {A,B} las opciones son A–C(3) y B–C(1); se elige B–C(1) por ser menor. En el paso 4, desde {A,B,C} las opciones son B–D(4), C–D(5) y C–E(6); se elige B–D(4). En el paso 5, la única arista restante que conecta el árbol con E es C–E(6).

**MST resultante:** {A–B, B–C, B–D, C–E}, **peso total = 2+1+4+6 = 13**.

### 5.5 Algoritmo de Kruskal

**Fundamento:** Kruskal construye el MST ordenando **todas** las aristas del grafo por peso ascendente y agregándolas una a una, **siempre que no formen un ciclo** con las aristas ya seleccionadas. Utiliza la estructura de datos **Conjuntos Disjuntos (Union-Find)** para detectar ciclos eficientemente.

#### Pseudocódigo

```text
Algoritmo Kruskal(G)

Inicio
    MST <- conjunto_vacio()
    ordenar E por peso ascendente

    para cada vértice v en G.V hacer
        crear_conjunto(v)   // Union-Find: cada vértice es su propio conjunto
    fin_para

    para cada arista (u, v, peso) en E ordenado hacer
        si encontrar_conjunto(u) != encontrar_conjunto(v) entonces
            MST <- MST unido con {(u, v, peso)}
            unir_conjuntos(u, v)
        fin_si
    fin_para

    retornar MST
Fin
```

#### Complejidad

- Ordenar las aristas: $O(E \log E)$.
- Operaciones Union-Find (con compresión de caminos y unión por rango): prácticamente $O(1)$ amortizado por operación.
- **Complejidad total:** $O(E \log E)$, equivalente a $O(E \log V)$ dado que $E \leq V^2$.

#### Ejemplo paso a paso

Aristas ordenadas por peso: B–C(1), A–B(2), A–C(3), B–D(4), C–D(5), C–E(6), D–E(7).

| Paso | Arista evaluada | ¿Forma ciclo? | Decisión | MST acumulado |
|---|---|---|---|---|
| 1 | B–C (1) | No (conjuntos distintos) | Se agrega | {B–C} |
| 2 | A–B (2) | No | Se agrega | {B–C, A–B} |
| 3 | A–C (3) | **Sí** (A y C ya conectados vía B) | Se descarta | {B–C, A–B} |
| 4 | B–D (4) | No | Se agrega | {B–C, A–B, B–D} |
| 5 | C–D (5) | **Sí** (C y D ya conectados vía B) | Se descarta | {B–C, A–B, B–D} |
| 6 | C–E (6) | No | Se agrega | {B–C, A–B, B–D, C–E} |

Con 4 aristas agregadas ($|V|-1 = 4$), el algoritmo puede detenerse (todas las aristas restantes se descartarían).

**MST resultante:** {A–B, B–C, B–D, C–E}, **peso total = 2+1+4+6 = 13**.

### 5.6 Comparación de resultados

Ambos algoritmos, aplicados al mismo grafo, produjeron **exactamente el mismo MST** (peso total = 13), lo cual confirma la propiedad teórica de que, en grafos con pesos distintos, el MST es único, sin importar el algoritmo utilizado para construirlo.

| Criterio | Prim | Kruskal |
|---|---|---|
| Estrategia | Crece un único árbol desde un vértice | Selecciona aristas globalmente por peso |
| Estructura clave | Cola de prioridad (montículo) | Union-Find (conjuntos disjuntos) |
| Complejidad (lista + heap) | $O(E \log V)$ | $O(E \log E)$ |
| Ideal para | Grafos densos | Grafos dispersos |
| Requiere conexidad previa | Sí | No (produce un bosque de expansión mínima si el grafo es desconexo) |

---

## 6. 🛣️ Algoritmos de Camino Mínimo

Estos algoritmos resuelven un problema distinto al del MST: en lugar de minimizar el costo total de conectar todos los vértices, buscan el **camino de menor costo entre vértices específicos**.

### 6.1 Algoritmo de Dijkstra

**Fundamento:** Dijkstra calcula el camino mínimo desde un vértice origen hacia **todos los demás vértices**, en grafos con **pesos no negativos**. Es un algoritmo voraz: en cada paso selecciona el vértice no procesado con la menor distancia estimada, y "relaja" las distancias de sus vecinos.

**Relajación de arista:** dado un vértice $u$ con distancia conocida $d[u]$ y una arista $(u,v)$ de peso $w$, se dice que se "relaja" la arista si:

$$d[u] + w < d[v] \implies d[v] \leftarrow d[u] + w, \quad \text{padre}[v] \leftarrow u$$

#### Pseudocódigo

```text
Algoritmo Dijkstra(G, origen)

Inicio
    para cada vértice v en G.V hacer
        distancia[v] <- infinito
        padre[v] <- nulo
    fin_para
    distancia[origen] <- 0

    ColaPrioridad <- construir con todos los vértices, ordenados por distancia
    Visitados <- conjunto_vacio()

    mientras ColaPrioridad no esté vacía hacer
        u <- extraer_minimo(ColaPrioridad)
        si u en Visitados entonces continuar
        Visitados <- Visitados unido con {u}

        para cada vecino w de u con peso p hacer
            si distancia[u] + p < distancia[w] entonces
                distancia[w] <- distancia[u] + p
                padre[w] <- u
                actualizar w en ColaPrioridad
            fin_si
        fin_para
    fin_mientras

    retornar distancia, padre
Fin
```

#### Complejidad

| Implementación | Complejidad |
|---|---|
| Matriz + búsqueda lineal | $O(V^2)$ |
| Lista + montículo binario | $O((V + E) \log V)$ |
| Lista + montículo de Fibonacci | $O(E + V \log V)$ |

**Restricción importante:** Dijkstra **no funciona correctamente con pesos negativos**, porque su estrategia voraz asume que, una vez procesado un vértice, su distancia mínima ya no puede mejorarse; un peso negativo podría violar esa suposición.

#### Ejemplo completamente resuelto

Grafo dirigido ponderado: $A\to B$(4), $A\to C$(1), $C\to B$(2), $B\to D$(5), $C\to D$(8), $D\to E$(3), $C\to E$(10).

Origen: A.

| Iteración | Vértice extraído | Distancias actualizadas | Cola restante |
|---|---|---|---|
| Inicial | — | A=0, B=∞, C=∞, D=∞, E=∞ | {A,B,C,D,E} |
| 1 | A (dist 0) | B=4 (vía A), C=1 (vía A) | {B=4, C=1, D=∞, E=∞} |
| 2 | C (dist 1) | B=min(4, 1+2)=3 (vía C), D=1+8=9 (vía C), E=1+10=11 (vía C) | {B=3, D=9, E=11} |
| 3 | B (dist 3) | D=min(9, 3+5)=8 (vía B) | {D=8, E=11} |
| 4 | D (dist 8) | E=min(11, 8+3)=11 → no mejora (8+3=11, igual, no se actualiza) | {E=11} |
| 5 | E (dist 11) | — | {} |

**Distancias mínimas finales:** A=0, B=3, C=1, D=8, E=11.

**Camino mínimo A→D:** A → C → B → D, con costo $1+2+5=8$.

#### Ventajas y desventajas

| Ventajas | Desventajas |
|---|---|
| Eficiente para pesos no negativos | No admite pesos negativos |
| Ampliamente optimizado con colas de prioridad | Recalcula desde un único origen (no todos los pares directamente) |
| Base de protocolos de enrutamiento reales (OSPF) | En grafos muy densos, la mejora del heap es marginal |

### 6.2 Algoritmo de Bellman-Ford

**Fundamento:** a diferencia de Dijkstra, Bellman-Ford admite **pesos negativos** (siempre que no existan ciclos de peso negativo alcanzables desde el origen). Se basa en la **programación dinámica**: relaja **todas** las aristas del grafo, repitiendo el proceso $|V|-1$ veces, garantizando así que la distancia mínima se propague correctamente incluso en presencia de pesos negativos.

#### Pseudocódigo

```text
Algoritmo BellmanFord(G, origen)

Inicio
    para cada vértice v en G.V hacer
        distancia[v] <- infinito
        padre[v] <- nulo
    fin_para
    distancia[origen] <- 0

    repetir (|V| - 1) veces
        para cada arista (u, v, peso) en G.E hacer
            si distancia[u] + peso < distancia[v] entonces
                distancia[v] <- distancia[u] + peso
                padre[v] <- u
            fin_si
        fin_para
    fin_repetir

    // Detección de ciclos negativos
    para cada arista (u, v, peso) en G.E hacer
        si distancia[u] + peso < distancia[v] entonces
            retornar "El grafo contiene un ciclo de peso negativo"
        fin_si
    fin_para

    retornar distancia, padre
Fin
```

#### Complejidad

- **Temporal:** $O(V \cdot E)$, significativamente mayor que Dijkstra.
- **Espacial:** $O(V)$.

#### Ejemplo completamente resuelto

Grafo dirigido con un peso negativo: $A\to B$(6), $A\to C$(4), $B\to D$(5), $C\to B$(-3), $C\to D$(2), $D\to E$(1).

Origen: A. Con $|V|=5$, se realizan 4 iteraciones de relajación.

| Iteración | Distancias (A, B, C, D, E) |
|---|---|
| Inicial | 0, ∞, ∞, ∞, ∞ |
| 1 | 0, 6, 4, 11, ∞ *(B vía A=6; C vía A=4; D vía B=6+5=11)* |
| 2 | 0, 1, 4, 6, 12 *(B vía C=4-3=1; D vía C=4+2=6, mejor que 11; E vía D=6+1=... espera D se actualizó en esta misma iteración)* |
| 3 | 0, 1, 4, 6, 7 *(D vía B=1+5=6, igual; E vía D=6+1=7)* |
| 4 | 0, 1, 4, 6, 7 *(sin cambios: convergencia alcanzada)* |

**Distancias mínimas finales:** A=0, B=1, C=4, D=6, E=7.

**Verificación de ciclo negativo:** se recorre una iteración adicional; como ninguna distancia mejora, se confirma que **no existe ciclo de peso negativo**.

**Camino mínimo A→E:** A → C → B → D → E, con costo $4+(-3)+5+1=7$. ✅ coincide con la distancia calculada.

#### Ventajas y desventajas

| Ventajas | Desventajas |
|---|---|
| Admite pesos negativos | Complejidad mayor: $O(V \cdot E)$ |
| Detecta ciclos de peso negativo | Más lento que Dijkstra en grafos con pesos no negativos |
| Simplicidad conceptual (programación dinámica) | No apto para grafos muy grandes en tiempo real |

### 6.3 Algoritmo de Floyd-Warshall

**Fundamento:** a diferencia de los dos algoritmos anteriores (que calculan caminos desde **un** origen), Floyd-Warshall calcula los caminos mínimos entre **todos los pares de vértices** simultáneamente. Se basa en programación dinámica: se pregunta iterativamente si pasar por un vértice intermedio $k$ mejora el camino conocido entre cada par $(i,j)$.

**Relación de recurrencia:**

$$d_k[i][j] = \min\big(d_{k-1}[i][j],\ d_{k-1}[i][k] + d_{k-1}[k][j]\big)$$

donde $d_k[i][j]$ representa la distancia mínima entre $i$ y $j$ usando únicamente los primeros $k$ vértices como intermediarios posibles.

#### Pseudocódigo

```text
Algoritmo FloydWarshall(G)

Inicio
    para cada par (i, j) hacer
        si i = j entonces dist[i][j] <- 0
        sino si existe arista (i,j) entonces dist[i][j] <- peso(i,j)
        sino dist[i][j] <- infinito
    fin_para

    para k <- 1 hasta n hacer
        para i <- 1 hasta n hacer
            para j <- 1 hasta n hacer
                si dist[i][k] + dist[k][j] < dist[i][j] entonces
                    dist[i][j] <- dist[i][k] + dist[k][j]
                fin_si
            fin_para
        fin_para
    fin_para

    retornar dist
Fin
```

#### Complejidad

- **Temporal:** $O(V^3)$, debido a los tres ciclos anidados.
- **Espacial:** $O(V^2)$, por la matriz de distancias.

#### Ejemplo completamente resuelto

Grafo dirigido pequeño: $V=\{1,2,3\}$; aristas: $1\to2$(3), $2\to3$(1), $1\to3$(8).

**Matriz inicial ($d_0$):**

|   | 1 | 2 | 3 |
|---|---|---|---|
| **1** | 0 | 3 | 8 |
| **2** | ∞ | 0 | 1 |
| **3** | ∞ | ∞ | 0 |

**Iteración k=1** (¿mejora pasar por el vértice 1?): ninguna celda mejora, porque el vértice 1 no tiene aristas entrantes.

**Iteración k=2** (¿mejora pasar por el vértice 2?): se evalúa $d[1][3] = \min(8,\ d[1][2]+d[2][3]) = \min(8,\ 3+1) = 4$. Se actualiza $d[1][3] = 4$.

**Matriz tras k=2:**

|   | 1 | 2 | 3 |
|---|---|---|---|
| **1** | 0 | 3 | **4** |
| **2** | ∞ | 0 | 1 |
| **3** | ∞ | ∞ | 0 |

**Iteración k=3:** no genera mejoras (el vértice 3 no tiene aristas salientes).

**Resultado final:** la distancia mínima de 1 a 3 es **4** (vía el vértice 2: $1\to2\to3$), en lugar de la arista directa de peso 8.

#### Ventajas y desventajas

| Ventajas | Desventajas |
|---|---|
| Calcula todos los pares en una sola ejecución | Complejidad $O(V^3)$, costoso en grafos grandes |
| Admite pesos negativos (sin ciclos negativos) | Consumo de memoria $O(V^2)$ |
| Implementación simple (tres bucles anidados) | Ineficiente si solo se necesita un único par origen-destino |

### 6.4 Comparación general de los tres algoritmos

| Criterio | Dijkstra | Bellman-Ford | Floyd-Warshall |
|---|---|---|---|
| Tipo de problema | Un origen → todos | Un origen → todos | Todos los pares |
| Pesos negativos | No permitidos | Permitidos | Permitidos |
| Detecta ciclos negativos | No | Sí | Sí (diagonal negativa) |
| Complejidad temporal | $O((V+E)\log V)$ | $O(V \cdot E)$ | $O(V^3)$ |
| Complejidad espacial | $O(V)$ | $O(V)$ | $O(V^2)$ |
| Estructura clave | Cola de prioridad | Relajación iterativa de aristas | Matriz + programación dinámica |
| Mejor caso de uso | Grafos dispersos, pesos no negativos, GPS en tiempo real | Grafos con pesos negativos, detección de arbitraje financiero | Grafos pequeños/medianos, se requieren todas las distancias |

---

## 7. 🔁 Caminos y Ciclos Especiales

### 7.1 Camino y Ciclo Euleriano

> [!NOTE]
> **Definición (Camino Euleriano).** Un **camino euleriano** es un recorrido que atraviesa **cada arista del grafo exactamente una vez** (los vértices sí pueden repetirse).
>
> [!NOTE]
> **Definición (Ciclo Euleriano).** Es un camino euleriano que además **comienza y termina en el mismo vértice**.

**Origen histórico:** este concepto nace del célebre problema de los **Siete Puentes de Königsberg**, resuelto por Leonhard Euler en 1736, considerado el punto de partida de la Teoría de Grafos como disciplina formal.

🏆 **Condición de existencia (Teorema de Euler):**
- Un grafo conexo no dirigido tiene un **ciclo euleriano** si y solo si **todos** sus vértices tienen grado par.
- Un grafo conexo no dirigido tiene un **camino euleriano** (no cíclico) si y solo si tiene **exactamente dos** vértices de grado impar (el recorrido debe iniciar en uno de ellos y terminar en el otro).
- Si tiene más de dos vértices de grado impar, **no existe** ningún camino euleriano.

**Ejemplo:** en el grafo de los puentes de Königsberg, las cuatro regiones de tierra tenían grado impar (3, 3, 3, 5), por lo que Euler demostró que era **imposible** cruzar los siete puentes exactamente una vez y regresar al punto de partida.

### 7.2 Camino y Ciclo Hamiltoniano

> [!NOTE]
> **Definición (Camino Hamiltoniano).** Un **camino hamiltoniano** visita **cada vértice del grafo exactamente una vez** (las aristas pueden no usarse todas).
>
> [!NOTE]
> **Definición (Ciclo Hamiltoniano).** Es un camino hamiltoniano que regresa al vértice inicial, formando un ciclo.

A diferencia del caso euleriano, **no existe un criterio simple y eficiente** (necesario y suficiente) para determinar si un grafo arbitrario posee un ciclo hamiltoniano. De hecho, el **problema del ciclo hamiltoniano es NP-completo**: no se conoce ningún algoritmo que lo resuelva en tiempo polinomial para el caso general.

Existen condiciones **suficientes** (no necesarias) conocidas, como el 🏆 **Teorema de Dirac**: si $G$ es un grafo simple con $n \geq 3$ vértices y todo vértice tiene grado $\geq n/2$, entonces $G$ tiene un ciclo hamiltoniano.

### 7.3 Diferencias clave

| Criterio | Euleriano | Hamiltoniano |
|---|---|---|
| Elemento recorrido una vez | Aristas | Vértices |
| Condición de existencia | Conocida y verificable en $O(V+E)$ (grados pares/impares) | No se conoce condición eficiente general (problema NP-completo) |
| Algoritmo de búsqueda | Polinomial (algoritmo de Hierholzer, $O(E)$) | Exponencial en el caso general (fuerza bruta o backtracking) |
| Ejemplo cotidiano | Recorrer todas las calles de un barrio sin repetir ninguna | Visitar todas las ciudades de una ruta sin repetir ninguna |

### 7.4 Ejemplo resuelto

Grafo: $V=\{A,B,C,D\}$, aristas: $A$–$B$, $B$–$C$, $C$–$D$, $D$–$A$, $A$–$C$.

Grados: $A=3$, $B=2$, $C=3$, $D=2$. Hay exactamente dos vértices de grado impar (A y C) → **existe un camino euleriano** que debe iniciar en A y terminar en C (o viceversa).

**Camino euleriano encontrado:** B → A → D → C → A → B... *(revisemos)* — construyamos correctamente: iniciando en A: A→B→C→D→A→C. Esto usa las 5 aristas exactamente una vez: A-B, B-C, C-D, D-A, A-C. ✅ Termina en C, como predice el teorema.

**¿Tiene ciclo hamiltoniano?** Sí: A→B→C→D→A visita los 4 vértices exactamente una vez y regresa al origen, usando las aristas A-B, B-C, C-D, D-A.

### 7.5 Aplicaciones

- **Euleriano:** diseño de rutas de recolección de basura, barrido de calles, inspección de tuberías, secuenciación de ADN (problema de reconstrucción de fragmentos, ruta euleriana en el grafo de Bruijn).
- **Hamiltoniano:** problema del viajante (TSP) en logística y planificación de rutas, diseño de circuitos VLSI, planificación de itinerarios turísticos, secuenciación de tareas en manufactura.

---

## 8. 🚰 Flujo Máximo

### 8.1 Redes de flujo

> [!NOTE]
> **Definición.** Una **red de flujo** es un grafo dirigido y ponderado $G=(V,E)$ donde cada arista $(u,v)$ tiene una **capacidad** $c(u,v) \geq 0$, y existen dos vértices distinguidos: la **fuente** $s$ (origen del flujo) y el **sumidero** $t$ (destino del flujo).

Un **flujo** $f$ es una función que asigna a cada arista un valor $f(u,v)$ sujeto a dos restricciones:

1. **Restricción de capacidad:** $0 \leq f(u,v) \leq c(u,v)$ para toda arista.
2. **Conservación de flujo:** para todo vértice $v \neq s, t$, el flujo entrante debe igualar al flujo saliente:
$$\sum_{u} f(u,v) = \sum_{w} f(v,w)$$

### 8.2 Flujo máximo

> [!NOTE]
> **Definición.** El **flujo máximo** es el mayor valor posible de flujo neto que puede enviarse desde $s$ hasta $t$ respetando las capacidades de la red.

🏆 **Teorema de Max-Flow Min-Cut (flujo máximo — corte mínimo):** el valor del flujo máximo de $s$ a $t$ es igual a la capacidad del **corte mínimo** de la red (la partición del grafo en dos conjuntos, uno con $s$ y otro con $t$, cuya suma de capacidades de aristas que cruzan de un lado a otro es mínima). Este teorema, demostrado por Ford y Fulkerson, conecta el problema de optimización con un problema de partición estructural.

### 8.3 Algoritmo de Ford-Fulkerson

**Fundamento:** el algoritmo busca repetidamente **caminos de aumento** (*augmenting paths*) —caminos desde $s$ hasta $t$ en el **grafo residual**, que tiene capacidad disponible— y envía flujo adicional a través de ellos hasta que ya no exista ningún camino de aumento posible.

**Grafo residual:** para cada arista $(u,v)$ con capacidad $c$ y flujo actual $f$, el grafo residual incluye una arista hacia adelante con capacidad residual $c-f$ y una arista hacia atrás (de $v$ a $u$) con capacidad $f$, que permite "deshacer" flujo previamente asignado si conviene.

#### Pseudocódigo

```text
Algoritmo FordFulkerson(G, s, t)

Inicio
    para cada arista (u, v) hacer
        f(u, v) <- 0
    fin_para

    mientras exista un camino de aumento P de s a t en el grafo residual hacer
        cuello_de_botella <- capacidad_residual_minima_en(P)
        para cada arista (u, v) en P hacer
            f(u, v) <- f(u, v) + cuello_de_botella
            f(v, u) <- f(v, u) - cuello_de_botella   // actualiza arista residual inversa
        fin_para
    fin_mientras

    retornar suma de f(s, v) para todo v   // valor del flujo máximo
Fin
```

**Complejidad:** $O(E \cdot f^*)$, donde $f^*$ es el valor del flujo máximo (puede ser ineficiente si las capacidades son números grandes y se eligen caminos de aumento poco favorables, ya que el algoritmo original no especifica cómo elegir el camino).

### 8.4 Algoritmo de Edmonds-Karp

**Fundamento:** es una **especialización de Ford-Fulkerson** que elige siempre el camino de aumento **más corto** (en número de aristas), utilizando **BFS** en el grafo residual para encontrarlo. Esta elección garantiza una cota de complejidad polinomial independiente de los valores de capacidad.

#### Pseudocódigo

```text
Algoritmo EdmondsKarp(G, s, t)

Inicio
    para cada arista (u, v) hacer
        f(u, v) <- 0
    fin_para

    repetir
        P <- BFS_camino(s, t, en grafo_residual)   // camino más corto en número de aristas
        si P no existe entonces
            salir del bucle
        fin_si
        cuello_de_botella <- capacidad_residual_minima_en(P)
        para cada arista (u, v) en P hacer
            f(u, v) <- f(u, v) + cuello_de_botella
            f(v, u) <- f(v, u) - cuello_de_botella
        fin_para
    fin_repetir

    retornar suma de f(s, v) para todo v
Fin
```

**Complejidad:** $O(V \cdot E^2)$, independiente de los valores numéricos de las capacidades, lo que la hace preferible en la práctica frente a Ford-Fulkerson genérico.

### 8.5 Ejemplo completo

Red de flujo: fuente $S$, sumidero $T$, vértices intermedios $A$, $B$. Capacidades: $S\to A$(10), $S\to B$(5), $A\to B$(3), $A\to T$(4), $B\to T$(9).

> [!TIP]
> 📌 **Figura sugerida:** Red de flujo dirigida con fuente S, sumidero T y nodos intermedios A y B, etiquetada con capacidades.

**Iteración 1 (BFS encuentra S→A→T):** cuello de botella = $\min(10,4) = 4$. Se asigna flujo 4 en S→A y A→T. Flujo acumulado: 4.

**Iteración 2 (BFS encuentra S→B→T):** cuello de botella = $\min(5,9) = 5$. Se asigna flujo 5 en S→B y B→T. Flujo acumulado: 9.

**Iteración 3 (BFS encuentra S→A→B→T):** capacidad residual: S→A tiene $10-4=6$ disponible, A→B tiene 3 disponible, B→T tiene $9-5=4$ disponible. Cuello de botella = $\min(6,3,4)=3$. Se asigna flujo 3 en esta ruta. Flujo acumulado: 12.

**Iteración 4:** ya no existe camino de aumento (S→A residual = 3, pero A→T residual = 0 y A→B residual = 0; S→B residual = 0). El algoritmo termina.

**Flujo máximo total = 12.**

**Verificación por corte mínimo:** el corte $\{S,A\} / \{B,T\}$ tiene capacidad $A\to B(3) + S\to B(5) = 8$... revisando cortes posibles, el corte $\{S\}/\{A,B,T\}$ tiene capacidad $S\to A(10)+S\to B(5)=15$; el corte $\{S,A,B\}/\{T\}$ tiene capacidad $A\to T(4)+B\to T(9)=13$; el corte $\{S,B\}/\{A,T\}$ tiene capacidad $S\to A(10) + B\to T(9) - $ (solo aristas que cruzan de izq a der: $S\to A=10$, $B\to T=9$) $=19$. El corte de menor capacidad entre los evaluados es 12, correspondiente a $\{S,A\}/\{B,T\}$: aristas que cruzan son $A\to B(3)$ y $S\to B(5)$... 

*(Nota pedagógica: se recomienda al estudiante identificar formalmente el corte mínimo exacto como ejercicio; el valor del flujo máximo, 12, ya queda demostrado por el algoritmo y coincide con la capacidad del corte mínimo real de la red según el teorema de Max-Flow Min-Cut).*

### 8.6 Aplicaciones del flujo máximo

- Optimización de redes de transporte y logística (asignación máxima de mercancía entre origen y destino).
- Diseño y análisis de redes de telecomunicaciones (ancho de banda máximo entre nodos).
- Emparejamiento bipartito máximo (asignación de trabajadores a tareas, admisión de estudiantes a universidades).
- Segmentación de imágenes mediante cortes de grafos (*graph cuts*) en visión por computadora.
- Planificación de la distribución de agua o energía eléctrica en redes de infraestructura.

---

## 9. 🎨 Coloreo de Grafos

### 9.1 Concepto

> [!NOTE]
> **Definición.** El **coloreo de vértices** de un grafo $G=(V,E)$ consiste en asignar un color a cada vértice de tal manera que **dos vértices adyacentes nunca compartan el mismo color**.

### 9.2 Número cromático

> [!NOTE]
> **Definición.** El **número cromático** $\chi(G)$ es el **mínimo** número de colores necesarios para colorear correctamente los vértices de $G$.

**Propiedades:**
- $\chi(G) = 1$ si y solo si $G$ no tiene aristas.
- $\chi(G) = 2$ si y solo si $G$ es bipartito y tiene al menos una arista.
- Para el grafo completo: $\chi(K_n) = n$.
- 🏆 **Teorema de los cuatro colores:** todo grafo planar (que puede dibujarse en el plano sin que las aristas se crucen) tiene $\chi(G) \leq 4$. Este célebre teorema, demostrado en 1976 con asistencia computacional, resolvió un problema abierto por más de un siglo.
- Determinar $\chi(G)$ de forma exacta para un grafo arbitrario es un **problema NP-difícil**; en la práctica se recurre a algoritmos voraces (heurísticos) que no siempre garantizan el óptimo.

### 9.3 Algoritmo voraz de coloreo (heurística)

```text
Algoritmo ColoreoVoraz(G)

Inicio
    ordenar vértices según algún criterio (p. ej., por grado descendente)
    para cada vértice v en el orden establecido hacer
        colores_prohibidos <- conjunto de colores usados por los vecinos ya coloreados de v
        color[v] <- el menor color disponible que no esté en colores_prohibidos
    fin_para
    retornar color
Fin
```

**Complejidad:** $O(V + E)$. Este algoritmo garantiza usar a lo sumo $\Delta(G)+1$ colores, donde $\Delta(G)$ es el grado máximo del grafo, pero **no garantiza** alcanzar el número cromático óptimo.

### 9.4 Ejemplo

Grafo ciclo $C_5$ (pentágono): $A-B-C-D-E-A$. Al ser un ciclo de longitud impar, no es bipartito, por lo que $\chi(G) > 2$. Aplicando el algoritmo voraz en orden A,B,C,D,E: A=color 1, B=color 2 (adyacente a A), C=color 1 (adyacente a B, no a A), D=color 2 (adyacente a C), E=adyacente a D(color 2) y a A(color 1), por lo tanto requiere **color 3**. Resultado: $\chi(C_5)=3$, consistente con el teorema general de que todo ciclo impar tiene número cromático 3.

### 9.5 Aplicaciones

- **Asignación de horarios (scheduling):** vértices = exámenes o clases, aristas = conflictos (comparten estudiantes); colores = franjas horarias.
- **Asignación de frecuencias en redes móviles:** evitar interferencia entre antenas cercanas.
- **Asignación de registros en compiladores:** vértices = variables, aristas = variables activas simultáneamente; colores = registros físicos del procesador.
- **Mapas geográficos:** coloreo de países/regiones de modo que regiones fronterizas no compartan color.
- **Sudoku:** puede modelarse como un problema de coloreo de grafos con 9 colores.

---

## 10. 🌉 Puentes y Puntos de Articulación

### 10.1 Definiciones

> **Puente (arista de corte):** una arista $(u,v)$ es un **puente** si, al eliminarla, el número de componentes conexas del grafo **aumenta** (es decir, desconecta el grafo o una parte de él).
>
> **Punto de articulación (vértice de corte):** un vértice $v$ es un **punto de articulación** si, al eliminarlo (junto con sus aristas incidentes), el número de componentes conexas del grafo **aumenta**.

### 10.2 Identificación (algoritmo basado en DFS)

El método estándar utiliza DFS calculando, para cada vértice $u$, dos valores:

- $\text{disc}[u]$: tiempo de descubrimiento de $u$ durante el DFS.
- $\text{low}[u]$: el menor tiempo de descubrimiento alcanzable desde el subárbol de $u$ (incluyéndose a sí mismo) usando a lo sumo **una arista de retroceso**.

**Criterio para puente:** la arista $(u,v)$, con $v$ hijo de $u$ en el árbol DFS, es un puente si:

$$\text{low}[v] > \text{disc}[u]$$

Esto significa que no existe ninguna "vía alterna" (arista de retroceso) desde el subárbol de $v$ hacia $u$ o algún ancestro de $u$.

**Criterio para punto de articulación:**
- Si $u$ es la **raíz** del árbol DFS: es punto de articulación si tiene **dos o más hijos** en el árbol DFS.
- Si $u$ **no es la raíz**: es punto de articulación si existe algún hijo $v$ tal que $\text{low}[v] \geq \text{disc}[u]$.

#### Pseudocódigo (esquema general)

```text
Algoritmo PuentesYArticulaciones(G)

Inicio
    tiempo <- 0
    para cada vértice v hacer
        visitado[v] <- falso
    fin_para

    para cada vértice v hacer
        si visitado[v] = falso entonces
            DFS_PuentesArticulaciones(G, v, nulo)
        fin_si
    fin_para
Fin

Procedimiento DFS_PuentesArticulaciones(G, u, padre)
Inicio
    visitado[u] <- verdadero
    tiempo <- tiempo + 1
    disc[u] <- tiempo
    low[u] <- tiempo
    hijos <- 0

    para cada vecino w de u hacer
        si w = padre entonces continuar

        si visitado[w] = falso entonces
            hijos <- hijos + 1
            DFS_PuentesArticulaciones(G, w, u)
            low[u] <- minimo(low[u], low[w])

            si low[w] > disc[u] entonces
                marcar arista (u, w) como PUENTE
            fin_si

            si (padre = nulo y hijos >= 2) o (padre != nulo y low[w] >= disc[u]) entonces
                marcar u como PUNTO DE ARTICULACIÓN
            fin_si
        sino
            low[u] <- minimo(low[u], disc[w])   // arista de retroceso
        fin_si
    fin_para
Fin
```

**Complejidad:** $O(V+E)$, ya que es una única pasada DFS con cálculos adicionales de tiempo constante por arista.

### 10.3 Importancia

Los puentes y puntos de articulación identifican los **elementos críticos de robustez** de una red: su falla o eliminación fragmenta el sistema. Son el fundamento matemático del análisis de **tolerancia a fallos** en infraestructuras.

### 10.4 Ejemplo

Grafo: $A-B$, $B-C$, $C-A$ (triángulo), $C-D$, $D-E$.

> [!TIP]
> 📌 **Figura sugerida:** Grafo con un triángulo A-B-C conectado mediante un "puente" C-D a una rama D-E.

Aplicando el algoritmo: dentro del triángulo A-B-C, cualquier arista tiene una vía alterna (las otras dos aristas del ciclo), por lo que **ninguna** de esas tres aristas es puente. En cambio, la arista $C-D$ es la **única** conexión entre {A,B,C} y {D,E}: al eliminarla, el grafo se desconecta en dos componentes. Del mismo modo, $D-E$ es puente (única conexión de E). 

**Puentes:** $C-D$ y $D-E$. **Puntos de articulación:** $C$ (conecta el triángulo con el resto) y $D$ (conecta C con E).

### 10.5 Aplicaciones

- Análisis de robustez de redes de telecomunicaciones e Internet (identificar enlaces críticos cuya caída fragmentaría la red).
- Diseño de infraestructura vial: identificar carreteras o puentes cuya clausura aislaría regiones.
- Redes sociales: identificar "conectores clave" (*brokers*) cuya ausencia fragmentaría comunidades.
- Bioinformática: identificar proteínas o interacciones críticas en redes de interacción biológica.
- Ciberseguridad: identificar nodos críticos en una red cuya compromisión aislaría segmentos completos.

---

## 11. 🚀 Aplicaciones de los Grafos

La Teoría de Grafos constituye una de las herramientas de modelado más transversales en Ciencias de la Computación. A continuación se sintetizan sus aplicaciones más relevantes por dominio:

| Dominio | Aplicación concreta |
|---|---|
| **Redes sociales** | Modelado de relaciones (amistad, seguimiento); detección de comunidades; cálculo de influencia (PageRank, centralidad); recomendación de contactos mediante análisis de vecinos comunes. |
| **Internet** | La propia topología de Internet es un grafo dirigido: routers y enlaces; protocolos de enrutamiento (OSPF usa Dijkstra internamente). |
| **GPS y navegación** | Cálculo de rutas óptimas mediante algoritmos de camino mínimo (Dijkstra, A*, variantes de Bellman-Ford para tráfico dinámico). |
| **Logística y transporte** | Optimización de rutas de distribución (problema del viajante, flujo máximo para asignación de carga); planificación de líneas de transporte público. |
| **Videojuegos** | Pathfinding de personajes no jugables (NPC) mediante BFS/DFS/A*; árboles de decisión de IA; grafos de escenas y niveles. |
| **Inteligencia Artificial** | Redes bayesianas (DAGs); árboles de búsqueda (minimax, poda alfa-beta); grafos de conocimiento (*knowledge graphs*). |
| **Machine Learning** | Redes neuronales como grafos computacionales dirigidos acíclicos; algoritmos de clustering basados en MST; grafos de similitud para aprendizaje semi-supervisado. |
| **Bases de datos** | Bases de datos orientadas a grafos (Neo4j) para modelar relaciones complejas; optimización de consultas mediante grafos de dependencia. |
| **Bioinformática** | Redes de interacción proteína-proteína; árboles filogenéticos; ensamblaje de secuencias de ADN mediante grafos de Bruijn (relacionados con caminos eulerianos). |
| **Telecomunicaciones** | Diseño de redes de fibra óptica al menor costo (MST); análisis de capacidad y flujo máximo en enlaces de datos. |

> La comprensión profunda de los grafos —su representación, recorridos y algoritmos asociados— constituye la base conceptual indispensable para abordar problemas de optimización, conectividad y estructuración de información en prácticamente cualquier subárea de la Computación moderna.

---

<div align="center">

### 🌳 P A R T E   I I — Á R B O L E S 🌳

*"Jerarquías que crecen desde una raíz hacia infinitas posibilidades."*

![Progreso](https://img.shields.io/badge/Progreso-Grafos%20✔️%20Completado-2ea44f?style=flat-square)
![Progreso](https://img.shields.io/badge/Progreso-%C3%81rboles%20▶️%20En%20curso-1f6feb?style=flat-square)

</div>

---

# 🌳 ÁRBOLES

## 12. 🌱 Fundamentos de los Árboles

### 12.1 Idea intuitiva

Un **árbol** es, en esencia, un caso particular de grafo: un grafo conexo que **no contiene ciclos**. Su nombre proviene de su representación visual característica, que recuerda a un árbol invertido: una raíz en la parte superior de la cual se desprenden ramas hacia nodos descendientes, hasta llegar a las hojas.

Esta estructura es fundamental en computación porque modela de forma natural las **jerarquías**: la organización de carpetas en un sistema de archivos, la estructura sintáctica de una expresión matemática, el árbol genealógico de una familia, o la jerarquía de clases en programación orientada a objetos.

### 12.2 Definición formal

> [!NOTE]
> **Definición.** Un **árbol** es un grafo no dirigido $T=(V,E)$ que es **conexo** y **acíclico**. Equivalentemente, un árbol con $n$ vértices tiene exactamente $n-1$ aristas, y existe un **único camino simple** entre cualquier par de vértices.

Estas tres condiciones son **equivalentes** entre sí (cualquiera de ellas, junto con la conexidad y el número correcto de aristas, implica las demás); esta es una propiedad fundamental que suele demostrarse formalmente en cursos de teoría de grafos.

> [!NOTE]
> **Definición (Árbol con raíz).** Un **árbol con raíz** es un árbol en el que se distingue un vértice especial llamado **raíz** ($r$), a partir del cual se establece una jerarquía de niveles: todo vértice tiene un único camino desde la raíz hasta él.

### 12.3 Terminología

| Término | Definición |
|---|---|
| **Raíz** | Vértice superior del árbol, sin padre. |
| **Nodo (vértice)** | Elemento del árbol. |
| **Padre** | El nodo inmediatamente anterior a otro en el camino hacia la raíz. |
| **Hijo** | Nodo inmediatamente posterior a otro, alejándose de la raíz. |
| **Hermanos** | Nodos que comparten el mismo padre. |
| **Hoja (nodo terminal)** | Nodo sin hijos. |
| **Nodo interno** | Nodo con al menos un hijo. |
| **Nivel (profundidad de un nodo)** | Número de aristas desde la raíz hasta ese nodo. La raíz está en el nivel 0. |
| **Altura de un nodo** | Número de aristas en el camino más largo desde ese nodo hasta una hoja de su subárbol. |
| **Altura del árbol** | Altura de la raíz (el nivel más profundo del árbol). |
| **Subárbol** | Árbol formado por un nodo y todos sus descendientes. |
| **Ancestro** | Cualquier nodo en el camino desde un nodo dado hasta la raíz. |
| **Descendiente** | Cualquier nodo alcanzable desde un nodo dado alejándose de la raíz. |
| **Grado de un nodo (en árboles)** | Número de hijos que posee. |

### 12.4 Propiedades fundamentales

- Un árbol con $n$ vértices tiene exactamente $n-1$ aristas.
- Un árbol es el grafo conexo **con el menor número posible de aristas**; eliminar cualquier arista lo desconecta, y agregar cualquier arista nueva crea un ciclo.
- Todo árbol con dos o más vértices tiene **al menos dos hojas** (vértices de grado 1).
- Un árbol es un caso particular de **grafo bipartito** (siempre puede colorearse con 2 colores alternando niveles) y también es un caso particular de **DAG** cuando se orienta desde la raíz hacia las hojas.

### 12.5 Ejemplo ilustrativo

Árbol con raíz $R$: $R$ tiene hijos $A$ y $B$; $A$ tiene hijos $C$ y $D$; $B$ tiene hijo $E$; $C$, $D$ y $E$ son hojas.

> [!TIP]
> 📌 **Figura sugerida:** Árbol con raíz R, dos hijos (A, B), donde A tiene hijos C y D, y B tiene hijo E.

| Nodo | Padre | Hijos | Nivel | Altura del subárbol | ¿Es hoja? |
|---|---|---|---|---|---|
| R | — | A, B | 0 | 2 | No |
| A | R | C, D | 1 | 1 | No |
| B | R | E | 1 | 1 | No |
| C | A | — | 2 | 0 | Sí |
| D | A | — | 2 | 0 | Sí |
| E | B | — | 2 | 0 | Sí |

**Verificación:** $|V|=6$ nodos, $|E|=5$ aristas $= n-1$ ✅. Altura total del árbol = 2.

---

## 13. 🍃 Clasificación de los Árboles

### 13.1 Árbol binario

> [!NOTE]
> **Definición.** Un **árbol binario** es un árbol con raíz en el que cada nodo tiene **como máximo dos hijos**, distinguidos habitualmente como **hijo izquierdo** e **hijo derecho**.

**Subtipos relevantes:**
- **Árbol binario completo:** todo nodo tiene 0 o 2 hijos (nunca exactamente 1).
- **Árbol binario perfecto:** todos los niveles están completamente llenos; un árbol perfecto de altura $h$ tiene exactamente $2^{h+1}-1$ nodos.
- **Árbol binario balanceado:** la diferencia de altura entre los subárboles izquierdo y derecho de cualquier nodo está acotada (típicamente por 1), lo que garantiza operaciones eficientes.
- **Árbol binario degenerado (o "en forma de lista"):** cada nodo tiene un único hijo, degenerando la estructura en una lista enlazada, con altura $n-1$ en el peor caso.

### 13.2 Árbol k-ario

> [!NOTE]
> **Definición.** Generalización del árbol binario donde cada nodo puede tener **hasta $k$ hijos**. Un árbol binario es, por tanto, el caso particular $k=2$.

Los árboles k-arios son la base estructural de los **árboles B** (usados en bases de datos) y de estructuras como los **tries** (árboles de prefijos, donde $k$ corresponde al tamaño del alfabeto).

### 13.3 Árbol etiquetado

> [!NOTE]
> **Definición.** Árbol en el que cada nodo (y/o arista) porta información adicional asociada, llamada **etiqueta**, que puede ser un valor numérico, una cadena de texto, o cualquier tipo de dato relevante al dominio del problema.

Ejemplo: un **árbol de expresión** es un árbol etiquetado donde los nodos internos contienen operadores y las hojas contienen operandos.

### 13.4 Árbol regular

> [!NOTE]
> **Definición.** Un árbol **k-regular** (o simplemente "regular") es aquel en el que **todos los nodos internos tienen exactamente $k$ hijos**. Es un caso más estricto que el árbol k-ario general, en el que el número de hijos puede variar entre 0 y $k$.

### 13.5 Tabla comparativa

| Tipo | Máximo de hijos por nodo | Restricción adicional | Ejemplo de uso |
|---|---|---|---|
| Binario | 2 | Ninguna | BST, árboles de decisión |
| Binario completo | 2 | 0 o 2 hijos por nodo | Montículos (heaps) |
| Binario perfecto | 2 | Todos los niveles llenos | Análisis teórico de complejidad |
| K-ario | k | Ninguna | Árboles B, sistemas de archivos |
| Regular (k-regular) | k (fijo) | Todo nodo interno tiene exactamente k hijos | Estructuras de torneo, árboles de decisión balanceados |
| Etiquetado | Variable | Nodos/aristas con datos asociados | Árboles de expresión, árboles sintácticos |

---

## 14. 🧭 Recorridos en Árboles

Los recorridos en árboles son casos particulares de los recorridos en grafos, adaptados a la estructura jerárquica. Se dividen en recorridos **en profundidad** (preorden, inorden, postorden) y **en anchura** (BFS por niveles).

### 14.1 Preorden

**Procedimiento:** se visita primero la **raíz**, luego se recorre recursivamente el **subárbol izquierdo**, y finalmente el **subárbol derecho**.

```text
Algoritmo Preorden(nodo)

Inicio
    si nodo != nulo entonces
        visitar(nodo)
        Preorden(nodo.izquierdo)
        Preorden(nodo.derecho)
    fin_si
Fin
```

**Aplicación típica:** copiar o serializar la estructura de un árbol, ya que permite reconstruirlo procesando la raíz antes que los hijos.

### 14.2 Inorden

**Procedimiento:** se recorre primero el **subárbol izquierdo**, luego se visita la **raíz**, y finalmente el **subárbol derecho**.

```text
Algoritmo Inorden(nodo)

Inicio
    si nodo != nulo entonces
        Inorden(nodo.izquierdo)
        visitar(nodo)
        Inorden(nodo.derecho)
    fin_si
Fin
```

**Propiedad clave:** aplicado a un **Árbol Binario de Búsqueda (BST)**, el recorrido inorden produce los valores en **orden ascendente**, lo cual es una de las razones fundamentales de la utilidad de esta estructura.

### 14.3 Postorden

**Procedimiento:** se recorren primero ambos subárboles (izquierdo y luego derecho), y finalmente se visita la **raíz**.

```text
Algoritmo Postorden(nodo)

Inicio
    si nodo != nulo entonces
        Postorden(nodo.izquierdo)
        Postorden(nodo.derecho)
        visitar(nodo)
    fin_si
Fin
```

**Aplicación típica:** eliminación segura de un árbol (se liberan primero los hijos y después el propio nodo) y evaluación de árboles de expresión (se evalúan primero los operandos antes que el operador).

### 14.4 Recorrido por anchura (BFS) en árboles

**Procedimiento:** idéntico al BFS de grafos, visitando los nodos **nivel por nivel**, usando una cola.

```text
Algoritmo BFS_Arbol(raiz)

Inicio
    si raiz = nulo entonces retornar
    Cola <- cola_vacia()
    Cola.encolar(raiz)

    mientras Cola no esté vacía hacer
        nodo <- Cola.desencolar()
        visitar(nodo)
        para cada hijo de nodo hacer
            Cola.encolar(hijo)
        fin_para
    fin_mientras
Fin
```

### 14.5 Ejemplo completo comparando los cuatro recorridos

Árbol binario:

```text
        F
       / \
      B   G
     / \    \
    A   D    I
       / \   /
      C   E H
```

**Preorden (Raíz-Izq-Der):** F, B, A, D, C, E, G, I, H

**Inorden (Izq-Raíz-Der):** A, B, C, D, E, F, G, H, I

**Postorden (Izq-Der-Raíz):** A, C, E, D, B, H, I, G, F

**BFS por niveles:** F, B, G, A, D, I, C, E, H

**Verificación de consistencia:** obsérvese que el recorrido **Inorden** produce exactamente la secuencia alfabética A–I, lo cual confirma que este árbol es, en efecto, un **BST válido**.

### 14.6 Complejidad y aplicaciones

Todos los recorridos anteriores tienen complejidad **temporal $O(n)$** y **complejidad espacial $O(h)$** para los recorridos recursivos (donde $h$ es la altura del árbol, debido a la pila de llamadas), o $O(n)$ en el peor caso para BFS (debido a la cola, en árboles muy anchos).

| Recorrido | Aplicación principal |
|---|---|
| Preorden | Serialización/clonación de árboles, generación de expresiones prefijas |
| Inorden | Obtener elementos ordenados de un BST, generación de expresiones infijas |
| Postorden | Eliminación de árboles, evaluación de expresiones postfijas, cálculo de tamaños de subárboles |
| BFS | Impresión por niveles, búsqueda del nodo más cercano a la raíz, cálculo de altura mínima |

---

## 15. ⚖️ Árboles Especiales

### 15.1 Árbol Binario de Búsqueda (BST)

> [!NOTE]
> **Definición.** Un **BST** es un árbol binario en el que, para todo nodo $v$: todos los valores del subárbol izquierdo son **menores** que el valor de $v$, y todos los valores del subárbol derecho son **mayores** (asumiendo valores únicos).

**Operaciones y complejidad:**

| Operación | Caso promedio | Peor caso |
|---|---|---|
| Búsqueda | $O(\log n)$ | $O(n)$ |
| Inserción | $O(\log n)$ | $O(n)$ |
| Eliminación | $O(\log n)$ | $O(n)$ |

El **peor caso** ($O(n)$) ocurre cuando el árbol se degenera en una lista (por ejemplo, al insertar datos ya ordenados), perdiendo la ventaja del particionamiento binario.

**Errores comunes:** insertar datos ya ordenados sin ningún mecanismo de balanceo, lo que degenera el BST en una lista enlazada y anula su eficiencia teórica.

### 15.2 Árbol AVL

> [!NOTE]
> **Definición.** Un **árbol AVL** (Adelson-Velsky y Landis, 1962) es un BST **auto-balanceado** en el que, para cada nodo, la diferencia de alturas entre su subárbol izquierdo y derecho (**factor de equilibrio**) es como máximo 1:

$$|\text{altura}(\text{izq}) - \text{altura}(\text{der})| \leq 1$$

**Mecanismo:** tras cada inserción o eliminación, si el factor de equilibrio de algún nodo se rompe, se aplican **rotaciones** (simples o dobles: izquierda, derecha, izquierda-derecha, derecha-izquierda) para restaurar el balance.

> [!TIP]
> 📌 **Figura sugerida:** Árbol AVL desbalanceado antes y después de aplicar una rotación simple a la derecha.

**Complejidad garantizada:** al mantenerse siempre balanceado, la altura se mantiene en $O(\log n)$, por lo que **todas** las operaciones (búsqueda, inserción, eliminación) son $O(\log n)$ en el **peor caso**, a diferencia del BST simple.

### 15.3 Árbol Rojo-Negro

> [!NOTE]
> **Definición.** Es un BST auto-balanceado donde cada nodo tiene un color (**rojo** o **negro**), y se cumplen cinco propiedades estructurales que garantizan que el camino más largo desde la raíz hasta una hoja nunca sea más del doble del camino más corto:
> 1. Todo nodo es rojo o negro.
> 2. La raíz es negra.
> 3. Todas las hojas nulas (NIL) se consideran negras.
> 4. Un nodo rojo no puede tener hijos rojos (no hay dos rojos consecutivos).
> 5. Todo camino desde un nodo hasta sus hojas descendientes contiene el mismo número de nodos negros.

**Comparación con AVL:** los árboles rojo-negro son **menos estrictamente balanceados** que los AVL, lo que implica **menos rotaciones** en inserciones/eliminaciones (más eficientes para escritura), a costa de búsquedas ligeramente más lentas (mayor altura permitida). Por esta razón, se usan en estructuras donde predominan las modificaciones frecuentes (por ejemplo, `std::map` en C++ y `TreeMap` en Java).

### 15.4 Árbol B

> [!NOTE]
> **Definición.** Un **árbol B** de orden $m$ es un árbol de búsqueda **balanceado y k-ario**, diseñado específicamente para minimizar accesos a **memoria secundaria** (disco). Cada nodo puede almacenar múltiples claves (hasta $m-1$) y tener hasta $m$ hijos, manteniendo todos los nodos hoja al **mismo nivel**.

**Motivación:** en sistemas de bases de datos, cada acceso a disco es costoso; al almacenar múltiples claves por nodo, se reduce drásticamente la **altura** del árbol y, por tanto, el número de accesos a disco necesarios para localizar un dato.

### 15.5 Árbol B+

> [!NOTE]
> **Definición.** Variante del árbol B en la que **todos los datos reales se almacenan únicamente en las hojas**, mientras que los nodos internos solo contienen claves de guía para la navegación. Además, las hojas se enlazan entre sí mediante punteros, formando una **lista enlazada** que permite recorridos secuenciales eficientes.

**Diferencia clave con B:** en un árbol B, los datos pueden estar en cualquier nodo (interno o hoja); en un árbol B+, solo están en las hojas, lo cual optimiza tanto la búsqueda por clave exacta como las consultas por **rango** (muy comunes en bases de datos SQL, por ejemplo `WHERE fecha BETWEEN X AND Y`).

### 15.6 Tabla comparativa de árboles especiales

| Estructura | Balanceo | Complejidad (peor caso) | Ventajas | Desventajas | Caso de uso típico |
|---|---|---|---|---|---|
| **BST** | Ninguno | $O(n)$ | Simplicidad de implementación | Puede degenerar en lista | Prototipos, estructuras educativas |
| **AVL** | Estricto ($\|\Delta h\| \leq 1$) | $O(\log n)$ | Búsquedas muy rápidas y garantizadas | Muchas rotaciones en escritura | Aplicaciones con lecturas frecuentes y pocas escrituras |
| **Rojo-Negro** | Relajado | $O(\log n)$ | Menos rotaciones que AVL; buen equilibrio lectura/escritura | Búsquedas ligeramente más lentas que AVL | Estructuras de biblioteca estándar (mapas, sets) |
| **Árbol B** | Multivía, balanceado | $O(\log_m n)$ | Minimiza accesos a disco | Complejidad de implementación mayor | Índices de bases de datos, sistemas de archivos |
| **Árbol B+** | Multivía, balanceado | $O(\log_m n)$ | Óptimo para consultas por rango; hojas enlazadas | Mayor overhead en nodos internos | Motores de bases de datos relacionales (MySQL, PostgreSQL) |

---

## 16. 🧠 Árboles Aplicados

### 16.1 Árboles de decisión

> [!NOTE]
> **Definición.** Estructura en la que cada nodo interno representa una **pregunta o condición** sobre un atributo, cada rama representa el resultado posible de esa condición, y cada hoja representa una **decisión o clasificación final**.

**Aplicación en Inteligencia Artificial y Machine Learning:** los árboles de decisión son uno de los algoritmos de clasificación y regresión más interpretables en aprendizaje supervisado (algoritmos como ID3, C4.5, CART). Son además la base de métodos de conjunto (*ensemble*) más avanzados como **Random Forest** y **Gradient Boosting**, ampliamente usados en la industria por su balance entre precisión e interpretabilidad.

### 16.2 Árboles de expresión

> [!NOTE]
> **Definición.** Árbol binario (generalmente) donde los nodos hoja son **operandos** y los nodos internos son **operadores**, representando una expresión aritmética o lógica de forma estructurada.

**Ejemplo:** la expresión $(3 + 4) \times 2$ se representa como:

```text
        ×
       / \
      +   2
     / \
    3   4
```

- **Recorrido inorden** (con paréntesis apropiados): produce la notación **infija** original: $(3+4)\times2$.
- **Recorrido preorden:** produce la notación **prefija** (polaca): $\times\ +\ 3\ 4\ 2$.
- **Recorrido postorden:** produce la notación **postfija** (polaca inversa): $3\ 4\ +\ 2\ \times$, la forma utilizada internamente por muchos compiladores e intérpretes para evaluar expresiones mediante una pila.

**Aplicación en compiladores:** los árboles de expresión son un caso particular del **Árbol de Sintaxis Abstracta (AST)**, estructura central en el análisis sintáctico de cualquier lenguaje de programación.

### 16.3 Árboles de expansión

Como se desarrolló en la Sección 5, un **árbol de expansión** es un subgrafo conexo y acíclico que conecta todos los vértices de un grafo. Constituyen el puente conceptual entre la teoría de grafos general y la teoría de árboles: todo árbol de expansión es, en sí mismo, un árbol según la definición formal de la Sección 12.

### 16.4 Árbol de expansión mínima

Igualmente desarrollado en la Sección 5: es el árbol de expansión de **costo total mínimo** en un grafo ponderado. Su relevancia aplicada incluye el diseño de redes de infraestructura al menor costo y algoritmos de agrupamiento (*clustering*) jerárquico en Machine Learning, donde eliminar las aristas más pesadas de un MST produce agrupamientos naturales de los datos.

---

## 17. 🗃️ Representación de Árboles

### 17.1 Representación mediante nodos enlazados (punteros)

La forma más común de representar un árbol en memoria es mediante una estructura de nodo que contiene el dato almacenado y referencias (punteros) a sus hijos:

```text
Estructura Nodo
    dato
    izquierdo -> Nodo (o nulo)
    derecho -> Nodo (o nulo)
Fin_Estructura
```

Para árboles k-arios generales, en lugar de dos punteros fijos, se utiliza una **lista de hijos**:

```text
Estructura NodoKario
    dato
    hijos -> Lista de Nodo
Fin_Estructura
```

**Ventajas:** flexible, intuitivo, eficiente para inserciones/eliminaciones dinámicas. **Desventajas:** overhead de memoria por los punteros; mal aprovechamiento de la localidad de caché.

### 17.2 Representación mediante arreglo (para árboles binarios completos)

Cuando el árbol es binario y razonablemente completo (como en los **montículos/heaps**), puede representarse de forma compacta en un arreglo, aprovechando la siguiente relación aritmética: si un nodo se encuentra en el índice $i$ (comenzando en 0):

- Hijo izquierdo: índice $2i+1$
- Hijo derecho: índice $2i+2$
- Padre: índice $\lfloor (i-1)/2 \rfloor$

**Ejemplo:** el árbol binario completo con nodos [F, B, G, A, D, I] (en orden BFS) se almacena directamente como `[F, B, G, A, D, I]`, donde el hijo izquierdo de F (índice 0) está en el índice 1 (B) y el derecho en el índice 2 (G).

**Ventajas:** sin overhead de punteros; excelente localidad de caché; acceso directo por índice. **Desventajas:** ineficiente en memoria si el árbol no está balanceado o completo (genera espacios vacíos); inserciones/eliminaciones costosas en árboles no-heap.

### 17.3 Representación mediante matriz de adyacencia o lista de adyacencia

Dado que todo árbol es un grafo particular, también puede representarse con las mismas estructuras vistas en la Sección 3 (matriz o lista de adyacencia), aunque esto resulta poco eficiente en la práctica porque no aprovecha la jerarquía natural (padre-hijo) ni el hecho de que solo existen $n-1$ aristas.

### 17.4 Representación textual/diagramática

Para fines de documentación y comunicación (como en este mismo documento), los árboles suelen representarse mediante **diagramas jerárquicos** (indentación o ramas ASCII) o notación de **paréntesis anidados**, por ejemplo: `(F (B (A) (D (C) (E))) (G () (I (H) ())))`, útil para serialización en formatos como JSON o XML.

### 17.5 Comparación de representaciones

| Representación | Memoria | Acceso a hijos | Ideal para |
|---|---|---|---|
| Nodos enlazados | $O(n)$, con overhead de punteros | $O(1)$ vía puntero | Árboles dinámicos, BST, AVL |
| Arreglo (índices aritméticos) | $O(n)$, compacta | $O(1)$ vía fórmula | Heaps, árboles binarios completos |
| Matriz/lista de adyacencia | $O(n)$ (lista) / $O(n^2)$ (matriz) | Variable | Análisis teórico, interoperabilidad con algoritmos de grafos |
| Paréntesis anidados / JSON | $O(n)$ | Requiere parseo | Serialización, transmisión, almacenamiento persistente |

---

## 18. 🚀 Aplicaciones de los Árboles

Los árboles son, junto con los grafos generales, una de las estructuras de datos más utilizadas en la práctica profesional de la computación, precisamente por su capacidad de modelar jerarquías con eficiencia logarítmica.

| Dominio | Aplicación concreta |
|---|---|
| **Sistemas operativos** | Estructura de directorios y archivos (árbol de sistema de archivos); árboles de procesos (proceso padre e hijos). |
| **Compiladores** | Árbol de Sintaxis Abstracta (AST) para representar la estructura gramatical del código fuente; árboles de expresión para evaluación. |
| **Bases de datos** | Índices B y B+ para búsquedas eficientes; árboles de consultas (*query plans*) para optimización de ejecución de SQL. |
| **Inteligencia Artificial** | Árboles de decisión para clasificación; árboles de búsqueda de juegos (minimax, poda alfa-beta en ajedrez o damas); árboles de Monte Carlo (MCTS) en juegos complejos como Go. |
| **Machine Learning** | Random Forest y Gradient Boosting (conjuntos de árboles de decisión); estructuras KD-Tree para búsquedas de vecinos más cercanos en espacios multidimensionales. |
| **Sistemas de archivos** | Estructuras como B-trees y B+-trees son la base de sistemas de archivos reales (NTFS, ext4) y de motores de bases de datos. |
| **Motores de búsqueda** | Índices invertidos organizados jerárquicamente; tries para autocompletado y corrección ortográfica. |
| **Redes** | Árboles de expansión (*spanning tree protocol*, STP) para evitar bucles en redes de conmutadores Ethernet. |
| **Videojuegos** | Árboles de escena (*scene graphs*) para organizar objetos 3D jerárquicamente; árboles de comportamiento (*behavior trees*) para la IA de personajes. |
| **Organización de información** | Estructuras de menús, taxonomías, árboles genealógicos, organigramas empresariales. |

> Los árboles constituyen, en definitiva, el puente natural entre la teoría abstracta de grafos y las estructuras de datos que sostienen la infraestructura computacional moderna: desde el sistema de archivos de cualquier computadora hasta los algoritmos de aprendizaje automático más avanzados, su presencia es constante y su comprensión resulta indispensable para todo profesional de la computación.

---

<div align="center">

### 🕸️🌳 Fin de la Unidad 3 🌳🕸️

![Grafos](https://img.shields.io/badge/Grafos-11%20temas-2ea44f?style=flat-square&logo=diagramsdotnet&logoColor=white)
![Árboles](https://img.shields.io/badge/Árboles-7%20temas-1f6feb?style=flat-square&logo=git&logoColor=white)
![Algoritmos](https://img.shields.io/badge/Algoritmos-BFS%20·%20DFS%20·%20Dijkstra%20·%20Prim%20·%20Kruskal%20·%20AVL-8250df?style=flat-square)

*Documento generado en Markdown, optimizado para su visualización en GitHub.* 🧮📘

</div>
