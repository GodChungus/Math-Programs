# Mathematical Programs & Visualizations

### A collection of Python-based mathematical programs exploring number theory, calculus, function visualization, fractals, and more.

---

## Overview

This project is a collection of mathematical programs that I originally developed during Grade 10 and eventually compiled into a single application with a graphical menu.

The project was initially created for my school's IT Exhibition (2081 B.S.). What started as a relatively simple programming project gradually turned into an opportunity to explore several mathematical concepts that I found interesting and implement them computationally.

The main objective was to combine mathematics with programming, particularly by creating visual representations of concepts that are otherwise somewhat difficult to appreciate through equations alone.

The project uses Python as its primary programming language, taking advantage of libraries such as NumPy, Matplotlib, and SymPy for numerical computation, symbolic mathematics, and graphical visualization.

The project contains five independent programs:

- Mandelbrot Set Renderer
- Number Theory Programs
- Graphing Calculator
- Taylor and Maclaurin Series Approximation
- Typing Speed Test

All of these programs are accessible through a single graphical interface built using Tkinter.

---

## The Programs

## 1. Mandelbrot Set Renderer

One of the more interesting components of this project is the Mandelbrot Set Renderer.

The Mandelbrot Set is a famous mathematical fractal that is generated through repeated iteration of a relatively simple equation involving complex numbers.

The fundamental equation is:

$$
z_{n+1}=z_n^2+c
$$

where:

- $z_n$ is the current complex number.
- $c$ is a constant complex number.
- $z_0=0$ is the initial value.

For every point $c$ in the complex plane, the program repeatedly evaluates this equation and determines whether the resulting sequence diverges.

### How It Works

The program generates a grid of complex numbers, with the real and imaginary components representing the horizontal and vertical axes.

For each complex number, the iteration is performed until one of two conditions is satisfied:

1. The magnitude of $z$ exceeds a specified escape threshold.
2. The maximum number of iterations is reached.

The magnitude is calculated using:

$$
|z|=\sqrt{a^2+b^2}
$$

where $z=a+bi$.

If the magnitude exceeds 2, the sequence is considered to have escaped. Otherwise, the point is treated as belonging to the Mandelbrot Set within the chosen iteration limit.

The number of iterations required for a point to escape determines its colour.

Points that do not escape within the iteration limit are displayed separately, producing the characteristic fractal structure.

### Customization

The renderer allows the user to specify:

- Number of pixels along the real axis.
- Number of pixels along the imaginary axis.
- Power of $z$ in the iteration equation.
- Maximum number of iterations.
- Matplotlib colour map.

The power of $z$ can also be modified to experiment with different fractal patterns beyond the conventional Mandelbrot Set.

The implementation can be found in `fractalRender.py`.

---

## 2. Number Theory Programs

The number theory module contains two programs that explore interesting properties of integers and prime numbers.

Both programs rely on relatively straightforward algorithms, but they demonstrate how mathematical definitions can be translated into computational procedures.

### Perfect Number Searcher

A perfect number is a positive integer that is equal to the sum of all its proper positive divisors.

For example:

$$
6=1+2+3
$$

Therefore, 6 is a perfect number.

Similarly:

$$
28=1+2+4+7+14
$$

The first few perfect numbers are:

$$
6,\ 28,\ 496,\ 8128,\ldots
$$

The program searches for perfect numbers below a user-defined upper limit.

For every integer $n$, it calculates the sum of its proper divisors:

$$
S(n)=\sum_{d \mid n, d<n}d
$$

If:

$$
S(n)=n
$$

then the number is identified as a perfect number.

An optimization used in the implementation is that no proper divisor of an integer can be greater than half of that integer.

Consequently, there is no need to iterate through every possible integer up to $n$.

### Mersenne Prime Searcher

A Mersenne Prime is a prime number that can be expressed in the form:

$$
M_p=2^p-1
$$

where $p$ is itself a prime number.

Some examples include:

$$
2^2-1=3
$$

$$
2^3-1=7
$$

$$
2^5-1=31
$$

The program searches through prime exponents and generates the corresponding Mersenne numbers.

It then attempts to determine whether the generated numbers are prime.

The primality-checking function uses trial division up to the square root of the number rather than checking every possible divisor.

This is based on the observation that if an integer has a factor greater than its square root, it must also have a corresponding factor smaller than its square root.

The implementation can be found in `numberTheory.py`.

---

## 3. Graphing Calculator

The Graphing Calculator was inspired by Desmos and was created to provide a simple way of visualizing different mathematical functions.

It uses a combination of SymPy, NumPy, and Matplotlib to generate graphs from user-provided coefficients and selected mathematical functions.

The calculator contains six primary options.

### Trigonometric Functions

The calculator can plot the following functions:

**Standard trigonometric functions:**

$$
\sin(x),\quad\cos(x),\quad\tan(x)
$$

**Hyperbolic functions:**

$$
\sinh(x),\quad\cosh(x),\quad\tanh(x)
$$

The hyperbolic functions are evaluated numerically using Python's mathematical functions and NumPy-generated coordinates, while the standard trigonometric functions are plotted using SymPy.

### Linear Functions

The calculator allows the user to enter the coefficients of a linear equation in the form:

$$
y=ax+b
$$

The coefficients $a$ and $b$ are obtained through user input and used to construct the corresponding symbolic expression.

### Quadratic Functions

Quadratic functions are represented in the standard form:

$$
y=ax^2+bx+c
$$

The user provides the three coefficients, and SymPy generates the corresponding parabola.

### Cubic Functions

Similarly, the calculator supports cubic functions of the form:

$$
y=ax^3+bx^2+cx+d
$$

The four coefficients are entered individually before the graph is generated.

### Logarithmic Functions

The logarithmic section provides two options:

1. Natural logarithm:

$$
y=\ln(x)
$$

2. Logarithm with a user-defined base:

$$
y=\log_a(x)
$$

The user can specify the logarithmic base, and SymPy handles the symbolic representation and plotting.

### Three-Dimensional Plotting

The calculator also includes a basic 3D plotting component.

It provides five predefined options:

- $z=xy$
- $z=x/y$
- Parametric 3D curves.
- A parametric 3D surface.
- $z=x^2+y^2$

The implementation uses SymPy's 3D plotting functionality, including `plot3d`, `plot3d_parametric_line`, and `plot3d_parametric_surface`.

Unlike the other sections, the 3D plotting component uses predefined functions rather than accepting arbitrary user-defined equations.

The implementation can be found in `graphingCalculator.py`.

---

## 4. Taylor and Maclaurin Series Approximation

This component explores one of the fundamental ideas in calculus: approximating functions using infinite polynomial expansions.

A Taylor Series represents a sufficiently differentiable function as an infinite sum of terms involving its derivatives at a particular point.

The general Taylor Series expansion around $x=a$ is:

$$
f(x)=\sum_{n=0}^{\infty}\frac{f^{(n)}(a)}{n!}(x-a)^n
$$

A Maclaurin Series is simply a special case of the Taylor Series where:

$$
a=0
$$

The program focuses on three functions:

- Sine
- Cosine
- Exponential

### Sine Function

The Maclaurin expansion of the sine function is:

$$
\sin(x)=x-\frac{x^3}{3!}+\frac{x^5}{5!}-\frac{x^7}{7!}+\cdots
$$

The program approximates this function by calculating successive terms of the expansion.

### Cosine Function

The Maclaurin expansion of cosine is:

$$
\cos(x)=1-\frac{x^2}{2!}+\frac{x^4}{4!}-\frac{x^6}{6!}+\cdots
$$

Similar to the sine function, additional terms generally improve the approximation over a suitable interval.

### Exponential Function

The exponential function has the expansion:

$$
e^x=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots
$$

Unlike the sine and cosine expansions, all the terms in this series have positive coefficients.

### Visualization

The program allows the user to select one of the three functions and specify the number of iterations.

It then generates a graph containing:

- The original mathematical function.
- Successive polynomial approximations.
- A legend identifying the number of terms used in each approximation.

The graphs are generated using Matplotlib, while NumPy is used to create the array of coordinates over which the functions are evaluated.

This makes it possible to observe how the polynomial approximations behave as additional terms are introduced.

The implementation can be found in `taylorSeries.py`.

---

## 5. Typing Speed Test

The final component is slightly different from the other programs, as it is not directly related to mathematics.

Inspired by Monkeytype, this program provides a simple typing-speed test.

The program contains a collection of approximately 70 common words and randomly selects words to generate a typing passage.

There are three available test lengths:

- 10 words
- 30 words
- 50 words

After selecting a test length, the program displays the randomly generated words and begins a countdown.

Once the countdown finishes, the user types the displayed passage.

The program measures the time taken to enter the response and calculates an estimated Words Per Minute (WPM) value.

The basic calculation is:

$$
WPM=\frac{\text{Number of Words}}{\text{Time in Minutes}}
$$

The current implementation uses the following calculation:

$$
WPM=\frac{N\times60}{t}
$$

where:

- $N$ is the number of words displayed.
- $t$ is the time taken in seconds.

**Limitations:** This is a very basic implementation. It does not check typing accuracy, compare the entered text against the original passage, or account for incorrectly typed words. Consequently, the reported WPM should be treated as an estimate rather than an accurate typing-speed measurement.

The implementation can be found in `typingTest.py`.

---

## Project Structure

The project is organized into separate Python modules, with each module responsible for a particular application.

```text
Math-Programs/
│
├── mainProgram.py
│
├── fractalRender.py
├── numberTheory.py
├── graphingCalculator.py
├── taylorSeries.py
├── typingTest.py
│
├── Extra/
│
└── README.md
