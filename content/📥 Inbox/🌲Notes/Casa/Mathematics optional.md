- [ ] # Booklist
Prakash purohit blog
## Paper – I

1.  **Calculus** – Shanti Narayan – Course on Mathematical Analysis (S. Chand)
2.  **Analytic Geometry** – Shanti Narayan (S. Chand)
3.  **Ordinary Differential Equations** – M.D. Raisinghania (S. Chand)
4.  **Statics** – Krishna Series
5.  **Dynamics** – Krishna Series

## Paper – II

1.  **Algebra** – (a) Khanna and Bhambri (b) I. N. Herstein
2.  **Real Analysis** – MD. Raisinghania – Elements of Real Analysis (S. Chand)
3.  **Complex Analysis** – Krishna Series
4.  **Linear Programming** –  Krishna Series
5.  **Partial Differential Equations**– M.D. Raisinghania + (Some portion of book on Boundary Value Problem by S. Chand)
6.  **Numerical Analysis** – Jain and Iynger
7.  **Fluid Dynamics** – M.D. Raisinghania
8.  **Mechanics** – Krishna Series (Rigid Dynamics vol.-1 and Vo.-II)
# Functions of several variables
### Introduction
Most measurable quantities in the real world do not depend on one single factor but on many factors. This indicates that functions of several variables are natural entities in the world of mathematics. 
So far, we have studied the concepts of limits, continuity, differentiability, etc for functions fo a single variable. Now, we introduce the concept of limit, continuity and differentiability of functions of several variables. Mainly, we study these concepts for real valued functions of 2 variables which can be generalised to functions of several variables. 
### [[Euclidean space]]
For a fixed $n \in N$, let $\mathbb{R}^n$ be the set of all ordered n-tuples $n \in (x_1, x_2, .... , x_n)$ where $x_1, x_2,...x_n \in \mathbb{R}$ are called the coordinates of $x$. 
$\rightarrow$ The elements fo $\mathbb{R}^n$ are called points of vectors and are denoted by $x,y,z$ etc. 
* we define the addition of vectors and multiplication of a vector by real numbers(called scalars) as follows
	* Let $x=(x_1,x_2,...,x_n)\in \mathbb{R}^n$ , $y=(y_1,y_2,...,y_n)\in \mathbb{R}^n$ and $\alpha \in \mathbb{R}$
	* Then $x+y=(x_1+y_1,x_2+y_2,...,x_n+y_n)\in \mathbb{R}^n$ and $\alpha x=(\alpha x_1,\alpha x_2,...,\alpha x_n) \in \mathbb{R}^n )$ 
	* These 2 operations make $\mathbb{R}^n$ a vector space over the real field $\mathbb{R}^n$ 
* The zero elements of $\mathbb{R}^n$ {sometimes called the origin or null vector} is the point $\mathbb{O} =(0,0,...,0)$ 
* We define the scalar/inner product of 2 vectors x and y by $x.y=\Sigma_{i=1}^nx_iy_i=x_1y_1+x_2y_2+...+x_ny_n$ and the norm of $x$ by $\|x\|=(x.x)^{1/2}=(\Sigma_{i=1}^nx_i²)^{1/2}$ 
* The vector space $\mathbb{R^n}$ with the above inner product and norm is called n-dimentional Euclidean space.
	* in particular, we get $\mathbb{R},\mathbb{R}^2,\mathbb{R}^3$ for n=1,2,3 respectively and we write $x=(x_1,x_2)$ if $x\in \mathbb{R}^2$ and $x=(x_1,x_2,x_3) \forall x \in \mathbb{R}^3$         

### Functions of several variables: 
* Let $f:X\rightarrow\mathbb{R}$. If $X\subset\mathbb{R}^n$ the f is called a function of $'n'$ variables.
	* f is a function of several variables if $n>1$ 
	* $f:X\rightarrow\mathbb{R}$ is a function of 2 variables if $X\subset\mathbb{R}^2$. 
	* $f:X\rightarrow\mathbb{R}$ is a function of 3 variables if $X\subset\mathbb{R}^3$.

### Neighborhood of a point: 
#### Spherical neighborhood of a point:
Let $\mathbb{R}^n$ be the **Euclidean space** and $a\in\mathbb{R}^n$ (i.e. $a=(a_1,a_2,...,a_n)$). If $\delta$ is any positive real number, then the set $\{x\in \mathbb{R}^n/\|x-a\|<\delta\}$ is called an open sphere.
	Since $$\|x-a\|<\delta\implies\left[\Sigma_{i=1}^n(x_i-a_i)^2\right]^{\frac{1}{2}}<\delta
	\implies\Sigma_{i=1}^n(x_i-a_i)²<{\delta}^2\implies(x_1-a_1)^2+(x_2-a_2)^2+...+(x_n-a_n)^2<\delta$$
The point $'a'$ is called the center and $'\delta'$ the radius of the sphere. This open sphere is denoted by $S(a,\delta)$. A closed sphere is denoted by $S[a,\delta]$ and is defined by $S[a,\delta]=\{x\in\mathbb{R}^n/\|x-a\|\le\delta\}$. Any open sphere with $'a'$ as its centre is called a spherical neighborhood of the point $'a'$. 
The open sphere with the center $a=(a_1,a_2)\in \mathbb{R}^2$ and radius $\delta$ is $S(a,\delta)=\{(x_1,x_2)\in\mathbb{R}^2/(x_1-a_1)^2+(x_2-a_2)²<\delta^2\}$ 
	This S is represented in a diagram below. 
$\therefore$ The open sphere in this case consists of all points of the cartesian plane which lie within the circle $(x_1-a_1)^2+(x_2-a_2)^2=\delta^2$

[![](https://i.imgur.com/2U1M8ZBt.png)](https://i.imgur.com/2U1M8ZB.png)
[[Drawing 2022-07-07 23.48.34.excalidraw]]

#### Rectangular Neighborhood of a point
Rectangular neighborhood of a point $a=(a_1,a_2,...,a_n)\in \mathbb{R}^n$ is defined to be the set $\{x\in\mathbb{R}^2/|x_i-a_i|<\delta_i\} \ i=1,2,...n$. 
The rectangular neighborhood of $(a_1,a_2)$ is $\{(x_1,x_2)\in\mathbb{R}²/|x_1-a_1|<\delta_1\ and\ |x_2-a_2|<\delta_2\}$.
If in particular $\delta_1=\delta_2=\delta$, then such a neighborhood is referred to as a square neighborhood of side $2\delta$.
![](https://i.imgur.com/dLRzG9g.png)
$\{(x_1,x_2)\in\mathbb{R}²/|x_1-a_1|<\delta_1\ ,\ |x_2-a_2|<\delta_2\}$

Note: Every sperical neighborhood R^n

#### **$\delta$** neighborhood of a point
Let $a=(a_1,a_2,...,a_n)\in\mathbb{R}^n$ adn $'\delta'$ be a +ve real number. The set of points $x=(x_1,x_2,...,x_n)\in\mathbb{R}^n$ where $a_r-\delta<x_0<a_r+\delta$ i.e $|x_r-a_r|<\delta\ ;\ r=1,2,...,n$ is called a $\delta$-neighborhood of the point 'a' and is denoted by $N(a,\delta)$. If we exclude the point 'a' from $N(a,\delta)$ then it is called a deleted neighborhood of 'a' is denoted by $N'(a,\delta)$ 

### Limit of a function
Let $f:x\rightarrow\mathbb{R},x\subset\mathbb{R}^n$. Then $f$ is said to tend to limit $l\in\mathbb{R}$ as 'x' approaches 'a' , i.e. $\lim_{x\to a} f(x)=l$  


# PYQ
[2021 paper 1](https://www.upsc.gov.in/sites/default/files/Mathematics%20Paper-I.pdf) 
[2021 paper 2](https://www.upsc.gov.in/sites/default/files/Mathematics%20Paper-II.pdf)

# Syllabus

- Linear Algebra
	- Vector spaces over R and C, linear dependence and independence, ==subspaces, bases, dimensions, Linear transformations, rank and nullity, matrix of a linear transformation==. Algebra of Matrices; Row and column reduction, Echelon form, congruence’s and similarity; Rankof a matrix; Inverse of a matrix; Solution of system of linear equations; Eigenvalues and eigenvectors, characteristic polynomial, Cayley-Hamilton theorem, Symmetric, skew-symmetric, Hermitian, skewHermitian, orthogonal and unitary matrices and their eigenvalues. 
- Calculus : 
	- Real numbers, functions of a real variable, limits, continuity, differentiability, mean-value theorem, ==Taylor’s theorem with remainders==, indeterminate forms, maxima and minima, asymptotes; ==Curve tracing==; Functions of two or three variables; Limits, continuity, partial derivatives, maxima and minima, Lagrange’s method of multipliers, Jacobian. ==Riemann’s definition of definite integrals==; Indefinite integrals; Infinite and ==improper integral==; Double and triple integrals (evaluation techniques only); Areas, surface and volumes. 
- Analytic Geometry 
	- Cartesian and polar coordinates in three dimensions, second degree equations in three variables, reduction to Canonical forms; straight lines, shortest distance between two skew lines, Plane, sphere, cone, cylinder, paraboloid, ellipsoid, hyperboloid of one and two sheets and their properties. 
- Ordinary Differential Equations 
	- Formulation of differential equations; Equations of first order and first degree, integrating factor; Orthogonal trajectory; Equations of first order but not of first degree, Clairaut’s equation, singular solution. Second and higher order liner equations with constant coefficients, complementary function, particular integral and general solution. Section order linear equations with variable coefficients, Euler-Cauchy equation; Determination of complete solution when one solution is known using method of variation of parameters. Laplace and Inverse Laplace transforms and their properties, Laplace transforms of elementary functions. Application to initial value problems for 2nd order linear equations with constant coefficients.
- Dynamics and Statics : 
	- Rectilinear motion, simple harmonic motion, motion in a plane, projectiles; Constrained motion; Work and energy, conservation of energy; Kepler’s laws, orbits under central forces. Equilibrium of a system of particles; Work and potential energy, friction, Common catenary; Principle of virtual work; Stability of equilibrium, equilibrium of forces in three dimensions. 
- Vector Analysis : 
	- Scalar and vector fields, differentiation of vector field of a scalar variable; Gradient, divergence and curl in cartesian and cylindrical coordinates; Higher order derivatives; Vector identities and vector equation. Application to geometry : Curves in space, curvature and torsion; Serret-Furenet's formulae. Gauss and Stokes’ theorems, Green's indentities.
- Algebra : 
	- Groups, subgroups, cyclic groups, cosets, Lagrange’s Theorem, normal subgroups, quotient groups, homomorphism of groups, basic isomorphism theorems, permutation groups, Cayley’s theorem. Rings, subrings and ideals, homomorphisms of rings; Integral domains, principal ideal domains, Euclidean domains and unique factorization domains; Fields, quotient fields. 
- Real Analysis : 
	- Real number system as an ordered field with least upper bound property; Sequences, limit of a sequence, Cauchy sequence, completeness of real line; Series and its convergence, absolute and conditional convergence of series of real and complex terms, rearrangement of series. Continuity and uniform continuity of functions, properties of continuous functions on compact sets. Riemann integral, improper integrals; Fundamental theorems of integral calculus. Uniform convergence, continuity, differentiability and integrability for sequences and series of functions; Partial derivatives of functions of several (two or three) variables, maxima and minima. 
- Complex Analysis : 
	- Analytic function, Cauchy-Riemann equations, Cauchy's theorem, Cauchy's integral formula, power series, representation of an analytic function, Taylor’s series; Singularities; Laurent’s series; Cauchy’s residue theorem; Contour integration. 
- Linear Programming : 
	- Linear programming problems, basic solution, basic feasible solution and optimal solution; Graphical method and simplex method of solutions; Duality. Transportation and assignment problems.
- Partial Differential Equations : 
	- Family of surfaces in three dimensions and formulation of partial differential equations; Solution of quasilinear partial differential equations of the first order, Cauchy’s method of characteristics; Linear partial differential equations of the second order with constant coefficients, canonical form; Equation of a vibrating string, heat equation, Laplace equation and their solutions. 
- Numerical Analysis and Computer Programming: 
	- Numerical methods: Solution of algebraic and transcendental equations of one variable by bisection, Regula-Falsi and Newton-Raphson methods, solution of system of linear equations by Gaussian Elimination and Gauss-Jorden (direct), Gauss-Seidel (iterative) methods. Newton’s (forward and backward) and interpolation, Lagrange’s interpolation. Numerical integration: Trapezoidal rule, Simpson’s rule, Gaussian quadrature formula. Numerical solution of ordinary differential equations : Eular and Runga Kutta methods. Computer Programming : Binary system; Arithmetic and logical operations on numbers; Octal and Hexadecimal Systems; Conversion to and from decimal Systems; Algebra of binary numbers. Elements of computer systems and concept of memory; Basic logic gates and truth tables, Boolean algebra, normal forms. Representation of unsigned integers, signed integers and reals, double precision reals and long integers. Algorithms and flow charts for solving numerical analysis problems. 
- Mechanics and Fluid Dynamics : Generalised coordinates; D’Alembert’s principle and Lagrange’s equations; Hamilton equations; Moment of inertia; Motion of rigid bodies in two dimensions. Equation of continuity; Euler’s equation of motion for inviscid flow; Stream-lines, path of a particle; Potential flow; Two-dimensional and axisymmetric motion; Sources and sinks, vortex motion; NavierStokes equation for a viscous fluid.