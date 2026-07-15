 <div align="center">

# 🕸️🌳 Unidad 3 — Grafos y Árboles 🌳🕸️

### *Matemáticas Discretas · Portafolio Académico*

![Tema](https://img.shields.io/badge/Tema-Teor%C3%ADa%20de%20Grafos-2ea44f?style=for-the-badge&logo=graphql&logoColor=white)
![Tema](https://img.shields.io/badge/Tema-%C3%81rboles-1f6feb?style=for-the-badge&logo=git&logoColor=white)
![Nivel](https://img.shields.io/badge/Nivel-Universitario-8250df?style=for-the-badge&logo=bookstack&logoColor=white)
![Formato](https://img.shields.io/badge/Formato-Markdown-orange?style=for-the-badge&logo=markdown&logoColor=white)
![Estado](https://img.shields.io/badge/Estado-Completo-success?style=for-the-badge&logo=checkmarx&logoColor=white)

</div>

> [!NOTE]
> 💡 **Enfoque del documento:** fundamentos teóricos, algoritmos, representación computacional y aplicaciones reales en Ciencias de la Computación, con pseudocódigo y ejemplos resueltos de forma concisa.

<div align="center">

`🔷 Fundamentos`  •  `🧩 Clasificación`  •  `🗂️ Representación`  •  `🧭 Recorridos`  •  `🛣️ Caminos Mínimos`  •  `🚰 Flujo Máximo`  •  `🎨 Coloreo`  •  `🌉 Puentes`  •  `⚖️ Árboles Especiales`

![Grafos](https://img.shields.io/badge/📚_Secciones_Grafos-11-2ea44f?style=flat-square)
![Árboles](https://img.shields.io/badge/📚_Secciones_Árboles-7-1f6feb?style=flat-square)
![Algoritmos](https://img.shields.io/badge/🧮_Algoritmos_cubiertos-15%2B-8250df?style=flat-square)

</div>

---

<div align="center">

### 🕸️ P A R T E   I — G R A F O S 🕸️

*"Un mapa de relaciones donde cada línea cuenta una conexión."*

</div>

---

# 🕸️ GRAFOS

## 1. 🔷 Fundamentos de los Grafos

Un **grafo** modela relaciones binarias entre elementos: puntos (vértices) unidos por líneas (aristas). Cualquier sistema de relaciones —amistades, rutas, dependencias— puede representarse así.

> [!NOTE]
> **Definición.** Un grafo es un par $G=(V,E)$, donde $V$ es un conjunto finito de **vértices** y $E$ es un conjunto de **aristas** que relacionan pares de vértices. Si es **no dirigido**, cada arista es $\{u,v\}$; si es **dirigido**, es un par ordenado $(u,v)$.

Notación: $|V|=n$ (orden), $|E|=m$ (tamaño).

### 📋 Terminología esencial

| Término | Definición |
|---|---|
| Adyacencia | Dos vértices unidos por una arista |
| Grado $\deg(v)$ | N.º de aristas incidentes a $v$ (en dirigidos: $\deg^+$ salida, $\deg^-$ entrada) |
| Camino | Secuencia de vértices adyacentes sin repetir aristas |
| Ciclo | Camino cerrado con al menos una arista |
| Lazo | Arista que conecta un vértice consigo mismo |
| Aristas paralelas | Varias aristas entre el mismo par de vértices |
| Subgrafo | $G'=(V',E')$ con $V'\subseteq V$, $E'\subseteq E$ |

> [!IMPORTANT]
> 🏆 **Lema del apretón de manos:** $\sum_{v\in V}\deg(v) = 2|E|$. Consecuencia: todo grafo no dirigido tiene un número **par** de vértices de grado impar.

**Ejemplo:** $V=\{A,B,C,D,E\}$, $E=\{AB,AC,BC,CD,DE\}$. Grados: A=2, B=2, C=3, D=2, E=1 → suma=10=2(5) ✅.

> [!TIP]
> 📌 **Figura sugerida:** Grafo no dirigido de 5 vértices con un triángulo A-B-C y una rama C-D-E.

**Aplicaciones:** redes sociales (usuarios/amistades), redes de computadoras (dispositivos/enlaces), ingeniería de software (módulos/dependencias), bioinformática (proteínas/interacciones).

---

## 2. 🧩 Clasificación de los Grafos

El tipo de grafo determina qué algoritmo aplicar. Principales criterios:

| Criterio | Tipos | Diferencia clave |
|---|---|---|
| Dirección | No dirigido / Dirigido | Aristas simétricas vs. orientadas |
| Peso | No ponderado / Ponderado | Aristas sin costo vs. con costo $w(e)$ |
| Multiplicidad | Simple / Multigrafo | Sin vs. con aristas paralelas o lazos |
| Conectividad interna | Completo ($K_n$) / Bipartito | Todo par conectado vs. dos particiones sin aristas internas |
| Conexidad | Conexo / Desconexo | Existe camino entre todo par vs. hay componentes separadas |
| Ciclicidad | Cíclico / Acíclico (DAG si es dirigido) | Contiene ciclos vs. no contiene |

En un grafo completo: $|E| = \binom{n}{2} = \frac{n(n-1)}{2}$. En dirigidos, la conexidad se distingue entre **fuerte** (camino en ambos sentidos entre todo par) y **débil** (conexo al ignorar dirección).

> [!TIP]
> 📌 **Figura sugerida:** Grafo bipartito trabajadores–tareas para un problema de asignación.

### 📊 Tabla comparativa

| Tipo | Ejemplo de uso |
|---|---|
| No dirigido | Amistades en redes sociales |
| Dirigido | Seguidores en Twitter/X |
| Ponderado | Rutas GPS con distancias |
| Simple | Grafo de dependencias de software |
| Multigrafo | Vuelos entre dos ciudades por varias aerolíneas |
| Completo | Torneos round-robin |
| Bipartito | Recomendación usuario-producto |
| Acíclico (DAG) | Pipeline de tareas CI/CD |

---

## 3. 🗂️ Representación de Grafos

### Matriz de adyacencia

> [!NOTE]
> **Definición.** Matriz $A_{n\times n}$ donde $A[i][j]=1$ (o el peso) si existe arista $(i,j)$, y $0$ si no. Simétrica en grafos no dirigidos.

**Ejemplo** ($V=\{A,B,C,D\}$, aristas AB, AC, BD, CD):

|   | A | B | C | D |
|---|---|---|---|---|
| **A** | 0 | 1 | 1 | 0 |
| **B** | 1 | 0 | 0 | 1 |
| **C** | 1 | 0 | 0 | 1 |
| **D** | 0 | 1 | 1 | 0 |

### Lista de adyacencia

> [!NOTE]
> **Definición.** Cada vértice almacena la lista de sus vecinos: $\text{Adj}: V \rightarrow \mathcal{P}(V)$.

```text
A -> [B, C]
B -> [A, D]
C -> [A, D]
D -> [B, C]
```

### ⚖️ Comparación

| Criterio | Matriz | Lista |
|---|---|---|
| Espacio | $O(n^2)$ | $O(n+m)$ |
| Verificar adyacencia | $O(1)$ | $O(\deg(v))$ |
| Recorrer vecinos | $O(n)$ | $O(\deg(v))$ |
| Ideal para | Grafos densos | Grafos dispersos (caso más común en la práctica) |

---

## 4. 🧭 Recorridos en Grafos

### BFS (Breadth-First Search)

Explora "por niveles" usando una **cola (FIFO)**; garantiza el camino más corto en número de aristas (grafos no ponderados).

```text
Algoritmo BFS(G, origen)
Inicio
    para cada v en G.V hacer visitado[v] <- falso; distancia[v] <- infinito
    Cola <- cola_vacia(); visitado[origen] <- verdadero; distancia[origen] <- 0
    Cola.encolar(origen)
    mientras Cola no esté vacía hacer
        u <- Cola.desencolar()
        para cada vecino w de u hacer
            si visitado[w] = falso entonces
                visitado[w] <- verdadero; distancia[w] <- distancia[u]+1
                padre[w] <- u; Cola.encolar(w)
            fin_si
        fin_para
    fin_mientras
    retornar distancia, padre
Fin
```

**Complejidad:** $O(V+E)$ tiempo, $O(V)$ espacio.

**Ejemplo:** grafo $A-B,A-C,B-D,C-D,C-E,D-F,E-F$, origen A. Distancias resultantes: A=0, B=1, C=1, D=2, E=2, F=3. Árbol BFS: A→B, A→C, B→D, C→E, D→F.

**Aplicaciones:** camino más corto no ponderado, "grados de separación" en redes sociales, rastreo web por niveles.

### DFS (Depth-First Search)

Explora "en profundidad" con **pila/recursión**; base para detectar ciclos y ordenar topológicamente.

```text
Algoritmo DFS_Visitar(G, u)
Inicio
    visitado[u] <- verdadero; tiempo <- tiempo+1; descubrimiento[u] <- tiempo
    para cada vecino w de u hacer
        si visitado[w] = falso entonces padre[w] <- u; DFS_Visitar(G, w)
    fin_para
    tiempo <- tiempo+1; finalizacion[u] <- tiempo
Fin
```

**Complejidad:** $O(V+E)$ tiempo, $O(V)$ espacio (pila de recursión).

**Ejemplo** (mismo grafo, orden alfabético): recorrido A→B→D→C→E→F, formando una única rama.

### ⚖️ BFS vs. DFS

| Criterio | BFS | DFS |
|---|---|---|
| Estructura | Cola (FIFO) | Pila / recursión |
| Camino mínimo (no ponderado) | Sí | No garantizado |
| Uso típico | Camino más corto, redes | Ciclos, backtracking, topología |

### Componentes Conexas

> [!NOTE]
> **Definición.** Subgrafo maximal donde todo par de vértices tiene camino entre sí.

Se obtiene ejecutando BFS/DFS desde cada vértice no visitado; cada ejecución completa descubre una componente. **Complejidad:** $O(V+E)$.

**Ejemplo:** con aristas A-B, B-C, D-E (F y G aislados) → 4 componentes: {A,B,C}, {D,E}, {F}, {G}.

**Aplicaciones:** subredes aisladas, comunidades en redes sociales, segmentación de imágenes.

### Orden Topológico

> [!NOTE]
> **Definición.** Ordenación lineal de los vértices de un **DAG** tal que, para toda arista $(u,v)$, $u$ aparece antes que $v$. Solo existe si el grafo es acíclico.

```text
Algoritmo DFS_Topologico(G, u, Pila)
Inicio
    visitado[u] <- verdadero
    para cada vecino w de u hacer
        si visitado[w] = falso entonces DFS_Topologico(G, w, Pila)
    fin_para
    Pila.apilar(u)   // se apila al finalizar
Fin
```

**Complejidad:** $O(V+E)$. **Ejemplo:** prerrequisitos Cálculo I → Cálculo II, Cálculo I → Física I → Física II, Cálculo II → Física II. Orden válido: Cálculo I → Física I → Cálculo II → Física II.

**Aplicaciones:** planificación de tareas (Make, CI/CD), prerrequisitos académicos, gestores de paquetes (npm, pip).

---

## 5. 🌲 Árboles de Expansión Mínima (MST)

> [!NOTE]
> **Definición.** Dado $G=(V,E,w)$ conexo y ponderado, un **árbol de expansión** incluye todos los vértices con $|V|-1$ aristas, sin ciclos. El **MST** es el de menor peso total posible.

**Propiedades:** si los pesos son distintos, el MST es único. La **propiedad de corte** (la arista mínima que cruza cualquier partición pertenece a algún MST) fundamenta los algoritmos de Prim y Kruskal.

**Grafo de referencia:** $A$-$B$(2), $A$-$C$(3), $B$-$C$(1), $B$-$D$(4), $C$-$D$(5), $C$-$E$(6), $D$-$E$(7).

### Algoritmo de Prim

Voraz: crece un único árbol agregando siempre la arista más barata que conecta con un vértice externo.

```text
Algoritmo Prim(G, origen)
Inicio
    para cada v hacer clave[v] <- infinito; en_MST[v] <- falso
    clave[origen] <- 0
    mientras existan vértices fuera del MST hacer
        u <- vértice de menor clave fuera del MST
        en_MST[u] <- verdadero
        para cada vecino w de u con peso p hacer
            si en_MST[w]=falso y p<clave[w] entonces clave[w]<-p; padre[w]<-u
        fin_para
    fin_mientras
Fin
```

**Complejidad:** $O(E\log V)$ con montículo binario.

**Resultado (origen A):** se agregan en orden A-B(2), B-C(1), B-D(4), C-E(6) → **MST = {A-B,B-C,B-D,C-E}, peso total = 13**.

### Algoritmo de Kruskal

Voraz: ordena todas las aristas por peso y las agrega si no forman ciclo (usando **Union-Find**).

```text
Algoritmo Kruskal(G)
Inicio
    ordenar E por peso ascendente
    para cada v hacer crear_conjunto(v)
    para cada arista (u,v,peso) en orden hacer
        si encontrar(u) != encontrar(v) entonces
            agregar arista al MST; unir(u,v)
    fin_para
Fin
```

**Complejidad:** $O(E\log E)$.

**Resultado:** B-C(1)✔, A-B(2)✔, A-C(3)✘ciclo, B-D(4)✔, C-D(5)✘ciclo, C-E(6)✔ → **mismo MST, peso total = 13**.

### ⚖️ Comparación

| Criterio | Prim | Kruskal |
|---|---|---|
| Estrategia | Crece un único árbol | Selecciona aristas globalmente |
| Estructura | Cola de prioridad | Union-Find |
| Ideal para | Grafos densos | Grafos dispersos |

**Aplicaciones:** redes eléctricas/telecom al menor costo, circuitos impresos, clustering en Machine Learning.

---

## 6. 🛣️ Algoritmos de Camino Mínimo

### Dijkstra

Calcula distancias mínimas desde **un origen** a todos los vértices, con **pesos no negativos**, mediante relajación voraz de aristas.

```text
Algoritmo Dijkstra(G, origen)
Inicio
    para cada v hacer distancia[v] <- infinito
    distancia[origen] <- 0
    mientras existan vértices no procesados hacer
        u <- no procesado con menor distancia
        marcar u como procesado
        para cada vecino w de u con peso p hacer
            si distancia[u]+p < distancia[w] entonces
                distancia[w] <- distancia[u]+p; padre[w] <- u
    fin_mientras
Fin
```

**Complejidad:** $O((V+E)\log V)$ con montículo. **No admite pesos negativos.**

**Ejemplo:** $A\to B(4), A\to C(1), C\to B(2), B\to D(5), C\to D(8), D\to E(3), C\to E(10)$. Resultado: A=0, C=1, B=3 (vía C), D=8 (vía B), E=11. **Camino mínimo A→D:** A→C→B→D, costo 8.

### Bellman-Ford

Admite **pesos negativos** (sin ciclos negativos); relaja todas las aristas $|V|-1$ veces (programación dinámica).

```text
Algoritmo BellmanFord(G, origen)
Inicio
    distancia[origen] <- 0; el resto <- infinito
    repetir (|V|-1) veces
        para cada arista (u,v,peso) hacer
            si distancia[u]+peso < distancia[v] entonces distancia[v] <- distancia[u]+peso
    fin_repetir
    // una pasada extra: si algo mejora, hay ciclo negativo
Fin
```

**Complejidad:** $O(V\cdot E)$.

**Ejemplo:** $A\to B(6), A\to C(4), B\to D(5), C\to B(-3), C\to D(2), D\to E(1)$. Tras convergencia: A=0, B=1, C=4, D=6, E=7. **Camino mínimo A→E:** A→C→B→D→E, costo 7. Sin ciclo negativo.

### Floyd-Warshall

Calcula distancias entre **todos los pares** simultáneamente (programación dinámica, permite vértices intermedios).

$$d_k[i][j] = \min\big(d_{k-1}[i][j],\ d_{k-1}[i][k]+d_{k-1}[k][j]\big)$$

```text
Algoritmo FloydWarshall(G)
Inicio
    inicializar dist[i][j] con pesos directos o infinito
    para k <- 1 hasta n hacer
        para i <- 1 hasta n hacer
            para j <- 1 hasta n hacer
                si dist[i][k]+dist[k][j] < dist[i][j] entonces
                    dist[i][j] <- dist[i][k]+dist[k][j]
    retornar dist
Fin
```

**Complejidad:** $O(V^3)$ tiempo, $O(V^2)$ espacio.

**Ejemplo:** $1\to2(3), 2\to3(1), 1\to3(8)$. Al evaluar $k=2$: $d[1][3]=\min(8,3+1)=4$ → mejora vía el vértice 2.

### ⚖️ Comparación general

| Criterio | Dijkstra | Bellman-Ford | Floyd-Warshall |
|---|---|---|---|
| Problema | 1 origen → todos | 1 origen → todos | Todos los pares |
| Pesos negativos | No | Sí | Sí |
| Detecta ciclo negativo | No | Sí | Sí |
| Complejidad | $O((V+E)\log V)$ | $O(V\cdot E)$ | $O(V^3)$ |
| Mejor uso | GPS, grafos dispersos | Arbitraje financiero, pesos negativos | Grafos pequeños, todas las distancias |

---

## 7. 🔁 Caminos y Ciclos Especiales

> [!NOTE]
> **Euleriano:** recorrido que usa **cada arista** exactamente una vez. **Hamiltoniano:** recorrido que visita **cada vértice** exactamente una vez. Ambos pueden ser *camino* (abierto) o *ciclo* (cerrado).

> [!IMPORTANT]
> 🏆 **Teorema de Euler:** existe ciclo euleriano ⟺ todos los vértices tienen grado par. Existe camino euleriano (no cíclico) ⟺ exactamente **dos** vértices de grado impar.

Origen histórico: los **Siete Puentes de Königsberg** (Euler, 1736), inicio formal de la Teoría de Grafos.

A diferencia del caso euleriano, **no existe condición eficiente general** para el caso hamiltoniano (problema **NP-completo**). El 🏆 **Teorema de Dirac** da una condición suficiente: si todo vértice tiene grado $\geq n/2$ ($n\geq3$), existe ciclo hamiltoniano.

### ⚖️ Diferencias clave

| Criterio | Euleriano | Hamiltoniano |
|---|---|---|
| Elemento recorrido una vez | Aristas | Vértices |
| Verificación | $O(V+E)$ (grados) | Sin algoritmo eficiente general (NP-completo) |

**Ejemplo:** grafo A-B, B-C, C-D, D-A, A-C. Grados: A=3, B=2, C=3, D=2 → 2 impares → **camino euleriano** A→B→C→D→A→C. También tiene **ciclo hamiltoniano**: A→B→C→D→A.

**Aplicaciones:** Euleriano → rutas de recolección de basura, secuenciación de ADN. Hamiltoniano → problema del viajante (TSP), diseño de circuitos VLSI.

---

## 8. 🚰 Flujo Máximo

> [!NOTE]
> **Red de flujo:** grafo dirigido con capacidades $c(u,v)$, una fuente $s$ y un sumidero $t$. Un **flujo** respeta $0\le f(u,v)\le c(u,v)$ y conserva flujo en cada vértice intermedio.

> [!IMPORTANT]
> 🏆 **Teorema Max-Flow Min-Cut:** el flujo máximo de $s$ a $t$ equivale a la capacidad del **corte mínimo** de la red.

### Ford-Fulkerson

Busca repetidamente **caminos de aumento** en el grafo residual hasta que no exista ninguno.

```text
Algoritmo FordFulkerson(G, s, t)
Inicio
    f <- 0 en todas las aristas
    mientras exista camino de aumento P (s→t) en grafo residual hacer
        cb <- capacidad residual mínima en P
        actualizar f a lo largo de P (+cb directo, -cb inverso)
    fin_mientras
    retornar flujo total desde s
Fin
```

### Edmonds-Karp

Especialización que elige el camino de aumento **más corto** vía BFS → complejidad $O(V\cdot E^2)$, independiente de las capacidades.

**Ejemplo:** $S\to A(10), S\to B(5), A\to B(3), A\to T(4), B\to T(9)$. Iteraciones: S-A-T(4), S-B-T(5), S-A-B-T(3) → **flujo máximo = 12**.

**Aplicaciones:** logística y transporte, ancho de banda en redes, emparejamiento bipartito máximo, segmentación de imágenes.

---

## 9. 🎨 Coloreo de Grafos

> [!NOTE]
> **Definición.** Asignar colores a los vértices de modo que **ningún par adyacente** comparta color. El **número cromático** $\chi(G)$ es el mínimo de colores necesarios.

- $\chi(G)=2$ ⟺ grafo bipartito con al menos una arista.
- $\chi(K_n)=n$.
- 🏆 **Teorema de los cuatro colores:** todo grafo planar cumple $\chi(G)\le4$.
- Calcular $\chi(G)$ exacto es **NP-difícil**; se usan heurísticas voraces.

```text
Algoritmo ColoreoVoraz(G)
Inicio
    para cada vértice v en algún orden hacer
        color[v] <- menor color no usado por vecinos ya coloreados
    fin_para
Fin
```

**Complejidad:** $O(V+E)$; usa a lo sumo $\Delta(G)+1$ colores (no siempre óptimo).

**Ejemplo:** ciclo $C_5$ (A-B-C-D-E-A), longitud impar → no bipartito → $\chi(C_5)=3$.

**Aplicaciones:** horarios de exámenes, asignación de frecuencias móviles, asignación de registros en compiladores, coloreo de mapas.

---

## 10. 🌉 Puentes y Puntos de Articulación

> [!NOTE]
> **Puente:** arista cuya eliminación aumenta el número de componentes conexas. **Punto de articulación:** vértice con la misma propiedad.

Se detectan con **DFS**, calculando $\text{disc}[u]$ (tiempo de descubrimiento) y $\text{low}[u]$ (menor tiempo alcanzable vía retroceso). Una arista $(u,v)$ es puente si $\text{low}[v]>\text{disc}[u]$; un vértice no raíz es articulación si $\text{low}[v]\ge\text{disc}[u]$ para algún hijo $v$ (la raíz lo es si tiene ≥2 hijos).

**Complejidad:** $O(V+E)$.

**Ejemplo:** triángulo A-B-C conectado por C-D a la rama D-E. **Puentes:** C-D y D-E. **Puntos de articulación:** C y D (las aristas del triángulo tienen vías alternas, por lo que no son puentes).

**Aplicaciones:** robustez de redes de telecomunicaciones/Internet, carreteras críticas, identificación de nodos clave en redes sociales o ciberseguridad.

---

## 11. 🚀 Aplicaciones de los Grafos

| Dominio | Aplicación |
|---|---|
| Redes sociales | Comunidades, influencia (PageRank), recomendación de contactos |
| Internet / GPS | Enrutamiento (OSPF), rutas óptimas (Dijkstra, A*) |
| Logística | TSP, flujo máximo para asignación de carga |
| Videojuegos | Pathfinding de NPC, árboles de decisión de IA |
| IA / ML | Redes bayesianas (DAGs), grafos de conocimiento, clustering vía MST |
| Bases de datos | Bases orientadas a grafos (Neo4j) |
| Bioinformática | Interacción proteína-proteína, ensamblaje de ADN (caminos eulerianos) |
| Telecomunicaciones | Diseño de redes al menor costo (MST), capacidad (flujo máximo) |

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

Un **árbol** modela jerarquías: carpetas, expresiones matemáticas, árboles genealógicos, clases en POO.

> [!NOTE]
> **Definición.** Grafo no dirigido $T=(V,E)$ **conexo y acíclico**. Tiene exactamente $n-1$ aristas y un único camino simple entre cualquier par de vértices. En un **árbol con raíz**, se distingue un vértice $r$ desde el cual se establece la jerarquía.

### 📋 Terminología

| Término | Definición |
|---|---|
| Padre / Hijo | Nodo anterior / posterior en la jerarquía |
| Hermanos | Comparten el mismo padre |
| Hoja | Nodo sin hijos |
| Nivel | N.º de aristas desde la raíz |
| Altura | Camino más largo desde un nodo hasta una hoja de su subárbol |
| Subárbol | Nodo + todos sus descendientes |

**Propiedades:** $n$ vértices ⟹ $n-1$ aristas; es el grafo conexo con mínimas aristas; todo árbol con ≥2 vértices tiene al menos 2 hojas; es bipartito y un caso particular de DAG si se orienta desde la raíz.

**Ejemplo:** raíz R con hijos A, B; A tiene hijos C, D; B tiene hijo E. $|V|=6$, $|E|=5=n-1$ ✅, altura=2.

---

## 13. 🍃 Clasificación de los Árboles

| Tipo | Máx. hijos/nodo | Restricción | Ejemplo de uso |
|---|---|---|---|
| Binario | 2 | Ninguna | BST, árboles de decisión |
| Binario completo | 2 | 0 o 2 hijos | Montículos (heaps) |
| Binario perfecto | 2 | Todos los niveles llenos ($2^{h+1}-1$ nodos) | Análisis teórico |
| K-ario | k | Ninguna | Árboles B, sistemas de archivos |
| Regular (k-regular) | k fijo | Todo nodo interno tiene exactamente k hijos | Torneos, decisión balanceada |
| Etiquetado | Variable | Nodos/aristas con datos asociados | Árboles de expresión |

**Nota:** un árbol binario **degenerado** (cada nodo con un solo hijo) equivale a una lista enlazada, con altura $n-1$.

---

## 14. 🧭 Recorridos en Árboles

| Recorrido | Orden | Aplicación |
|---|---|---|
| **Preorden** | Raíz → Izq → Der | Serialización/clonación |
| **Inorden** | Izq → Raíz → Der | En un BST produce orden ascendente |
| **Postorden** | Izq → Der → Raíz | Eliminación segura, evaluación de expresiones postfijas |
| **BFS** | Por niveles (cola) | Impresión por niveles, altura mínima |

```text
Algoritmo Inorden(nodo)
Inicio
    si nodo != nulo entonces
        Inorden(nodo.izquierdo); visitar(nodo); Inorden(nodo.derecho)
Fin
```

**Ejemplo** (árbol binario con raíz F, hijos B y G; B con hijos A y D; D con hijos C y E; G con hijo I; I con hijo H):

- **Preorden:** F,B,A,D,C,E,G,I,H
- **Inorden:** A,B,C,D,E,F,G,H,I *(orden alfabético → confirma BST válido)*
- **Postorden:** A,C,E,D,B,H,I,G,F
- **BFS:** F,B,G,A,D,I,C,E,H

**Complejidad:** $O(n)$ tiempo; espacio $O(h)$ recursivo o $O(n)$ para BFS.

---

## 15. ⚖️ Árboles Especiales

> [!NOTE]
> **BST:** para todo nodo, subárbol izquierdo < nodo < subárbol derecho. Búsqueda/inserción/eliminación: $O(\log n)$ promedio, **$O(n)$ peor caso** (degenera en lista si se insertan datos ordenados sin balanceo).

**AVL:** BST auto-balanceado; para cada nodo, $|\text{altura(izq)}-\text{altura(der)}|\le1$. Usa **rotaciones** tras cada inserción/eliminación para mantener el balance → garantiza $O(\log n)$ en el **peor caso**.

> [!TIP]
> 📌 **Figura sugerida:** Árbol AVL antes y después de una rotación simple a la derecha.

**Rojo-Negro:** BST balanceado por color (rojo/negro) con 5 propiedades estructurales (raíz negra, sin dos rojos consecutivos, mismo n.º de negros en todo camino a hoja). Menos estricto que AVL → **menos rotaciones**, ideal para escrituras frecuentes (`std::map`, `TreeMap`).

**Árbol B:** k-ario balanceado, cada nodo con múltiples claves; minimiza accesos a disco. **Árbol B+:** variante donde los datos solo están en las hojas, enlazadas entre sí → óptimo para consultas por rango (SQL).

### 📊 Comparación

| Estructura | Balanceo | Peor caso | Uso típico |
|---|---|---|---|
| BST | Ninguno | $O(n)$ | Educativo/prototipos |
| AVL | Estricto | $O(\log n)$ | Lecturas frecuentes |
| Rojo-Negro | Relajado | $O(\log n)$ | Librerías estándar (mapas/sets) |
| Árbol B | Multivía | $O(\log_m n)$ | Índices de bases de datos |
| Árbol B+ | Multivía | $O(\log_m n)$ | Motores SQL (MySQL, PostgreSQL) |

---

## 16. 🧠 Árboles Aplicados

**Árboles de decisión:** cada nodo interno es una condición, cada hoja una decisión. Base de **Random Forest** y **Gradient Boosting** en Machine Learning.

**Árboles de expresión:** operadores en nodos internos, operandos en hojas. Ejemplo: $(3+4)\times2$ →

```text
        ×
       / \
      +   2
     / \
    3   4
```

Inorden → infija $(3+4)\times2$; Preorden → prefija $\times+34\ 2$; Postorden → postfija $34+2\times$ (usada por compiladores). Caso particular: el **AST** (Árbol de Sintaxis Abstracta).

**Árboles de expansión / MST:** ya desarrollados en la Sección 5; conectan la teoría de grafos con la de árboles, y fundamentan el clustering jerárquico en ML.

---

## 17. 🗃️ Representación de Árboles

| Representación | Memoria | Ideal para |
|---|---|---|
| **Nodos enlazados** (punteros a hijos) | $O(n)$ con overhead | Árboles dinámicos, BST, AVL |
| **Arreglo** (índices: hijo izq=$2i+1$, der=$2i+2$, padre=$\lfloor(i-1)/2\rfloor$) | $O(n)$ compacta | Heaps, árboles binarios completos |
| **Matriz/lista de adyacencia** | $O(n)$–$O(n^2)$ | Interoperabilidad con algoritmos de grafos |
| **Paréntesis anidados / JSON** | $O(n)$ | Serialización y transmisión |

---

## 18. 🚀 Aplicaciones de los Árboles

| Dominio | Aplicación |
|---|---|
| Sistemas operativos | Sistema de archivos, árbol de procesos |
| Compiladores | AST, árboles de expresión |
| Bases de datos | Índices B/B+, planes de consulta |
| IA | Árboles de decisión, minimax, MCTS (Go) |
| Machine Learning | Random Forest, KD-Tree |
| Motores de búsqueda | Tries, índices invertidos |
| Redes | Spanning Tree Protocol (evita bucles en switches) |
| Videojuegos | Scene graphs, behavior trees |
| Organización | Menús, taxonomías, organigramas |

---

<div align="center">

### 🕸️🌳 Fin de la Unidad 3 🌳🕸️

![Grafos](https://img.shields.io/badge/Grafos-11%20temas-2ea44f?style=flat-square&logo=diagramsdotnet&logoColor=white)
![Árboles](https://img.shields.io/badge/Árboles-7%20temas-1f6feb?style=flat-square&logo=git&logoColor=white)
![Algoritmos](https://img.shields.io/badge/Algoritmos-BFS%20·%20DFS%20·%20Dijkstra%20·%20Prim%20·%20Kruskal%20·%20AVL-8250df?style=flat-square)

*Documento generado en Markdown, optimizado para su visualización en GitHub.* 🧮📘

</div> 

| 🧩 **Actividad / Proyecto** | 📁 **Recurso / Enlace** |
|-----------------------------|--------------------------|
| 🧠 ACD (Aprendizaje Colaborativo y Dirigido) | 📎 Repositorio ACD |
| 🔬 APE (Aprendizaje Práctico Experimental) | 📎 Carpeta APE |
| 📚 AA (Aprendizaje Autónomo) | 📎 Recursos AA |
| 💡 ABP (Aprendizaje Basado en Problemas) | 📎 Material ABP |
| 🗂️ Portafolio General | 📎 Documentos y anexos |

