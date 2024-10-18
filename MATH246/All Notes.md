# Types of Equations
## Exactness
$H(x, y)$ such that $\partial x (H(x, y)) = M(x, y), \partial y (H(x, y)) = N(x, y)$
Equations take the form $M(x, y)dx+N(x, y)dy=0$
Equation is said to be exact if such a $H(x, y)$ exists such that $\partial y(\partial x(H(x, y))) = \partial y(\partial x(H(x, y)))$. In other words, $\partial y(M(x, y)) = \partial x(N(x, y))$. 
Generally, we might have an equation of the form $\frac{d}{dx}H(x,y)=H_{x}(x,y)+H_{y}(x,y)$. In this case, the solution to the DE is $H(x,y)=C$
#### Integrating Factor
 $\partial y(M(x, y) \neq \partial x(N(x, y)))$ 
Desire some $\rho(x, y)$ such that $\partial y(M(x, y)\rho) = \partial x(N(x, y)\rho)$. 
$$\partial y(M(x, y))\rho + \partial y(\rho)M(x, y) = \partial x(N(x, y))\rho +  \partial x(\rho)N(x, y)$$
Set either $\partial x (\rho) = 0 \text{ or } \partial y(\rho)=0$
That way, the equation is simplified. Pick whichever one simplifies it the most. 
## Homogeneous
$y'+a(x)y = 0$. Multiply by $e^{\int a(x) \, dx}$ and turn the equation into $\frac{d}{dx}( e^{\int a(x) \, dx}y)$ = 0, integrate both sides to get a constant $C$ and divide to isolate $y$. 
## Nonhomogeneous
$y'+a(x) = b(x)$. Find the same $e^{\int a(x) \, dx}$ and multiply equation by it, integrate, and then divide to isolate y. In both homogeneous and nonhomogeneous, the same integrating factor is used. With nonhomogeneous, there are just more steps needed. 
Please. Remember how to integrate. Trigonometric identities cannot be forgotten. 
General solution for a nonhomogeneous equation will take the form $$\displaystyle y = e^{-A(t)} \int b(x)e^{A(t)}dt$$ Where $A(t)$ is some antiderivative(integral) of $a(t)$. In most situations, simply integrate $a(t)$ and set the integrating constant, $C$ to $0$ to get the most simply expression. Try not to focus on memorizing this equation. Instead, you need to be able to derive it and understand how the formula is gotten and how to apply it. 
# Graphical Methods
## Phase Line Portraits
Manipulate the equation into a form such that we have $y' = f(y)$. We want to find the locations where $f(y) = 0$. These are going to be the critical points of our equation, the points where $\frac{dy}{dt} = 0$. 
In between the critical points, evaluate whether $\frac{dy}{dx}$ is positive or negative. On negative intervals, $y$ is decreasing as $t$ increases. On positive intervals, $y$ is increasing as $t$ increases. In order to draw a graph out, the asymptotes are where $\frac{dy}{dx}$ is equal to 0. Fill in the gaps. One graph might look like 
![[Pasted image 20240506211511.png]]
Note that for $-\infty<t<0$, $y$ is increasing, for $0<t<3$ y is decreasing, and for $3<t<\infty$, $y$ is increasing. We can describe some of these critical points. $y=0$ is a stable critical point because solutions approach/converge $y=0$ as $t\to \infty$, whereas $y=3$ is a non-stable critical point because solutions diverge from it. In situations where $y$ is diverging from one side and converging from the other side, we can describe it as a semi-stable point. 
## Contour Plots
Another type of graph. You can graph them just like any other graph by simply visualizing what solutions might look like. For example, take the equation $\displaystyle\frac{dy}{dx}=\frac{1}{2y-6}$. A solution takes the form $(y-3)^2=x+C+9$. In this case, the solution curves look like parabolas. ![[Pasted image 20240506212013.png]]
Given an IVP, we can isolate one of these curves and describe it as the function curve for $y$. However, note that only half of one of the curves can describe a single IVP(otherwise, it would no longer be a function). 
## Direction (Slope) Fields
In a direction field graph, we simply set up spaced out points and draw a line representing the slope of the function, or $\frac{dy}{dx}$ at each one of those points. Essentially, the graph shows what the graph to a solution to the equation might look like. With an IVP, we can find that point on the graph and use the surrounding lines to estimate what the graph might look like without actually solving for $y$. ![[Pasted image 20240507091009.png]]
Above, we have the graph of $\frac{dy}{dt}=t-y^2$ and an IVP of $y(-1)=0$. As shown, we found the point $(-1, 0)$ and plotted it on the graph, then used the direction lines to create a solution curve. 
# Applications
## Tanks and Mixtures
Learn the different situations for different types of application problems and how to solve them
When a tank is draining as a result of gravity, the rate out is equal to $a*\sqrt{2gh}$
$g$ is the acceleration of gravity ($g = 9.8 m/s^2$)
$a$ is the cross sectional area of stream of water flowing out the drain
$h$ is the height of the liquid or whatever mixture is flowing out
Always remember, when working with mixtures, tanks, and those kinds of problems, consider 
RATE IN - RATE OUT. Create an equation such that $Q'(t)=\text{RATE IN}-\text{RATE OUT}$. When working with concentration, consider that $C(T) = \frac{Q(T)}{V(T)}$
where $Q(T)$ is the quantity of whatever we are working with(salt, chocolate, sugar, whtf)
## Population Dynamics
$\frac{dp}{dt} = R(p)p-h(t)$
Doubling every three weeks -> $\displaystyle 2^{\frac{1}{3}*t} = e ^{\frac{1}{3}*ln(2)*t}$ -> $\displaystyle r = \frac{1}{3}ln(2)$
### Logistic Model
Population change rate is also affected by the size of the population itself. Model looks something like $\displaystyle \frac{dp}{dt} = (r-ap)p$ where $r$ and $a$ are constant variables that describe the change in population. 
The stationary points of the phase line portrait are $p = 0$ and $p = \frac{r}{a}$
If we let $k = r/a$ denote the carrying capacity of the ecosystem, then the logistic model 
can be expressed as $\displaystyle \frac{dp}{dt} = r(1-\frac{p}{k})p$
and can then be simplified into $\displaystyle p(t) = \frac{ke^{rt}p_I}{k+(e^{rt}-1)p_I}$
Note that the carrying capacity of the population denotes the maximum/minimum sustainable population, in other words the limit. It is also when $\frac{dp}{dt} = 0$. 
If we have some $t=I, T_1, T_2$, we can get that $\displaystyle e^{rT_1} = \frac{p_{T_1}(k-p_I)}{p_I(k-p_{T_1})}$ and $\displaystyle e^{rT_2} = \frac{p_{T_2}(k-p_I)}{p_I(k-p_{T_2})}$
and then continue to solve for $r$. 
## Motion
A moving object with fixed mass $m$ is governed by $ma = F$, where $a$ is acceleration and $F$ is the net force acting on it. Thus, $\displaystyle m\frac{dv}{dt} =$ gravitational force $+$ drag force = $F_{grav}+F_{drag}$
### Gravity
Gravity pulls the object down, whereas drag resists the pull of the object. Consequently, a falling object can be modeled using a linear equation. 
We can go on approximate $F_{grav} = mg$ where $g$ is the gravitational constant, or $9.8m/sec^2$
For situations where there is a medium, $F = \alpha mg$ where $\displaystyle \alpha = \frac{\rho_{obj}-\rho_{med}}{\rho_{obj}+\rho_{med}}$ where $\rho_{obj}$ is the density of the object and $\rho_{med}$ is the density of the medium. This number is also known as the Atwood number and consists of values between -1 and 1. 
When $\alpha$ is negative, $F_{grav}$ is also negative and results in an object rising. Think buoyancy. 
### Drag
**Viscous Drag**
Moving heats surrounding objects, results in a loss of kinetic energy. Modeled by $\displaystyle F_{visc} = -bv$ where $b$ is nonnegative constant
**Turbulent Drag** 
As object falls it creates a wake which consumes kinetic energy. Modeled by $F_{turb} = -k|v|v$
where $k$ is a nonnegative constant and $|v|$ is the absolute value of $v$
Thus, the final equation is modeled by 
$F_{drag} = F_{visc}+F_{turb} = -bv - c|v|v$
### Terminal Velocity
Terminal velocity is described as the velocity at which an object can no longer change in speed, whether that be through slowing down to terminal velocity or accelerating to terminal velocity. In other words, it is the point at which $\frac{dv}{dt} = 0$. It is something similar to the carrying capacity in population dynamics. Typically, this is simply equal to $v_{\infty} = \sqrt{\frac{g}{k}}$. Note that terminal velocity is only relevant in drag problems. If we are solely calculating gravity, we can't reach a point where it will stop accelerating. 
### Example Problems
A common problem of turbulent drag through air sets is as follows: $\displaystyle F_{turb} = -\frac{1}{2}\rho_{air}A|v|v$,
where $\rho_{air}$ describes the density of the air and $A$ is the aerodynamic cross section. Note that the values for $\rho_{air}$ and $A$ will be given in these types of problems. We can create a differential equation of the form $\frac{dv}{dt} = g-k|v|v$, where $k = \frac{\rho_{air}A}{2m}>0$. In some cases, the problem will provide the elements such as $m$, $\rho_{air}$, and $A$, or simply explicitly provide what is known as the drag constant, or $k$. Generally, many equation of this type will take the form $\displaystyle \frac{dv}{dt} = g-kv^2$
From there, we can go on to set up an equation $\displaystyle \frac{dv}{dt} = k(v_{\infty}^2-v^2)$
Solving the equation will result in something that looks like $\displaystyle v(t) = v_{\infty}\frac{e^{2v_{\infty}kt}-1}{e^{2v_{\infty}kt}+1}$

When moving through a very viscous liquid, we instead ignore the turbulence drag:
$\displaystyle \frac{dv}{dt} = \alpha g - rv$, where $\displaystyle r = \frac{\rho_{med}v_{med}L}{m} > 0$. We have a single stationary solution at $\displaystyle v_{\infty} = \frac{\alpha g}{r}$. 
The equation has solution $\displaystyle v(t) = e^{-rt}v_o+(1-e^{-rt})v_{\infty}$ 
## Loans
Consider loan problems as being similar to the tank mixture problems or population dynamics where there is a growth rate and something being subtracted. In the case of loans, the APR(Annual Percentage Rate) term is dependent on the amount of money owned, and the amount of money withdrawn is likely to be a constant subtracter. The equation generally looks something like $\displaystyle \frac{dB}{dt} = rB-P$ where $r$ is the APR and $P$ is the annum payment rate(constant). An IVP of this type will usually have the constraint of $B(0) = B_I$ and we are solving for $B(T) = 0$. These problems shouldn't be difficult, maneuver to $\displaystyle \frac{dB}{dt}-rB = -P$  and set up a $\mu = e^{\int -rBdt}$ such that $\displaystyle \frac{d}{dt}(\mu B) = -\mu P$. Integrate and solve for $B(T)$. 
# Numerical Approximation Methods
$h$ is the step size
## Euler's Method
$t_{i}=t_{i-1}+h$ 
$y_{i}\approx y_{i-1}+h*f(t_{i-1}, y_{i-1})$
Basically, use previous values of $t$ and $y$ with a step of $h$ to approximate. Explicit method, only uses known values. $O(n)$, first order. 
## Runge-Trapezoidal Method
$t_{i}=t_{i-1}+h$
$y_{i}\approx y_{i-1}+\frac{1}{2}h(f(t_{i-1}, y_{i-1})+f(t_{i-1}+h, y_{i-1}+h*f(t_{i-1}, y_{i-1})))$
The theory behind this is to use Euler's method to approximate a $y_{i}$ and then create a trapezoid of sorts. Implicit second order method, $O(n^2)$. 
## Runge Midpoint Method
$t_{i}=t_{i-1}+h$
$y_{i}\approx y_{i-1}+hf\left( t_{i-1}+\frac{1}{2}h , y_{i-1}+\frac{1}{2}hf(t_{i-1}, y_{i-1})\right)$
Approximate the midpoint between $y_{i}$ and $y_{i-1}$ using Euler's method and then use that approximated midpoint value to approximate $y_{i}$. Implicit second order method, $O(n^2)$. 
# General Theory
## Wronskian
$$W[y_{1},y_{2}]=\left|\begin{array}{cc}
y_{1} & y_{2} \\
y_{1}' & y_{2}' 
\end{array}\right|$$
As long as the Wronskian of our set of solutions is not equal to 0, then they are a valid set of solutions. Linear independence and whatnot. 
# Solving homogeneous higher order ODEs w/ constant coefficients
$ay''+by'+cy=0$. Substitute $y=e^{rt}$ and divide both sides by $e^{rt}$ to get the **characteristic polynomial**, of the form $ar^2+br+c=0$. Note that we can use the same method with higher order ODEs, but most common example will be an equation of second order and thus two roots(two solutions for $r$). With one of these types of equations, the general solution will take the form $y=c_{1}e^{r_{1}t}+c_{2}e^{r_{2}t}$ where $c_{1}$ and $c_{2}$ are some constants that can be solved for by plugging in an IVP and solving. $r_{1}$ and $r_{2}$ will be the two roots of the characteristic polynomial. In the case of a double root where $b^2-4ac=0$, use $te^{r_{1}t}$ as the second "component". 
# Solving Non-homogeneous higher order ODEs
Now that we have some $f(t)$ on the right hand side, we can't use the same general formula from before. However, we can use the associated homogeneous to generate a general solution to the non-homogeneous equation. $y=y_{p}+y_{c}$ where $y_{p}$ is a particular solution for the non-homogeneous, and $y_{c}$ is the general solution to the associated homogeneous. 
## Undetermined Coefficients
The idea of undetermined coefficients is that we might be able to guess what a particular solution will look like, given what $f(t)$ is. This only really works when our $f(t)$ is something nice. For example, if $f(t)=e^{5t}$, a good guess for $y_{p}$ might be $Ae^{5t}$. When we have something that involves $\cos$ or $\sin$, remember to include both. For example, if $f(t)=\cos(2t)$, guess $A\cos(2t)+B\sin(2t)$. This is because when you derivate trigonometric functions, you get other trigonometric functions. If we have $f(t)=te^{5t}$, guess $Ae^{5t}+Bte^{5t}$. Same logic with the trigonometric functions. As you do more derivations, some of the $t$s will disappear, so you need all versions with lower order. Make sure when using this method that no terms of the particular solution overlap with the general solution for the associated homogeneous. For example, if we have $f(t)=e^{5t}$ but $5$ is already one of the roots, we can guess $te^{5t}$. For each multiplicity of $z$, we simply increase the order of $t$ by $1$. If $z$ has multiplicity $0$, we don't need to worry. However, if $z$ had a multiplicity of $2$, we would need to guess something along the lines of $At^2e^{zt}+Bte^{zt}+Ce^{zt}$. After that, just plug it in, solve for the *undetermined coefficients*, and combine with general solution of associated homogeneous to get the general solution of the non-homogeneous. Note that the final solution, if it isn't an IVP, will still have constants $c_{1}$ and $c_{2}$. 
## Variation of Parameters
There's a lot of math behind the scenes, but you don't really need to know it and it shouldn't come up during any exams. Basically, the gist of it is that you can express $y_{p}$ as $u_{1}y_{1}+u_{2}y_{2}$ where $y_{1}$ and $y_{2}$ are the components that make up our associated homogeneous solution. $u_{1}=\int-\frac{y_{2}f}{W[y_{1}, y_{2}]}$ and $u_{2}=\int \frac{y_{1}f}{W[y_{1}, y_{2}]}$. Unlike undetermined coefficients which only works well when the forcing, $f(t)$ is clean and allows us to easily generalize the solution, variation of parameters is usable in all cases. It can be a bit computational heavy since it requires calculating the Wronskian as well as evaluating integrals and calculating long products, it is still very useful. 
# Laplace Transforms
## General Theory
The Laplace Transformation of a function $y(t)$ is defines as $\int_{0}^{\infty}y(t)e^{-st}dt$. In actual computation, we instead use $\lim_{ b \to \infty }\int_{{0}^b}y(t)e^{-st}dt$ since we can't take an integral from $0$ to $\infty$. With very simple functions for $f(t)$, it isn't too difficult to compute. However, we eventually just start using identities instead because computation becomes cumbersome. Note some special notation. You might see $Y(s)$ rather than $L(y(t))$ simply for ease of notation. Naturally, $L$ is also a invertible function. 
## Application
The reason why the Laplace transform matters is because we can express $L[y'(t)]=sL[y(t)]-y(0)$. In other words, after applying the Laplace transform, we can get rid of any derivatives in the equation. Likewise, we can apply this to higher powers as well. For example, $L[y''(t)]=s^2L[y(t)]-sy(0)-y'(0)$ and so on. Solving an IVP using Laplace transforms involved taking the Laplace of both sides, isolating $L[y(t)]$, and then taking the inverse Laplace transform such that we are left with $y(t)$ on one side and whatever mess is left on the other side. 
## Step Functions
We define the step function as $u(t)=\begin{cases}0&t<0 \\1&t\ge0\end{cases}$. The general idea is that the step function turns other functions "on" and "off". Importantly, we can use the notation $u_{c}(t)=\begin{cases}0&t<c\\1&t\ge c\end{cases}$. When we put that together with other equations, we can express that $u_{\pi}(t)\sin(t-\pi)$ is $0$ for $t<\pi$ and $\sin(t-\pi)$ for $t\ge\pi$. You might also see the notation $u(t-c)$ rather than $u_{c}$. It may be confusing, but just remember the different types of notation. 
# Mechanical Vibration
Note that positive is going up and negative is going down. 
The basic setup for these types of problems is that there is a weight hanging from a spring. We might have a rest point $y_{r}$ which describes the point that the mass reaches in a state of rest. We can create an equation to describe this point of equilibrium: $mg=ky_{r}$ where $k$ is the spring constant, $g$ is the force of gravity($9.8$) and $m$ is the mass of the weight. 
We can then create a general equation, taking all possible forces into account:$$my''+\gamma y'+ky=f(t)$$
$\gamma$ describes a damping force, $k$ is the same spring constant and $m$ is the mass. Additionally, we have $f(t)$ as an external force acting upon the equation. 
Note these equations that may be needed to solve for some of these values:
$mg=ky$ and $F_{\text{Damping}}=\gamma y'$. In the latter, it might be that we are given $y'$ at some point in time as well as the $F_{\text{Damping}}$ at that moment and must solve for $\gamma$ . 
## Unforced and Undamped
$$my''+ky=0$$
No external forces or damping forces. Solution of the form $y=c_{1}\cos\left( t\sqrt{ \frac{k}{m} } \right)+c_{2}\sin\left( t\sqrt{ \frac{k}{m} } \right)$. We can generalize this even further to become $y=A\cos\left( t\sqrt{ \frac{k}{m} } -\delta\right)$, where $A=\sqrt{ c_{1}+c_{2} }$ describes the amplitude and $\delta$ satisfies $\cos \delta=\frac{c_{1}}{A}$ and $\sin \delta = \frac{c_{2}}{A}$. The graph of this is just nonstop oscillations with constant amplitude. 
## Unforced and Damped
$$my''+\gamma y'+ky=0$$
#### Underdamped
$\gamma^{2}-4mk< 0$. Two complex roots. Graph oscillates heavily, amplitude decreases over time and approaches 0. Oscillations continue infinitely and amplitude approaches 0 as $t\to \infty$. 
#### Critically Damped
$\gamma^2-4mk=0$. Double roots/one real root with multiplicity of 2. This represents the smallest possible $\gamma$ for which oscillation completely stops. In a graph, it goes asymptotically towards $y=0$. 
#### Overdamped
$\gamma^{2}-4mk>0$. Two real roots. Similarly to a critically damped graph, curve goes asymptotically towards $y=0$. 
	Although neither critically damped nor overdamped systems experience oscillation, critically damped systems have a slight curvature that overdamped systems lack. 
$e^tA=e^{\lambda t}(I-t(A-\lambda I))$ for duplicates. 