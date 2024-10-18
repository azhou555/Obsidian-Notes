Study Euler's methods, improved, implicit explicit, etc. Know what the order of a differential equation is, what it means, and so on. 
Step Size : $h$, increments of $y$ used to approximate $y_{i}$
Euler Method: $y_{n+1} = y_{n}+hf(t_{n}, y_{n})$. 
Concept: Approximate $y_{n+1}$ by taking the change in $y$ with respect to $t$ at a point where the values are already known and if the step size is super small it is basically an integral. 
Explicit 1st Order Approximation Method $O(n)$, each step is $O(n^2)$
Runge-Trapezoidal(Improved Euler's) Method: $y_{n+1} = y_{n}+\frac{h}{2}[f(t_{n}, y_{n})+f(t_{n+1}, y_n+h(f(t_{n}, y_{n})))]$ 
Concept: With the original Euler's Method, $f(t, y)$ is liable to change during the step. Therefore, approximate what $y_{n+1}$ is using the Euler's method, and then take the mean of that value and the known value to do a better approximation. 
Implicit 2nd Order Approximation Method $O(n^2)$
Runge-Midpoint Method: $y_{n+1} = y_{n}+h(f\left({t_{n+\frac{1}{2}}, y_{n}+\frac{h}{2}(t_{n}, y_{n})} \right)$
Concept: As the name suggests, approximate $y_{n+1}$ by approximating the midpoint first using Euler's and applying that. 
Implicit 2nd Order Approximation Method $O(n^2)$

ode45 is a precise numerical approximation using 4th and 5th order numerical methods: Matlab. 
Based on explicit 4th order Runge-Kutta method

Implicit numerical methods approximate using unknown values, whereas explicit numerical methods evaluate using known values. 
Example: Runge Midpoint and Runge Trapezoidal use explicit methods to approximate unknown values, and then use the approximations to approximate the final desired value. 