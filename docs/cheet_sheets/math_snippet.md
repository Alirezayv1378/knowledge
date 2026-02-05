# Math & Algorithm Analysis Snippets (CLRS)

---

## Big-O, Ω, Θ

Inline:
$O(1)$, $O(\log n)$, $O(n)$, $O(n \log n)$, $O(n^2)$

Block:
$$
T(n) = \Theta(n \log n)
$$

---

## Recurrences

Divide & Conquer:
$$
T(n) = aT\left(\frac{n}{b}\right) + f(n)
$$

Common example:
$$
T(n) = 2T\left(\frac{n}{2}\right) + n
$$

---

## Summations

Arithmetic sum:
$$
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
$$

General form:
$$
\sum_{i=1}^{n} f(i)
$$

---

## Logarithms

$$
\log n
$$

$$
\log_2 n
$$

CLRS assumption:
$$
\log n = \log_2 n
$$

---

## Exponents & Growth Rates

$$
n^2
$$

$$
2^n
$$

$$
n!
$$

Growth comparison:
$$
O(1) < O(\log n) < O(n) < O(n \log n) < O(n^2) < O(2^n)
$$

---

## Limits

$$
\lim_{n \to \infty} \frac{1}{n} = 0
$$

---

## Probability & Expectation

Probability:
$$
\Pr(X = x)
$$

Expectation:
$$
\mathbb{E}[X] = \sum x \Pr(X = x)
$$

---

## Sets

$$
x \in S
$$

$$
A \subseteq B
$$

$$
A \cup B \quad A \cap B
$$

---

## Logical Symbols (Proofs)

$$
\forall x \quad \exists y
$$

$$
A \Rightarrow B
$$

$$
A \Leftrightarrow B
$$

---

## Matrices

$$
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

---

## Functions

$$
f : A \to B
$$

$$
f(n) = n^2 + 3n + 1
$$

---

## Master Theorem (Template)

$$
T(n) = aT\left(\frac{n}{b}\right) + \Theta(n^c)
$$
