<!--
=======================================================================
THE GAMMA FUNCTION - README.md (HTML Edition)
=======================================================================
This README is fully formatted in semantic HTML for GitHub repositories.
It includes mathematical definitions, properties, implementations, and 
visualization layouts.
=======================================================================
-->

<div align="center">
  <img src="https://img.shields.io/badge/Mathematics-Calculus%20%26%20Analysis-blue?style=for-the-badge&logo=mathematics&logoColor=white" alt="Math Badge" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License Badge" />
  <img src="https://img.shields.io/badge/Contributions-Welcome-brightgreen?style=for-the-badge" alt="Contributions Badge" />

  <hr />

  <h1>The Gamma Function — <code>Γ(z)</code></h1>
  <p><strong>A Comprehensive Overview, Mathematical Foundations, and Computational Implementations</strong></p>

  <p>
    <a href="#overview">Overview</a> •
    <a href="#mathematical-definition">Mathematical Definition</a> •
    <a href="#key-properties">Key Properties</a> •
    <a href="#visualizations">Visualizations</a> •
    <a href="#computational-implementations">Implementations</a> •
    <a href="#license">License</a>
  </p>
</div>

<main>

  <!-- OVERVIEW SECTION -->
  <section id="overview">
    <h2>## 📝 Overview</h2>
    <p>
      The <strong>Gamma Function</strong>, denoted by the Greek uppercase letter <strong>Γ (Gamma)</strong>, is an extension of the factorial function to complex and real numbers. First introduced by Leonhard Euler in the 18th century, it stands as one of the most vital special functions in mathematical analysis, number theory, statistics, and quantum physics.
    </p>
    <blockquote>
      💡 <strong>Why it matters:</strong> While the traditional factorial <code>n!</code> is restricted strictly to non-negative integers, the Gamma Function smoothly interpolates between these points, allowing mathematicians and engineers to compute "factorials" for numbers like <code>3.5</code> or even complex values like <code>2 + 3i</code>.
    </blockquote>
  </section>

  <hr />

  <!-- MATHEMATICAL DEFINITION SECTION -->
  <section id="mathematical-definition">
    <h2>## 📐 Mathematical Definition</h2>
    <p>For any complex number $z$ where the real part is strictly positive ($\text{Re}(z) > 0$), the Gamma Function is defined via the following convergent improper integral:</p>

    $$\Gamma(z) = \int_{0}^{\infty} t^{z-1} e^{-t} \, dt$$

    <h3>Analytic Continuation</h3>
    <p>
      For coordinates where $\text{Re}(z) \le 0$, the function cannot be directly evaluated by the integral above. Instead, it is extended to the rest of the complex plane (except at non-positive integers) using <strong>analytic continuation</strong> via the recurrence relation:
    </p>

    $$\Gamma(z) = \frac{\Gamma(z+1)}{z}$$

    <p>
      This reveals that the Gamma Function possesses <strong>simple poles</strong> (points where the function tends toward infinity) at $z = 0, -1, -2, -3, \dots$.
    </p>
  </section>

  <hr />

  <!-- KEY PROPERTIES SECTION -->
  <section id="key-properties">
    <h2>## ⚡ Key Properties</h2>
    
    <p>The Gamma Function obeys several elegant functional equations and identities:</p>

    <table width="100%">
      <thead>
        <tr>
          <th align="left">Property / Identity Name</th>
          <th align="left">Mathematical Formula</th>
          <th align="left">Significance</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><strong>Factorial Relation</strong></td>
          <td>$\Gamma(n) = (n-1)!$</td>
          <td>Connects the function directly to standard integer factorials for $n \in \mathbb{N}$.</td>
        </tr>
        <tr>
          <td><strong>Euler's Reflection Formula</strong></td>
          <td>$\Gamma(z)\Gamma(1-z) = \frac{\pi}{\sin(\pi z)}$</td>
          <td>Allows evaluation of negative inputs; highlights that $\Gamma(1/2) = \sqrt{\pi}$.</td>
        </tr>
        <tr>
          <td><strong>Legendre Duplication Formula</strong></td>
          <td>$\Gamma(z)\Gamma\left(z + \frac{1}{2}\right) = 2^{1-2z} \sqrt{\pi} \, \Gamma(2z)$</td>
          <td>Useful for breaking down deep fractional intervals or doubling arguments.</td>
        </tr>
        <tr>
          <td><strong>Stirling's Approximation</strong></td>
          <td>$\Gamma(z+1) \approx \sqrt{2\pi z} \left(\frac{z}{e}\right)^z$</td>
          <td>Provides highly accurate asymptotic behavior for large values of $z$.</td>
        </tr>
      </tbody>
    </table>
  </section>

  <hr />

  <!-- VISUALIZATIONS SECTION -->
  <section id="visualizations">
    <h2>## 📊 Visualizations</h2>
    <p>When plotted along the real axis, the function behaves as follows:</p>
    <ul>
      <li>For $x > 0$, it forms a smooth, parabolic U-shape curve, reaching a local minimum near $x \approx 1.46163$.</li>
      <li>For $x < 0$, it rapidly alternates between positive and negative vertical asymptotes at every integer step.</li>
    </ul>
    
    <br />
    <div align="center">
      <!-- Standard analytical graph placeholder mapping the function behavior -->
      <img src="https://upload.wikimedia.org/wikipedia/commons/e/e5/Gamma_plot.svg" alt="Gamma Function Plot along the Real Axis" width="550px" />
      <p><em>Figure 1: Behavior of $\Gamma(x)$ along the real number line showing characteristic poles at non-positive integers.</em></p>
    </div>
  </section>

  <hr />

  <!-- COMPUTATIONAL IMPLEMENTATIONS SECTION -->
  <section id="computational-implementations">
    <h2>## 💻 Computational Implementations</h2>
    <p>
      In practical code execution, calculating the infinite integral directly is incredibly inefficient. Most modern mathematical libraries leverage either the <strong>Lanczos Approximation</strong> or the <strong>Spouge Approximation</strong> to evaluate values up to exceptional machine precision.
    </p>

    <h3>🐍 Python (SciPy)</h3>
    <p>In Python, native optimized implementations are available out-of-the-box in the <code>scipy.special</code> suite.</p>
    <pre><code>import scipy.special as special

# Calculate Gamma for an integer
print(special.gamma(5))  # Output: 24.0 -> (5-1)! = 4! = 24

# Calculate Gamma for a float
print(special.gamma(2.5)) # Output: 1.329340388179137

# Calculate log-gamma (preferred for large numbers to prevent overflow)
print(special.gammaln(100)) # Output: 359.134205369575
</code></pre>

    <h3>☕ JavaScript / Node.js</h3>
    <p>Below is a lightweight JavaScript execution utilizing a high-precision Lanczos approximation approximation:</p>
    <pre><code>function gamma(z) {
    const g = 7;
    const p = [
        0.99999999999980993, 676.5203681218851, -1259.1392167224028,
        771.32342877765313, -176.61502916214059, 12.507343278686905,
        -0.13857109526572012, 9.9843695780195716e-6, 1.5056327351493116e-7
    ];

    if (z &lt; 0.5) {
        return Math.PI / (Math.sin(Math.PI * z) * gamma(1 - z));
    }

    z -= 1;
    let x = p[0];
    for (let i = 1; i &lt; g + 2; i++) {
        x += p[i] / (z + i);
    }
    let t = z + g + 0.5;
    return Math.sqrt(2 * Math.PI) * Math.pow(t, z + 0.5) * Math.exp(-t) * x;
}

console.log(gamma(5));   // Output: 24
console.log(gamma(1.5)); // Output: 0.886226925452758 (Square root of PI / 2)
</code></pre>
  </section>

  <hr />


