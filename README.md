Mathematical Programs & Visualizations
A collection of Python-based mathematical programs exploring number theory, calculus, function visualization, fractals, and more.
Overview

This project is a collection of mathematical programs that I originally developed during Grade 10 and eventually compiled into a single application with a graphical menu.

The project was initially created for my school's IT Exhibition (2081 B.S.). What started as a relatively simple programming project gradually turned into an opportunity to explore several mathematical concepts that I found interesting and implement them computationally.

The main objective was to combine mathematics with programming, particularly by creating visual representations of concepts that are otherwise somewhat difficult to appreciate through equations alone.

The project uses Python as its primary programming language, taking advantage of libraries such as NumPy, Matplotlib, and SymPy for numerical computation, symbolic mathematics, and graphical visualization.

Rather than focusing on one particular mathematical topic, the project contains several independent programs:

Mandelbrot Set Rendering
Number Theory Programs
A Graphing Calculator
Taylor and Maclaurin Series Approximation
A Typing Speed Test

All of these programs are accessible through a single graphical interface built using Tkinter.

The Programs
1. Mandelbrot Set Renderer

One of the more interesting components of this project is the Mandelbrot Set Renderer.

The Mandelbrot Set is a famous mathematical fractal that is generated through repeated iteration of a relatively simple equation involving complex numbers.

The fundamental equation is:

𝑧
𝑛
+
1
=
𝑧
𝑛
2
+
𝑐

where:

𝑧
𝑛
 is the current complex number.
𝑐
 is a constant complex number.
𝑧
0
=
0
 is the initial value.

For every point 
𝑐
 in the complex plane, the program repeatedly evaluates this equation and determines whether the resulting sequence diverges.

How It Works

The program generates a grid of complex numbers, with the real and imaginary components representing the horizontal and vertical axes.

For each complex number, the iteration is performed until one of two conditions is satisfied:

The magnitude of 
𝑧
 exceeds a specified escape threshold.
The maximum number of iterations is reached.

The magnitude is calculated using:

∣
𝑧
∣
=
𝑎
2
+
𝑏
2

where 
𝑧
=
𝑎
+
𝑏
𝑖
.

If the magnitude exceeds 2, the sequence is considered to have escaped. Otherwise, the point is treated as belonging to the Mandelbrot Set within the chosen iteration limit.

The number of iterations required for a point to escape determines its colour.

Points that do not escape within the iteration limit are displayed separately, producing the characteristic fractal structure.

Customization

The renderer allows the user to specify:

Number of pixels along the real axis.
Number of pixels along the imaginary axis.
Power of 
𝑧
 in the iteration equation.
Maximum number of iterations.
Matplotlib colour map.

The power of 
𝑧
 can also be modified to experiment with different fractal patterns beyond the conventional Mandelbrot Set.

The implementation can be found in fractalRender.py.

2. Number Theory Programs

The number theory module contains two programs that explore interesting properties of integers and prime numbers.

Both programs rely on relatively straightforward algorithms, but they demonstrate how mathematical definitions can be translated into computational procedures.

Perfect Number Searcher

A perfect number is a positive integer that is equal to the sum of all its proper positive divisors.

For example:

6
=
1
+
2
+
3

Therefore, 6 is a perfect number.

Similarly:

28
=
1
+
2
+
4
+
7
+
14

The first few perfect numbers are:

6
,
 
28
,
 
496
,
 
8128
,
…

The program searches for perfect numbers below a user-defined upper limit.

For every integer 
𝑛
, it calculates the sum of its proper divisors:

𝑆
(
𝑛
)
=
∑
𝑑
∣
𝑛


𝑑
<
𝑛
𝑑

If:

𝑆
(
𝑛
)
=
𝑛

then the number is identified as a perfect number.

An optimization used in the implementation is that no proper divisor of an integer can be greater than half of that integer.

Consequently, there is no need to iterate through every possible integer up to 
𝑛
.

Mersenne Prime Searcher

A Mersenne Prime is a prime number that can be expressed in the form:

𝑀
𝑝
=
2
𝑝
−
1

where 
𝑝
 is itself a prime number.

Some examples include:

2
2
−
1
=
3
2
3
−
1
=
7
2
5
−
1
=
31

The program searches through prime exponents and generates the corresponding Mersenne numbers.

It then attempts to determine whether the generated numbers are prime.

The primality-checking function uses trial division up to the square root of the number rather than checking every possible divisor.

This is based on the observation that if an integer has a factor greater than its square root, it must also have a corresponding factor smaller than its square root.

The implementation can be found in numberTheory.py.

3. Graphing Calculator

The Graphing Calculator was inspired by Desmos and was created to provide a simple way of visualizing different mathematical functions.

It uses a combination of SymPy, NumPy, and Matplotlib to generate graphs from user-provided coefficients and selected mathematical functions.

The calculator contains six primary options.

Trigonometric Functions

The calculator can plot the following functions:

Standard trigonometric functions:

sin
⁡
(
𝑥
)
,
cos
⁡
(
𝑥
)
,
tan
⁡
(
𝑥
)

Hyperbolic functions:

sinh
⁡
(
𝑥
)
,
cosh
⁡
(
𝑥
)
,
tanh
⁡
(
𝑥
)

The hyperbolic functions are evaluated numerically using Python's mathematical functions and NumPy-generated coordinates, while the standard trigonometric functions are plotted using SymPy.

Linear Functions

The calculator allows the user to enter the coefficients of a linear equation in the form:

𝑦
=
𝑎
𝑥
+
𝑏

The coefficients 
𝑎
 and 
𝑏
 are obtained through user input and used to construct the corresponding symbolic expression.

Quadratic Functions

Quadratic functions are represented in the standard form:

𝑦
=
𝑎
𝑥
2
+
𝑏
𝑥
+
𝑐

The user provides the three coefficients, and SymPy generates the corresponding parabola.

Cubic Functions

Similarly, the calculator supports cubic functions of the form:

𝑦
=
𝑎
𝑥
3
+
𝑏
𝑥
2
+
𝑐
𝑥
+
𝑑

The four coefficients are entered individually before the graph is generated.

Logarithmic Functions

The logarithmic section provides two options:

Natural logarithm:
𝑦
=
ln
⁡
(
𝑥
)
Logarithm with a user-defined base:
𝑦
=
log
⁡
𝑎
(
𝑥
)

The user can specify the logarithmic base, and SymPy handles the symbolic representation and plotting.

Three-Dimensional Plotting

The calculator also includes a basic 3D plotting component.

It provides five predefined options:

𝑧
=
𝑥
𝑦
𝑧
=
𝑥
/
𝑦
Parametric 3D curves.
A parametric 3D surface.
𝑧
=
𝑥
2
+
𝑦
2

The implementation uses SymPy's 3D plotting functionality, including plot3d, plot3d_parametric_line, and plot3d_parametric_surface.

Unlike the other sections, the 3D plotting component uses predefined functions rather than accepting arbitrary user-defined equations.

The implementation can be found in graphingCalculator.py.

4. Taylor and Maclaurin Series Approximation

This component explores one of the fundamental ideas in calculus: approximating functions using infinite polynomial expansions.

A Taylor Series represents a sufficiently differentiable function as an infinite sum of terms involving its derivatives at a particular point.

The general Taylor Series expansion around 
𝑥
=
𝑎
 is:

𝑓
(
𝑥
)
=
∑
𝑛
=
0
∞
𝑓
(
𝑛
)
(
𝑎
)
𝑛
!
(
𝑥
−
𝑎
)
𝑛

A Maclaurin Series is simply a special case of the Taylor Series where:

𝑎
=
0

The program focuses on three functions:

Sine
Cosine
Exponential
Sine Function

The Maclaurin expansion of the sine function is:

sin
⁡
(
𝑥
)
=
𝑥
−
𝑥
3
3
!
+
𝑥
5
5
!
−
𝑥
7
7
!
+
⋯

The program approximates this function by calculating successive terms of the expansion.

Cosine Function

The Maclaurin expansion of cosine is:

cos
⁡
(
𝑥
)
=
1
−
𝑥
2
2
!
+
𝑥
4
4
!
−
𝑥
6
6
!
+
⋯

Similar to the sine function, additional terms generally improve the approximation over a suitable interval.

Exponential Function

The exponential function has the expansion:

𝑒
𝑥
=
1
+
𝑥
+
𝑥
2
2
!
+
𝑥
3
3
!
+
⋯

Unlike the sine and cosine expansions, all the terms in this series are positive powers of 
𝑥
 with positive coefficients.

Visualization

The program allows the user to select one of the three functions and specify the number of iterations.

It then generates a graph containing:

The original mathematical function.
Successive polynomial approximations.
A legend identifying the number of terms used in each approximation.

The graphs are generated using Matplotlib, while NumPy is used to create the array of coordinates over which the functions are evaluated.

This makes it possible to observe how the polynomial approximations behave as additional terms are introduced.

The implementation can be found in taylorSeries.py.

5. Typing Speed Test

The final component is slightly different from the other programs, as it is not directly related to mathematics.

Inspired by Monkeytype, this program provides a simple typing-speed test.

The program contains a collection of approximately 70 common words and randomly selects words to generate a typing passage.

There are three available test lengths:

10 words
30 words
50 words

After selecting a test length, the program displays the randomly generated words and begins a countdown.

Once the countdown finishes, the user types the displayed passage.

The program measures the time taken to enter the response and calculates an estimated Words Per Minute (WPM) value.

The basic calculation is:

𝑊
𝑃
𝑀
=
Number of Words
Time in Minutes

The current implementation uses the following calculation:

𝑊
𝑃
𝑀
=
𝑁
×
60
𝑡

where:

𝑁
 is the number of words displayed.
𝑡
 is the time taken in seconds.

Limitations: This is a very basic implementation. It does not check typing accuracy, compare the entered text against the original passage, or account for incorrectly typed words. Consequently, the reported WPM should be treated as an estimate rather than an accurate typing-speed measurement.

The implementation can be found in typingTest.py.

Project Structure

The project is organized into separate Python modules, with each module responsible for a particular application.

text
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

File Descriptions
File	Purpose
mainProgram.py	Main graphical interface that connects all the programs
fractalRender.py	Generates Mandelbrot-style fractal visualizations
numberTheory.py	Contains perfect number and Mersenne prime searches
graphingCalculator.py	Implements the mathematical graphing calculator
taylorSeries.py	Computes and visualizes Maclaurin series approximations
typingTest.py	Implements the typing-speed test
Extra/	Contains additional supporting project files
README.md	Project documentation
Main Application

The main application is responsible for bringing all the individual programs together.

It is implemented using Python's Tkinter library, which provides the graphical interface.

Instead of requiring the user to execute each Python file separately, the main program creates a window containing five buttons.

Each button is connected to the corresponding function imported from its respective module.

The main interface provides the following options:

Mandelbrot Render
Number Theory Programs
Graph Your Equations!
Approximate Function!
See How Fast You Can Type!

Selecting a button invokes the corresponding Python function.

An important detail is that most of the individual applications still rely on console input. Consequently, the user may need to interact with the terminal after selecting an option from the graphical interface.

The main application uses Tkinter's mainloop() to keep the graphical window running.

The implementation can be found in mainProgram.py.

Technologies Used
Python

Python was chosen primarily for its readability and its extensive ecosystem of libraries for mathematical computation and visualization.

It also made it relatively straightforward to separate the different applications into independent modules.

NumPy

NumPy is used for numerical computation and generating arrays of coordinates.

It is particularly useful in the fractal renderer, where a large number of complex coordinates must be evaluated, and in the Taylor Series visualizations.

Matplotlib

Matplotlib is responsible for generating most of the project's two-dimensional visualizations.

It is used for:

Mandelbrot Set rendering.
Hyperbolic function plotting.
Taylor and Maclaurin Series visualization.
Displaying numerical results graphically.
SymPy

SymPy provides symbolic mathematical functionality.

It is primarily used in the graphing calculator to construct and plot mathematical expressions, including polynomial, trigonometric, logarithmic, and three-dimensional functions.

Tkinter

Tkinter provides the graphical interface for the main application.

It allows the different programs to be accessed through a single window instead of requiring the user to execute individual modules manually.

Standard Python Libraries

The project also makes use of several built-in Python modules:

math for mathematical operations.
time for delays and measuring elapsed time.
random for generating randomized typing passages.
sys for program termination.
Installation

Clone the repository:

bash
git clone https://github.com/GodChungus/Math-Programs.git
cd Math-Programs


Install the required Python libraries:

bash
pip install numpy matplotlib sympy


Tkinter is included with many standard Python installations. On some Linux distributions, it may need to be installed separately.

Make sure the supporting files in the Extra directory are available to the main application.

Running the Project

The main entry point of the application is:

bash
python mainProgram.py


This launches the graphical interface.

From there, you can select whichever mathematical program you would like to use.

Note: The graphical interface acts primarily as a launcher. Most of the individual programs use console-based input, so keep the terminal open while interacting with them.

Limitations & Possible Improvements

This project was originally developed as an educational exhibition project. Although it contains several interesting mathematical applications, there are plenty of areas that could be improved.

Improved User Interface

The current implementation uses Tkinter for the main menu, but most of the actual programs still depend on console input.

A possible improvement would be to integrate all the individual applications into a proper graphical interface.

This would make the overall experience more consistent and eliminate the need to switch between the graphical window and terminal.

More Efficient Fractal Rendering

The Mandelbrot renderer currently evaluates each complex coordinate individually using nested loops.

A possible improvement would be to use NumPy vectorization to perform multiple complex-number calculations simultaneously.

This could significantly improve rendering performance, particularly at higher resolutions and iteration counts.

Improved Number Theory Algorithms

The number theory module currently relies on relatively simple trial-division techniques.

There are several opportunities for improvement:

Implementing the Sieve of Eratosthenes.
Using more efficient primality-testing algorithms.
Implementing specialized tests for Mersenne primes.
Improving the performance of perfect number searches.

The current primality-checking implementation would also benefit from additional testing and correction before being used for larger searches.

More Flexible Graphing Calculator

The graphing calculator currently supports a limited collection of predefined mathematical functions.

It could be extended to accept arbitrary mathematical expressions from the user.

Additional features could include:

Customizable plotting intervals.
Better graph formatting.
Interactive zooming and panning.
Implicit function plotting.
Parametric equations.
More advanced 3D plotting.
Taylor Series Error Analysis

The Taylor Series visualizations currently focus on comparing the approximations with their corresponding original functions.

A useful extension would be to calculate and visualize the approximation error.

For example:

𝐸
𝑛
(
𝑥
)
=
∣
𝑓
(
𝑥
)
−
𝑇
𝑛
(
𝑥
)
∣

where:

𝑓
(
𝑥
)
 is the original function.
𝑇
𝑛
(
𝑥
)
 is the polynomial approximation of degree 
𝑛
.

This would provide a more quantitative way of understanding convergence and approximation accuracy.

Improved Typing Speed Test

The typing test is currently a relatively simple experiment.

It could be expanded to include:

Accuracy calculations.
Character-level error detection.
More extensive word databases.
Customizable test durations.
A proper graphical interface.
More accurate WPM calculations.
Background

This project was initially developed when I was in Grade 10, for my school's IT Exhibition held in 2081 B.S.

What began as an attempt to create a collection of interesting Python programs gradually turned into a much larger exploration of mathematics and programming.

While developing the different components, I got the opportunity to experiment with concepts from number theory, calculus, complex analysis, and mathematical visualization.

I also learned quite a bit about structuring larger Python projects, using external libraries, and translating mathematical definitions into algorithms.

The project is not necessarily intended to be a collection of perfectly optimized algorithms. Rather, it serves as a record of my early experimentation with computational mathematics and the things I learned along the way.

There is also quite a bit of documentation within the individual Python files themselves, so anyone interested in understanding the actual implementations can refer to the source code.

</>
