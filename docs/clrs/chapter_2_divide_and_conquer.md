# Divide and Conquer

## Definition
has three steps:
1.  **Divide** the problem into one or more subproblems that are smaller instances of the same problem.
2. **Conquer** the subproblems by solving them recursively.
3. **Combine** the subproblem solutions to form a solution to the original problem.

---
## Matrix Multiplication => $O(n^3)$

$$
C[i][j] = \sum_{k=1}^{n} A[i][k] \cdot B[k][j]  
$$
$$
A =  
\begin{pmatrix}  
a & b \\ 
c & d  
\end{pmatrix},  
\quad  
B =  
\begin{pmatrix}  
e & f \\  
g & h  
\end{pmatrix}  
$$
$$
C =  
\begin{pmatrix}  
ae + bg & af + bh \\  
ce + dg & cf + dh  
\end{pmatrix}  
$$
```sql
FUNCTION NormalMultiply(A, B):
    REQUIRE columns(A) == rows(B)

    n = rows(A)
    m = columns(B)
    k = columns(A)

    Create result matrix C of size n × m filled with 0

    FOR i from 0 to n-1:
        FOR j from 0 to m-1:
            FOR t from 0 to k-1:
                C[i][j] += A[i][t] * B[t][j]

    RETURN C

```
---
## Strassen’s algorithm => $O(n^{2.807})$
$$
A =  
\begin{pmatrix}  
a & b \\ 
c & d  
\end{pmatrix},  
\quad  
B =  
\begin{pmatrix}  
e & f \\  
g & h  
\end{pmatrix}  
$$
$$
\begin{aligned}
M_1 &= (a + d)(e + h)\\
M_2 &= (c + d)e\\
M_3 &= a(f - h)\\
M_4 &= d(g - e)\\
M_5 &= (a + b)h\\
M_6 &= (c - a)(e + f)\\
M_7 &= (b - d)(g + h)\\
\end{aligned}
$$
$$
\begin{aligned}  
C_{11} &= M_1 + M_4 - M_5 + M_7 \\
C_{12} &= M_3 + M_5 \\
C_{21} &= M_2 + M_4 \\
C_{22} &= M_1 - M_2 + M_3 + M_6  
\end{aligned}  
$$
$$
C =  
\begin{pmatrix}  
C_{11} & C_{12}\\
C_{21} & C_{22}
\end{pmatrix}
$$

```sql
FUNCTION Strassen(A, B):
    IF matrix size is small:
        RETURN NormalMultiply(A, B)

    Pad A and B to even square size if needed

    Split A into A11, A12, A21, A22
    Split B into B11, B12, B21, B22

    Compute 7 products recursively (M1 … M7)

    Combine M1 … M7 into result blocks C11, C12, C21, C22

    Merge blocks into full matrix C
    Remove padding

    RETURN C

```
---