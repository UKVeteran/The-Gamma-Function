<div align="center">
  <img src="https://img.shields.io/badge/Mathematics-Calculus%20%26%20Analysis-blue?style=for-the-badge&logo=mathematics&logoColor=white" alt="Math Badge" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License Badge" />
  <img src="https://img.shields.io/badge/Contributions-Welcome-brightgreen?style=for-the-badge" alt="Contributions Badge" />

  <hr />

  <h1>The Gamma Function — <code>Γ(z)</code></h1>
  <p><strong>A Comprehensive Overview, Mathematical Foundations, and Computational Implementations</strong></p>

  <p>
    <a href="#-overview">Overview</a> •
    <a href="#-mathematical-definition">Mathematical Definition</a> •
    <a href="#-key-properties">Key Properties</a> •
    <a href="#-visualizations">Visualizations</a> •
    <a href="#-computational-implementations">Implementations</a> •
    <a href="#-license">License</a>
  </p>
</div>

---

## 📝 Overview

The **Gamma Function**, denoted by the Greek uppercase letter **Γ (Gamma)**, is an extension of the factorial function to complex and real numbers. First introduced by Leonhard Euler in the 18th century, it stands as one of the most vital special functions in mathematical analysis, number theory, statistics, and quantum physics.

> 💡 **Why it matters:** While the traditional factorial $n!$ is restricted strictly to non-negative integers, the Gamma Function smoothly interpolates between these points, allowing mathematicians and engineers to compute "factorials" for numbers like $3.5$ or even complex values like $2 + 3i$.

---

## 📐 Mathematical Definition

For any complex number $z$ where the real part is strictly positive ($\text{Re}(z) > 0$), the Gamma Function is defined via the following convergent improper integral:

$$\Gamma(z) = \int_{0}^{\infty} t^{z-1} e^{-t} \, dt$$

### Analytic Continuation

For coordinates where $\text{Re}(z) \le 0$, the function cannot be directly evaluated by the integral above. Instead, it is extended to the rest of the complex plane (except at non-positive integers) using **analytic continuation** via the recurrence relation:

$$\Gamma(z) = \frac{\Gamma(z+1)}{z}$$

This reveals that the Gamma Function possesses **simple poles** (points where the function tends toward infinity) at $z = 0, -1, -2, -3, \dots$.

---

## ⚡ Key Properties

The Gamma Function obeys several elegant functional equations and identities:

| Property / Identity Name | Mathematical Formula | Significance |
| :--- | :--- | :--- |
| **Factorial Relation** | $\Gamma(n) = (n-1)!$ | Connects the function directly to standard integer factorials for $n \in \mathbb{N}$. |
| **Euler's Reflection Formula** | $\Gamma(z)\Gamma(1-z) = \frac{\pi}{\sin(\pi z)}$ | Allows evaluation of negative inputs; highlights that $\Gamma(1/2) = \sqrt{\pi}$. |
| **Legendre Duplication Formula** | $\Gamma(z)\Gamma\left(z + \frac{1}{2}\right) = 2^{1-2z} \sqrt{\pi} \, \Gamma(2z)$ | Useful for breaking down deep fractional intervals or doubling arguments. |
| **Stirling's Approximation** | $\Gamma(z+1) \approx \sqrt{2\pi z} \left(\frac{z}{e}\right)^z$ | Provides highly accurate asymptotic behavior for large values of $z$. |

---

## 📊 Visualizations

When plotted along the real axis, the function behaves as follows:
* For $x > 0$, it forms a smooth, parabolic U-shape curve, reaching a local minimum near $x \approx 1.46163$.
* For $x < 0$, it rapidly alternates between positive and negative vertical asymptotes at every integer step.

<br />

<div align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/e/e5/Gamma_plot.svg" alt="Gamma Function Plot along the Real Axis" width="550px" />
  <p><em>Figure 1: Behavior of Γ(x) along the real number line showing characteristic poles at non-positive integers.</em></p>
</div>

---

## 💻 Computational Implementations

In practical code execution, calculating the infinite integral directly is incredibly inefficient. Most modern mathematical libraries leverage either the **Lanczos Approximation** or the **Spouge Approximation** to evaluate values up to exceptional machine precision.

### 🐍 Python (SciPy)

In Python, native optimized implementations are available out-of-the-box in the `scipy.special` suite.

```python
import scipy.special as special

# Calculate Gamma for an integer
print(special.gamma(5))  # Output: 24.0 -> (5-1)! = 4! = 24

# Calculate Gamma for a float
print(special.gamma(2.5)) # Output: 1.329340388179137

# Calculate log-gamma (preferred for large numbers to prevent overflow)
print(special.gammaln(100)) # Output: 359.134205369575
