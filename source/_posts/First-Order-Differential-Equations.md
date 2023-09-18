---
title: First Order Differential Equations
date: 2023-09-17 21:22:13
tags: [MAT244, math, uoft, ode]
category: [Notes, Year2, MAT244]
mathjax: true
---

# First order equations

First order Differential equations are equations that include only $y$ and $y'$

## Separable First Order Differential equations

These are the easiest ones to solve. They are in the form

$$
\frac{dy}{dx} = \frac{f(x)}{g(y)}
$$

This is easy. We can **separate** the two variables to yield

$$
g(y)dy = f(x) dx
$$

Integrating both parts, we get
$$
\int g(y) dy = \int f(x) dx + C
$$

## Linear Differential Equations

These are equations in the form 
$$
y' + p(x)y = q(x)
$$

if $q(x) = 0$ then the equation is called homogeneous, else it is inhomogeneous.

for homogenous equations, we can separate the variables.

$$
\begin{align*}
    y'+p(x)y &= 0\\
    y' &= -p(x)y\\
    \frac{dy}{dx} &= -p(x)y\\
    \frac{dy}{y} &= -p(x)dx\\
    \int \frac{dy}{y} &= \int-p(x)dx\\
    \ln|y|&= \int p(x)dx\\
    y &= e^{\int p(x)dx} + C
\end{align*}
$$
where $C$ is a constant. With **initial condition** $y(0) = y_0$, we can solve for $C$.

As for inhomogeneous equations, there are two methods

### Variation of Perimeters

*(tbh I don't know how this works.)*

First assume the solution is 
$$
y = ue^{-P(x)}
$$
where $P(x) = \int p(x)dx$ and $u$ is a function about x

Then substitute $u(x)$ into the equation

$$
\begin{align*}
    y' = u'e^{-P(x)} + -p(x)ue^{-P(x)} + p(x)ue^{-P(x)} &= q(x)\\
    u'e^{-P(x)} &= q(x)
    u = \int e^{-P(x)} q(x)dx + C
\end{align*}
$$

Then substitute back to the assumption, we get

$$
y = e^{-P(x)}\int e^P(x)q(x) dx + Ce^{-P(x)}
$$

### Method of separating factors

The idea is to somehow turn the LHS into $(\mu y)'$ by using the product rule. So we need to find the appropriate $\mu$. Luckily this could be done by solving a separable ODE.

First multiply $\mu$ to both sides of the equation.

$$
\begin{align*}
    \mu y' + \mu p(x)y &= \mu q(x)\\
\end{align*}
$$

Then by the product rule, in order for the LHS to be $(\mu y)'$, it must be true that $\mu' = p(x)\mu$. This is a separable linear equation. Solve it we get:

$\mu = C_0e^{\int p(x) dx}$.

Then with this proper $\mu$, the ODE turns into

$$
\begin{align*}
    (\mu y)' &= p(x)\\
    y &= \mu^{-1}\int \mu p(x) dx + \mu^{-1}C\\
    y &= \frac{\int C_0e^{\int p(x) dx}p(x) dx}{C_0e^{\int p(x) dx}} + \frac{C}{C_0e^{\int p(x) dx}}
\end{align*}
$$

since the $C_0$ cancels out in the first term, and we can choose $C = \frac{C}{C_0}$ in the second term, the choice of $C_0$ doesn't matter. So without loss of generality, choose $C_0 = 1$

$$
    y = e^{-\int p(x) dx}  \int e^{\int p(x) dx}p(x)dx + C{e^{-\int p(x) dx}}
$$

> The two methods derive the exact same general solution to the equations

## Miscellaneous First Order ODEs

These are some ODEs that could be reduced to first order/separable ODEs.


### Bernoulli equation

They are of the form 

$$y' + p(t)y + g(t)y^n$$

where $n \neq 1, 2$ and $t > 0$

Strategy: let $z = y(t)^{1-n}$

Then 
$$ z' = (1-n)y^{-n}y'$$

Then we multiply both sides of the equation by $(1-n)y^{-n}$

$$
\begin{align*}
    y'(1-n)y^{-n} - (1-n)p(t)yy^{-n} &= g(t)(1-n)y^ny^{-n}\\
    z'-(1-n)p(t)z&=(1-n)g(t)
\end{align*}
$$
Then we get an ODE.

$$ $$

### Homogenous (non-linear) ODEs

they are in the form
$$
\frac{dy}{dx} = \phi(\frac{y}{x})
$$
usually $\phi(\frac{y}{x}) = \frac{ax+by}{cx+dy}$. Now we can let $y = ux$, so
$$
y' = u'x + u = \phi(u) \Rightarrow u' = \frac{1}{x}(\phi(u)-u)
$$

Now we have a new separable ODE.

$$
\begin{align*}
\int \frac{du}{\phi(u)-u} &= \frac{dx}{x}\\
x &= e^{\int \frac{du}{\phi(u)-u}}
\end{align*}
$$