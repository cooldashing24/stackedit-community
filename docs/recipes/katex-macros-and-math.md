# KaTeX Mathematical Notation & Macro Architecture in StackEdit++

> **Platform**: [StackEdit++](https://stackeditplusplus.meshworld.in) • [Live App](https://stackeditplusplus.meshworld.in/app)  
> **Engine**: KaTeX (Fast, client-side LaTeX typesetting)

---

## Overview

StackEdit++ ships with native, high-performance in-browser math rendering powered by **KaTeX**. Unlike cloud-rendered MathJax engines that query remote fonts and delay rendering, KaTeX executes synchronously in browser RAM, rendering complex formulas and matrices instantly as you type.

---

## 1. Basic Math Delimiters

### Inline Math (`$ ... $`)
Use single dollar signs for formulas embedded inside running text:

```markdown
Euler's identity, $e^{i\pi} + 1 = 0$, connects five fundamental constants.
```

**Preview:**  
Euler's identity, $e^{i\pi} + 1 = 0$, connects five fundamental constants.

### Display / Block Math (`$$ ... $$`)
Use double dollar signs on dedicated lines for centered, prominent equations:

```markdown
$$
\int_{-\infty}^{\infty} e^{-x^2} \, dx = \sqrt{\pi}
$$
```

---

## 2. Advanced Environments

### Matrices and Vectors
KaTeX supports standard LaTeX matrix environments (`matrix`, `pmatrix`, `bmatrix`, `vmatrix`):

```markdown
$$
\mathbf{R}(\theta) = \begin{bmatrix}
\cos\theta & -\sin\theta \\
\sin\theta & \cos\theta
\end{bmatrix}
$$
```

### Piecewise Functions (`cases`)
```markdown
$$
f(x) = \begin{cases}
x^2 & \text{if } x \ge 0 \\
-x  & \text{if } x < 0
\end{cases}
$$
```

### Multi-Line Equations (`aligned`)
```markdown
$$
\begin{aligned}
\nabla \cdot \mathbf{E} &= \frac{\rho}{\varepsilon_0} \\
\nabla \cdot \mathbf{B} &= 0 \\
\nabla \times \mathbf{E} &= -\frac{\partial \mathbf{B}}{\partial t} \\
\nabla \times \mathbf{B} &= \mu_0 \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t}
\end{aligned}
$$
```

---

## 3. Custom Macros for Engineering & Research

You can define custom shorthand macros directly in your markdown documents to avoid repetitive LaTeX boilerplate:

```markdown
$$
\gdef\R{\mathbb{R}}
\gdef\norm#1{\left\|#1\right\|}
\gdef\inner#1#2{\left\langle #1, #2 \right\rangle}
$$

Let $x, y \in \R^n$. The Cauchy-Schwarz inequality states:

$$
|\inner{x}{y}| \le \norm{x} \norm{y}
$$
```

---

## 4. Performance & Formatting Best Practices

1. **Avoid Empty Lines inside `$$ ... $$` Blocks**: KaTeX blocks must not contain blank lines, as Markdown AST parsers treat blank lines as paragraph breaks.
2. **Use `\text{...}` for Natural Language**: Inside math mode, always wrap plain words in `\text{...}` to preserve standard font kerning and spacing.
3. **Escaping Underscores**: Outside math mode, underscores can trigger italics. When writing technical variable names with underscores, always wrap them in inline code (`` `my_var` ``) or math mode (`$my\_var$`).
