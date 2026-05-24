# Core Data Structures: Arrays

- **Tags:** #data-structures #computer-science #memory-management #linear-algebra
- **Related Notes:** [[Computer Memory Architecture]], [[Algorithmic Complexity (Big O)]], [[Search Algorithms]], [[Sorting Algorithms]], [[Tensors in Machine Learning]]

---

## I. Definition and Core Concepts

According to the *National Institute of Standards and Technology (NIST) Dictionary of Algorithms and Data Structures*, an **array** is an assemblage of items that are randomly accessible by integers known as indices. It serves as a foundational data structure to store and organize multiple elements of a homogeneous data type under a single identifier.

### Dimensionality and Classification
Arrays are classified structurally based on their geometric axes:

*   **One-Dimensional Array (1D):** A linear arrangement of items, often treated computationally as a list or a mathematical vector.
*   **Two-Dimensional Array (2D):** A grid structure composed of rows and columns, mapped conceptually as a table or a mathematical matrix.
*   **Tensors:** Multidimensional arrays extended to $d$-dimensions (where $d > 2$). These are foundational to high-dimensional engineering mathematics and Deep Learning frameworks (e.g., PyTorch, TensorFlow).

### Indexing Mechanisms
Every item within an array is addressable via a unique numerical coordinate system:
*   **Single vs. Multi-Index:** A 1D array requires a single index $i$. A 2D array requires an index pair $(i, j)$ tracking the row and column coordinates respectively.
*   **Base Indexing Systems:** 
    *   **0-Based Indexing:** Used by C, C++, Java, and Python. The first element resides at index `0`.
    *   **1-Based Indexing:** Used by Fortran, MATLAB, and Julia. The first element resides at index `1`.

---

## II. Memory Architecture and Address Polynomials

The defining mechanical advantage of an array is **$O(1)$ random access**. This efficiency is a direct consequence of storing elements in **contiguous memory cells** (physically adjacent hardware addresses). 

To map abstract indices to physical hardware memory locations, the runtime environment evaluates an **address polynomial**.

### 1D Array Addressing
For a 1D array with a base address (starting location) $x$ and an element data size $W$ (in bytes):

$$Address(A[i]) = x + (i - \text{base}) \cdot W$$

> [!NOTE]
> If an array is 1-based and elements are assumed to occupy 1 byte ($W = 1$), the formula simplifies to the traditional form: $x + (i - 1)$.

### Multidimensional Simulation (2D Arrays)
Because physical Random Access Memory (RAM) is linear (1D), multidimensional grids must be flattened into a linear sequence using one of two primary mapping conventions:

#### 1. Row-Major Order
Elements are stored sequentially row-by-row. This layout is standard in C, C++, and Python (`NumPy`).
For a 2D array with $R$ rows and $C$ columns, using **1-based indexing**, the physical memory location of element $A[i][j]$ is calculated as:

$$\text{Address}(A[i][j]) = x + \Big(C \cdot (i - 1) + (j - 1)\Big) \cdot W$$

Using **0-based indexing**, the formula becomes:

$$\text{Address}(A[i][j]) = x + (i \cdot C + j) \cdot W$$

#### 2. Column-Major Order
Elements are stored sequentially column-by-column. This layout is standard in Fortran and MATLAB.
Using **1-based indexing**, the address calculation for an array with $R$ rows is:

$$\text{Address}(A[i][j]) = x + \Big((i - 1) + R \cdot (j - 1)\Big) \cdot W$$

Using **0-based indexing**, the formula becomes:

$$\text{Address}(A[i][j]) = x + (i + j \cdot R) \cdot W$$

Visualizing a 2x3 Array Layout in Memory:
Matrix: [[A, B, C],
[D, E, F]]

Row-Major (C/C++):     [ A | B | C | D | E | F ]
Column-Major (Fortran):  [ A | D | B | E | C | F ]

---

## III. Memory Allocation and Safety

### Allocation Models
Languages handle the lifecycle of array storage through two predominant models:
*   **Manual Management:** In mid-level languages like C, memory must be explicitly allocated (e.g., via `malloc()`) and deallocated (`free()`). Neglecting to free memory blocks creates a **memory leak**, causing the application's memory footprint to expand indefinitely.
*   **Automated Management:** Modern high-level languages like Java and Python utilize **Garbage Collection (GC)** engines. The runtime system monitors array references and automatically reclaims memory allocations when objects are no longer reachable.

### Architectural Pitfalls
*   **Segmentation Faults:** Attempting to read or write to an index outside the allocated boundaries of an array (out-of-bounds access) forces the operating system to intervene. To protect memory integrity, the OS terminates the executing program with a segmentation fault (`SIGSEGV`).
*   **Alternative Architectures:** High-level environments like Java do not guarantee strict multi-dimensional contiguity. Instead, they often implement **Iliffe Vectors** (arrays of pointers pointing to separate arrays), allowing for irregular or jagged structures.

---

## IV. Array Operations & Algorithmic Complexity

| Operation | Algorithm | Time Complexity | Spatial Complexity | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **Traversal** | Linear Loop | $\Theta(N)$ | $O(1)$ | Visits every node exactly once. |
| **Search** | [[Sequential Search]] | $O(N)$ | $O(1)$ | Required for unsorted structural arrays. |
| **Search** | [[Binary Search]] | $O(\log N)$ | $O(1)$ | **Requires sorted input data.** |
| **Sort** | [[Merge Sort]] | $O(N \log N)$ | $O(N)$ | Stable sort; divide-and-conquer strategy. |
| **Sort** | [[Quicksort]] | $O(N \log N)$ average<br>$O(N^2)$ worst case | $O(\log N)$ stack space | Unstable sort; performance degrades on sorted inputs if pivot choices are naive. |

### Low-Level Masking
**Masking** applies bitwise operations (such as `AND`, `OR`, `XOR`) over array elements using a specific bit pattern (a mask). This technique enables high-performance filtering, subset evaluation, or structural modification without modifying adjacent data segments.

---

## V. Mathematical Implementations

Arrays serve as the primary concrete representation for abstract mathematical models across scientific computing:

### Linear Algebra
*   **Vectors:** Realized directly as one-dimensional arrays.
*   **Matrices:** Realized as two-dimensional arrays. Operations like vector addition require elemental parity ($\vec{u} + \vec{v}$), while the **dot product** sums the products of corresponding elements:

$$\vec{u} \cdot \vec{v} = \sum_{i=0}^{n-1} u_i v_i$$

### Discrete Structures
*   **Binary Relations:** A relation $R$ on finite sets can be represented via a 2D boolean adjacency matrix, where entry $M[i][j] = 1$ if $(x_i, y_j) \in R$ and $0$ otherwise.
*   **Direct Products:** The Cartesian/Direct Product $A \times B$ yields a rectangular space of coordinate pairs whose total allocation footprint corresponds to the product of their cardinalities: $|A| \cdot |B|$.
*   **Functions:** Discrete function graphs can be mapped explicitly as arrays containing tuple structures $(x, f(x))$.

### Algebraic Polynomials
Polynomial expressions can be represented strictly via a single array of coefficients, where the array index explicitly corresponds to the variable's exponent.

$$P(x) = a_n x^n + a_{n-1} x^{n-1} + \dots + a_1 x + a_0$$

```python
# Representing P(x) = 5x^3 - 2x + 7
# Index maps directly to the power: [power 0, power 1, power 2, power 3]
polynomial_coefficients = [7, -2, 0, 5]
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg2NTY4NDkzMF19
-->