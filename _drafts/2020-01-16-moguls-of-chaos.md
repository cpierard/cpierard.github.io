---
layout: post
title:  "Moguls of Chaos"
permalink: /projects/moguls-of-chaos/
---

<style>
.aligncenter {
    text-align: center;
}
</style>

<p class="aligncenter">
    <img src="https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.independentsportsnews.com%2Fwp-content%2Fuploads%2F2018%2F12%2FFIS-Freestyle-Ski-World-Cup-in-Thaiwoo.jpg&f=1&nofb=1" width = "450" alt="centered image"/>
</p>

This example was taken from the book **The Essence of Chaos** by *Edward Lorenz*. The aim of the model he presets in that chapter is to show how we can construct parsimonious models from real case phenomena that exhibit chaos.

The model consists of a board that goes down a regularly-bumpy slope or moguls without any control of the direction whatsoever. The dynamical system of this board is described by the system of ODE shown bellow

$$\frac{dx}{dt} = U, \quad \frac{dx}{dt} = V, \quad \frac{dz}{dt} = W.$$

\begin{align}
\frac{du}{dt} &= -F \partial_x H - cu,
\end{align}
\begin{align}
\frac{dv}{dt} &= -F \partial_y H - cv,
\end{align}
\begin{align}
\frac{dw}{dt} &= -g + F - cw.
\end{align}
\begin{align}
\frac{d \vec{u}}{dt} &= -F \nabla_H H - c \vec{u}.\\
\end{align}

$$\vec{x} = (x,y,z)$$ are the spacial coordinates and $$\vec{u} = (u,v,w)$$ are the components of the velocity of the board. And $$H$$ is the shape pf the slope that is parameterized by the following expression:

$$H(x,y) = -ax - b \ cos(px) \ cos(qy).$$

Our first goal is to solve the ODE system for a given initial condition using a numerical integration method.

# Boards down the slope!

Our first goal is to solve the ODE system for a given initial condition using a numerical integration method. For this, we declare a function containing the right-hand side terms of the ODE system that we want to solve.

We use the fourth-order **Runge-Kutta method** as an integrator and we wrap it around the `solver` function.

So now that we have our solver we can crush some snow with our boards in the moguls!

**Example 1**

Initial conditions: $$x = 0.0$$, $$y = [0,1]$$ (randomly chosen), $$U = 3.5$$ and $$V = 0$$.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/bords_rand.png" width="30%" />
</p>

**Example 3**
Initial conditions just spaced 1mm apart from $$0.497$$m to $$0.503$$m.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/boards_1mm.png" width="30%" />
</p>


The above shows that the system is sensitive to initial conditions but we would like to explore further the dynamics of the system. One of the techniques for exploring the dynamics of the system is by plotting the phase space and see how the system behaves. The only problem is that for this system, there are 4 variables, which means that the phase space of the system lives in a four-dimensional space, which is not possible for us to visualize. We need to do some modifications to our board to reduce the dimensions of our system.

# Sleds down the slope!

To reduce the dimensions of our system, we can make the downslope velocity to be constants, or in the real world, by equipping our board with some brakes and an engine so it can maintain a constant velocity while going down the pits or up the bumps. In a mathematical sense, we say that $$\partial_t U = 0$$.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/sleds.png" width="30%" />
</p>


Initial conditions $$x = 0$$ m, $$y = [0, 0.1]$$ m, $$v = 2$$ m/s and $$u = 3.5$$ m/s.

We see that the system behaves chaotically even though the downslope speed is maintained.

# Sleds and strange attractors

Now our system has 3 variables, which will allow us to plot its phase space. The only problem now is that the system is no compact because $$x$$ and $$y$$ can grow or decrease infinitely. Although, the cross slope velocity $$v$$ is bounded between $$-5$$ m/s and $$5$$ m/s, because of friction.

A way to do this is reducing the slope to be $$x \in [-5, 5]$$ m and $$y \in [-2, 2]$$ m, and set the boundaries to be periodic. This way, we will be able to compact the position of the sled without altering the physics of the system.

We can see how the sled goes out of the domain and re-enters at the opposite side.

The main interest of this is to build a strange attractor. For this, we set a ensemble of sled all starting from $$x = 0$$m, but with random $$y$$ and cross slope velocities $$v$$, with $$u$$ set to 3.5m.

**Ten thousand sleds going down the slope!**

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/b_05.gif" width="50%" />
</p>


# Routes from Chaos

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/b_01.gif" width="33%" />
<img src="/../assets/projects/moguls_of_chaos/b_02.gif" width="33%" />
<img src="/../assets/projects/moguls_of_chaos/b_05.gif" width="33%" />
<img src="/../assets/projects/moguls_of_chaos/b_06.gif" width="33%" />
</p>

Now we see that the attractor changes if we change the height of the bumps in the slope, the parameter $$b$$. Especially, we can think that when $$b = 0$$ m, the sled will follow straight lines, which are non-chaotic, and as we increase $$b$$ these trajectories will transition to chaotic ones.

A practical way of visualizing this is by a bifurcation diagram, in which we plot the state of the system according to a parameter that drives the system.

In the sled case, we can use the local maximum cross slope velocity, deleting the transient states, to visualize were the sled has a periodic behavior or a chaotic one

We can see that there is axial symmetry concerning $$V = 0$$ m/s. This means that the bifurcation diagram can be drawn in either the negative side of the velocities or the positive side, creating regions without a point in the lower and upper part.

We can correct this is we consider only the cross slope speed, i.e. take the absolute value of $$V$$.

![](/../assets/projects/moguls_of_chaos/bifurcation_diagram_speed.png)

# References

- Lorenz, Edward N. *The Essence of Chaos*. Univ. of Washington Press, 1993.
