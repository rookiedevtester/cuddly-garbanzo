### **Core Concept: The Algorithm**

At the heart of computer science lies the **algorithm**, a conceptual tool that transforms a task into a sequence of steps that a machine can execute. An algorithm represents the "intelligence" required to solve a problem, encoded in a way that the actual performance of the task no longer requires an understanding of the underlying principles—merely the ability to follow directions.

#### **I. Definitions and Properties**
*   **Informal Definition**: A set of steps defining how a task is performed, such as a recipe for cooking or directions for finding a location.
*   **Formal Definition**: An **ordered** set of **unambiguous**, **executable** steps that defines a **terminating** process.

**Key Characteristics for Exam Mastery**:
1.  **Ordered**: The steps must have a well-established structure for execution, whether sequential or parallel.
2.  **Unambiguous**: During execution, the information available must determine uniquely and completely the actions required by each step; no "creativity" is allowed from the executor.
3.  **Executable (Effective)**: Each step must be "doable" or "effective" (e.g., "list all integers" is not executable because it is an infinite task).
4.  **Terminating**: The process must eventually reach an end. *Note: While formal theory requires termination, applied computing often involves nonterminating processes like heart monitors, which are technically repeated algorithms.*

---

### **II. Algorithm vs. Program**
It is critical to distinguish between the **abstract algorithm** and its **physical realization**.
*   **Algorithm**: The conceptual method or "story".
*   **Program**: A representation of an algorithm designed for a computer to execute. A single algorithm can be expressed in many programming languages or even in the form of a digital circuit.
*   **Process**: The actual activity of executing an algorithm.

---

### **III. Algorithm Representation**
To communicate an algorithm to a machine, we use precisely defined building blocks called **primitives**.
1.  **Syntax**: The symbolic representation or "grammar" of the primitive.
2.  **Semantics**: The underlying meaning of the primitive.
3.  **Pseudocode**: A less formal notational system used during development to express ideas succinctly without the rigid constraints of a formal programming language.
4.  **Flowcharts**: A visual representation of an algorithm using geometric shapes to show the flow and direction of decisions.

---

### **IV. Algorithm Discovery & Design Paradigms**
Algorithm discovery is the artistic process of problem-solving. It often follows **Pólya’s Phases**: **Understand** the problem, **Devise** a plan, **Carry out** the plan, and **Evaluate** the solution.

**Common Design Paradigms**:
*   **Stepwise Refinement (Top-Down)**: Breaking a complex problem into smaller, more manageable subproblems until they match known primitives.
*   **Bottom-Up**: Creating solutions by combining existing, prefabricated components.
*   **Divide and Conquer**: Breaking a problem into smaller instances of the same problem (divide), solving them (conquer), and combining results (e.g., Merge Sort).
*   **Greedy Method**: Making the locally optimal choice at each stage with the hope of finding a global optimum (e.g., Prim's Algorithm).
*   **Brute-Force**: Systematically enumerating all potential solutions to find the best one; often impractical due to **combinatorial explosion**.

---

### **V. Basic Control Structures**
Algorithms are constructed using three fundamental building blocks:
1.  **Sequencing**: Executing steps in the order they are given.
2.  **Selection**: Using a Boolean condition to choose between alternative paths of execution (e.g., `if-then-else`).
3.  **Iteration (Loops)**: Repeating a block of code based on a condition (e.g., `while`, `repeat`, `for`).
4.  **Recursion**: A repetitive process where a function calls itself to solve a smaller instance of the same problem. Every recursive function must have a **base case** to terminate the process.

---

### **VI. Algorithm Analysis (Efficiency & Complexity)**
Algorithm analysis measures the resources (time and memory) required by an algorithm.
*   **Time Complexity**: Measuring the number of steps performed rather than the number of instructions in the code.
*   **Big O Notation**: A geometric prediction of an algorithm's worst-case resource usage as the input size ($N$) increases.

| Class | Name | Example Algorithm |
| :--- | :--- | :--- |
| **$O(1)$** | Constant | Accessing an array index |
| **$O(\log N)$** | Logarithmic | Binary Search |
| **$O(N)$** | Linear | Sequential Search |
| **$O(N \log N)$** | Linearithmic | Merge Sort, Heapsort |
| **$O(N^2)$** | Quadratic | Insertion Sort, Selection Sort |
| **$O(2^N)$** | Exponential | Listing all subsets of a set |

---

### **VII. Theoretical Limits of Algorithms**
Computer science theory seeks to understand the boundary between solvable and unsolvable problems.
*   **Computable Functions**: Functions for which an algorithm can be constructed to determine the output.
*   **Undecidable Problems**: Problems for which no single algorithm can be designed to always lead to a correct "yes" or "no" answer (e.g., the **Halting Problem**, which proves it is impossible to write a program that can check any other program for infinite loops).
*   **P vs. NP**:
    *   **P**: Problems solvable in "reasonable" (polynomial) time.
    *   **NP**: Problems where a candidate solution can be *verified* in polynomial time.
    *   **NP-Complete**: The hardest problems in NP; if an efficient solution is found for one, it solves all of them (e.g., Traveling Salesperson Problem).
