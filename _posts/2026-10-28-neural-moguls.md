---
layout: post
title:  "Moguls of Chaos with deep learning - Part 2"
permalink: /projects/neural-moguls/
---

<style>
.aligncenter {
    text-align: center;
}
</style>

[repository](https://github.com/cpierard/moguls_of_chaos).

<p class="aligncenter">
    <img src="/../assets/projects/neural_moguls/traj_test_b0.50_u3.50.png"/>
</p>
###### caption.

math

$$\frac{dx}{dt} = u, \quad \frac{dx}{dt} = v, \quad \frac{dz}{dt} = w.$$

\begin{align}
\frac{du}{dt} &= -F \partial_x H - cu,
\end{align}
\begin{align}
\frac{dv}{dt} &= -F \partial_y H - cv,
\end{align}
\begin{align}
\frac{dw}{dt} &= -g + F - cw,
\end{align}

this is how you math inline $$\vec{x} = (x,y,z)$$.

$$H(x,y) = -ax - b \ cos(px) \ cos(qy),$$

<p class="aligncenter">
    <img src="/../assets/projects/neural_moguls/traj_test_b0.50_u3.50.png"/>
</p>
###### caption.

# Subtitle

I used the fourth-order *Runge-Kutta method* as an integrator and wrap it around a *solver*, to integrate the four variables of the system. Once the solver is working properly, we can compute the solutions for different boards.

**Example 1**

For this example we set the initial conditions for ten boards, with slight variations in their initial position: $$x = 0.0$$ m, $$u = 3.5$$ m/s, $$v = 0$$ m/s, and $$y$$ it is randomly chosen form the interval $$[0,1]$$ m, in a way that $$y$$ is different for every board. The resulting trajectories can be seeing int the following figure.

<p class="aligncenter">
<img src="/../assets/projects/neural_moguls/mlp_rms_error_b0.50_u3.50.png" width="35%" />
</p>
###### caption.

<p class="aligncenter">
<img src="/../assets/projects/neural_moguls/mlp_phase_space_b0.50_u3.50.png" width="35%" />
</p>
###### caption.

<p class="aligncenter">
<img src="/../assets/projects/neural_moguls/mlp_phase_space_b0.50_u3.50.gif" width="35%" />
</p>
###### caption.