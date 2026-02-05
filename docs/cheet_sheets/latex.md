# Math in Obsidian — Cheat Sheet (CLRS-friendly)

## Math Modes

### Inline math

Use **single `$`**

```md
The running time is $O(n \log n)$.
```

The running time is $O(n \log n)$.

### Block math (formulas on their own line)

Use **double `$$`**

```md
$$
T(n) = 2T(n/2) + \Theta(n)
$$
```

$$
T(n) = 2T(n/2) + \Theta(n)
$$

---

## Arithmetic Operators

```md
+   -   \times   \div
```

Examples:

```md
$a + b$
$a \times b$
$a \div b$
```

$$a + b$$
$$a \times b$$
$$a \div b$$

---

## Fractions

```md
\frac{a}{b}
```
$$
\frac{a}{b}
$$

```md
$$
\frac{n(n+1)}{2}
$$
```
$$
\frac{n(n+1)}{2}
$$

---

## Exponents & Subscripts

```md
a^2
x_i
x_{i+1}
```

$$a^2$$
$$x_i$$
$$x_{i+1}$$
```md
$$
n^{\log n}
$$
```

$$
n^{\log n}
$$

---

## Roots

```md
\sqrt{n}
\sqrt[k]{n}
```
$$
\sqrt{n}
$$
$$
\sqrt[k]{n}
$$
---

## Greek Letters (very common in CLRS)

```md
\alpha \beta \gamma \delta
\epsilon \theta \lambda
\mu \pi \sigma \phi \omega
```

$\alpha$  $\beta$  $\gamma$  $\delta$
$\epsilon$  $\theta$  $\lambda$
$\mu$   $\pi$  $\sigma$  $\phi$  $\omega$

Uppercase:

```md
\Gamma \Delta \Theta \Lambda \Sigma \Phi \Omega
```

$\Gamma$  $\Delta$
$\Theta$  $\Lambda$
$\Pi$  $\Sigma$  $\Phi$  $\Omega$

---

## Comparisons

```md
=   \neq
<   >   \le   \ge
```

$=$   $\neq$
$<$   $>$   $\le$   $\ge$


```md
a \le b
```

$$a \le b$$

---

## Big-O, Ω, Θ (CLRS core)

```md
O(n)
\Omega(n)
\Theta(n \log n)
```

Example:

```md
$$
T(n) = \Theta(n \log n)
$$
```

---

## Sets

```md
\in        \notin
\subset    \subseteq
\cup       \cap
\emptyset
```

$\in$        $\notin$
$\subset$    $\subseteq$
$\cup$      $\cap$
$\emptyset$

```md
x \in S
```

$x \in S$

---

## Summations & Products

```md
\sum_{i=1}^{n}
\prod_{i=1}^{n}
```

$$\sum_{i=1}^{n}$$
$$\prod_{i=1}^{n}$$

```md
$$
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
$$
```

$$
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
$$
---

## Limits

```md
\lim_{n \to \infty}
```

$$\lim_{n \to \infty}$$
```md
$$
\lim_{n \to \infty} \frac{1}{n} = 0
$$
```
$$
\lim_{n \to \infty} \frac{1}{n} = 0
$$
---

## Logarithms

```md
\log n
\log_2 n
\ln n
```
$$\log n$$
$$\log_2 n$$
$$\ln n$$
CLRS often assumes:

```md
\log n = \log_2 n
```

$$\log n = \log_2 n$$
---

## Functions

```md
f(n)
f : A \to B
```

```md
$$
f(n) = n^2 + 3n + 1
$$
```

$$
f(n) = n^2 + 3n + 1
$$
---

## Probability (used in randomized algorithms)

```md
\Pr
\mathbb{E}
```

```md
$$
\mathbb{E}[X] = \sum x \Pr(X=x)
$$
```

$$
\mathbb{E}[X] = \sum x \Pr(X=x)
$$
---

## Brackets & Grouping

```md
( a )
[ a ]
\{ a \}
```

Auto-size:

```md
\left( \frac{n}{2} \right)
```
$$\left( \frac{n}{2} \right)
$$
---

## Vectors & Matrices

```md
\vec{v}
\mathbf{A}
```

Matrix:

```md
$$
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$
```
$$
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}
$$

---

## Logical Symbols (proofs)

```md
\forall   \exists
\land     \lor
\neg
\Rightarrow
\Leftrightarrow
```

$\forall$   $\exists$
$\land$     $\lor$
$\neg$
$\Rightarrow$ $\Leftrightarrow$
---
## Algorithm Analysis Staples (CLRS gold)

```md
n!
2^n
\log n
n \log n
```

```md
$$
O(1) < O(\log n) < O(n) < O(n \log n) < O(n^2)
$$
```
$$
O(1) < O(\log n) < O(n) < O(n \log n) < O(n^2)
$$

---

## Obsidian Tips for Math Notes 🔥

### Use headings + math blocks

```md
## The Master Theorem

$$
T(n) = aT\left(\frac{n}{b}\right) + f(n)
$$
```

### Inline explanations

```md
If $f(n) = \Theta(n^c)$, then case 2 applies.
```

### Reusable snippets

Create a note called:

```
Math Snippets
```

Copy-paste common formulas like:

```md
$$
T(n) = 2T(n/2) + n
$$
```

---

## Want next?

I can:

- 📘 Turn this into a **one-page CLRS math reference note**
    
- 🧠 Show **how to structure algorithm + proof notes**
    
- ✏️ Give you **ready-made templates** for each CLRS chapter
    

Just tell me how deep you want to go 🚀