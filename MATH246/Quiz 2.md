## Phase Line Portraits
1. Find stationary points($\frac{dy}{dt} = 0$)
2. Find the signs before, in between, and after the stationary points
3. Stable stationary points are ones where the derivative is positive before and negative after
4. Unstable stationary points are ones where the derivative is negative before and positive after
5. Semi-stable stationary points are ones where the sign stays the same before and after the point
6. Using a phase line portrait, be able to estimate what the solution curves might look like. 
- When looking at a solutions curve graph, be able to tell which values of y are stationary points and whether or not they are stable, unstable, or semi-stable. This is done by observing the behavior of curve right before and right after the point. 
## Tanks and Mixtures
Learn the different situations for different types of application problems and how to solve them
When a tank is draining as a result of gravity, the rate out is equal to $a*\sqrt{2gh}$
$g$ is the acceleration of gravity ($g = 9.8 m/s^2$)
$a$ is the cross sectional area of stream of water flowing out the drain
$h$ is the height of the liquid or whatever mixture is flowing out
Always remember, when working with mixtures, tanks, and those kinds of problems, consider 
RATE IN - RATE OUT. When working with concentration, consider that $C(T) = \frac{Q(T)}{V(T)}$
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
As object falls it creates a wake which consumes kinetic energy. Modeled by $F_{turb} = -c|v|v$
where $c$ is a nonnegative constant and $|v|$ is the absolute value of $v$
Thus, the final equation is modeled by 
$F_{drag} = F_{visc}+F_{turb} = -bv - c|v|v$
### Terminal Velocity
Terminal velocity is described as the velocity at which an object can no longer change in speed, whether that be through slowing down to terminal velocity or accelerating to terminal velocity. In other words, it is the point at which $\frac{dv}{dt} = 0$. It is something similar to the carrying capacity in population dynamics. Typically, this is simply equal to $v_{\infty} = \sqrt{\frac{g}{k}}$
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
## Conclusion
Generally, the most important thing is memorizing the base equations. Ideally, being able to draw up the solution for the equation is best, but they can be derived, just with some effort. Pray for no logistic models. Know how to do partial fraction decomposition, a lot of the problems will take the form of an autonomous equation and necessitate that you be able to separate the fractions and integrate. 
