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

Mogul skiing is a ski discipline that consists of descending a slope full of small regular bumps, where the skills and technique of skiers are tested to its full. Ed Lorenz, an outdoorsman and science legend, discovered that objects descending the moguls exhibit chaotic behavior. He built a small numerical model to explore the dynamics of an idealized board descending such type of slopes and exemplified some of the tools used for studying chaos.

<p class="aligncenter">
    <img src="https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fwww.independentsportsnews.com%2Fwp-content%2Fuploads%2F2018%2F12%2FFIS-Freestyle-Ski-World-Cup-in-Thaiwoo.jpg&f=1&nofb=1" width = "450" alt="centered image"/>
</p>

This example was taken from the book **The Essence of Chaos** by *Edward Lorenz*. The aim of the model he presents in his book is showing how we can construct parsimonious models that exhibit chaos, from real case phenomena.

The model consists of a board that goes down a regularly-bumpy slope or moguls without any control of the direction whatsoever. The dynamical system of this board is described by the system of ODE shown bellow

$$\frac{dx}{dt} = u, \quad \frac{dx}{dt} = v, \quad \frac{dz}{dt} = w.$$

\begin{align}
\frac{du}{dt} &= -F \partial_x H - cu,
\end{align}
\begin{align}
\frac{dv}{dt} &= -F \partial_y H - cv,
\end{align}
\begin{align}
\frac{dw}{dt} &= -g + F - cw.
\end{align}

$$\vec{x} = (x,y,z)$$ are the spacial coordinates and $$\vec{u} = (u,v,w)$$ are the components of the velocity of the board. $$H$$ is the shape of the slope that is parameterized by the following expression:

$$H(x,y) = -ax - b \ cos(px) \ cos(qy),$$

where $$p$$ and $$q$$ are the spatial frequencies in which the bumps and pits alternate. The $$a$$ parameter is the angle of the slope and the $$b$$ parameter can be seen as the height of the bumps measured form the mean slope (remember this parameter because it will be important for the last section).

This system of equations can be solved numerically using a Runge-Kutta scheme, thus, our first objective is to integrate several solutions for different initial conditions to observe the behavior of the board.

This blog doesn't show the code used to solve the equations or plot the examples, but it can be found in the following [repository](https://github.com/cpierard/moguls_of_chaos).

# Boards down the slope!

I used the fourth-order *Runge-Kutta method* as an integrator and wrap it around a *solver*, to integrate the four variables of the system. Once the solver is working properly, we can compute the solutions for different boards.

**Example 1**

For this example we set the initial conditions for ten boards, with slight variations in their initial position: $$x = 0.0$$, $$u = 3.5$$, $$v = 0$$, and $$y$$ it is randomly chosen form the interval $$[0,1]$$, in a way that $$y$$ is different for every board. The resulting trajectories can be seeing int the following figure.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/bords_rand.png" width="30%" />
</p>

We can see how the boards follow similar trajectories, down until 10 m, where they start to diverge.

**Example 2**
We can explore the behavior with other initial conditions, but this time we set the $$y$$ position of 7 boards only 1 mm apart between the values $$[0.497, 0.503]$$ m, keeping the same values for $$x,u,v$$ used in the previous example.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/boards_1mm.png" width="30%" />
</p>

The figure above shows how the trajectories of the boards are practically the same until 20 m down the slope. After 20 m, some small variations appear in the trajectories of the boards, until they start growing bigger and bigger. Around 50 m down the slope, the trajectories diverge completely one from another, following very different paths.

These boards are a perfect example of a system that is sensitive to initial conditions, i.e. that small perturbations or variations in the initial conditions can lead to totally different solutions at some time in the future, which is commonly known as **chaos theory**.

From the trajectories of the boards is difficult to find regularities in the dynamics of this system, because the trajectories appear to behave randomly as they go down the slope. Therefore, in order to find regularity, we can use the velocities of the boards as they go down the slope. One of the tools that are very handy in the dynamical systems is the phase space plots, which basically consists of plotting the velocity of a system against its position. The problem is that our system has two spatial coordinates and two velocities components, which would make our phase space plot four-dimensional. Our brains can't handle a four-dimensional space, so we need to do some modifications to our system in order to reduce its dimensions to only three.

# Sleds down the slope!

To reduce the dimensions of our system, we can make the downslope velocity constant, or in the real world scenario, by equipping our board with some brakes and an engine so it can maintain a constant velocity while going down the pits or up the bumps, transforming it into a sled! In a mathematical sense, we say that $$\partial_t u = 0$$. This modification allows us to neglect the $$u$$ component of velocity and reduce the phase space to three dimensions.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/sleds.png" width="30%" />
</p>

The previous figure shows eleven sleds going down the slope, with initial conditions $$x = 0$$ m, $$y = [0, 0.1]$$ m, $$v = 2$$ m/s, and $$u = 3.5$$ m/s. We see that the system behaves chaotically even though the downslope speed is maintained. We also see how all the sleds reach the same downslope position by the end of the simulation.

# Sleds and strange attractors

Now our system has 3 variables, which will allow us to visualize its phase space plot. But the modifications that we need to do to our system are not over. If we see the trajectory-plots displayed above, we can see that $$x$$ and $$y$$ grow infinitely, which means that our phase space plot will not be compact, just a collection of points scattered around an infinite domain. The good news is that the cross-slope velocity is already bounded between $$[-5, 5]$$ m/s because of friction.

We need to find a way to make our system compact while preserving the physics of the system. If we analyze closely the structure of our mogul-slope, we can see that it is a collection of regular bumps and pits, that repeat themselves towards infinity.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/shape_of_moguls.png" width="70%" />
</p>

Therefore, we can crop our domain in a tile (figure below) from which we can reconstruct our full slope by placing consecutive tiles next to one another. In other words, we take this tile and set its boundaries to be periodic, so whatever exits the right side, re-enters the domain by the left side, and whatever exits the domain in by the lower boundary, re-enters by the top boundary. This slope-tile is defined in the domain: $$x \in [-5,5]$$ m and $$y \in [-2,2]$$ m.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/shape_of_moguls_compact.png" width="50%" />
</p>

**The washing machine!**

Once that our system is compact, we can run some simulations to plot the phase space of the system. The thing is that if we run it for one sled, we will see only a point traveling with apparent random motions in the 3D domain. So, a good idea would be to simulate a good amount of sleds, an ensemble of sleds, with the same downward velocity and with random initial positions (inside the domain of the tile) and random cross slope velocities. This will fill the phase-space of points and we will be able to see how they evolve as the descend the moguls. The downside of this is that it will be really difficult for us to identify any structures in the phase space because basically, the phase space plot will consist of a turbulent soup of points that flows down weirdly.

To cope with this visualization challenge, we can use another tool called **Poincaré maps**, in which we intersect the phase space with a plane transversal to the "flow", which in our case are planes defined by $$x = \text{constant}$$. However, we can take advantage of the feature that our sleds descend the slope with constant velocity $$u$$ to define our version of the Poincaré map. In other words, we set the downward velocity of the ensemble to be the same for all the members, but with different cross-slope positions and velocities, in a manner that they will form planes that go down the slope. This set-up will allow us to get rid of the $$x$$ coordinate in the phase space plot and only plot $$v$$ against $$y$$.

For the first run, we set an ensemble of 8000 sleds, all starting from $$x = 0$$ m, but with random $$y$$, random cross slope velocities $$v$$ and with $$u = 3.5$$ m/s, for all the members. The result can be seen in the following animation.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/b_05.gif" width="50%" />
</p>

We can see that is like a [horseshoe map](https://en.wikipedia.org/wiki/Horseshoe_map), but also, it reminds me of a washing machine!

# Routes from Chaos

Now we see that the attractor changes if we change the height of the bumps in the slope, the parameter $$b$$. Especially, we can think that when $$b = 0$$ m, the sled will follow straight lines, which are non-chaotic, and as we increase $$b$$ these trajectories will transition to chaotic ones.

<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/b_01.gif" width="33%" />
<img src="/../assets/projects/moguls_of_chaos/b_02.gif" width="33%" />
</p>
<p class="aligncenter">
<img src="/../assets/projects/moguls_of_chaos/b_05.gif" width="33%" />
<img src="/../assets/projects/moguls_of_chaos/b_06.gif" width="33%" />
</p>

A practical way of visualizing this is by a bifurcation diagram, in which we plot the state of the system according to a parameter that drives the system. We can use the local maximum cross slope velocity, deleting the transient states, to visualize where the sled has a periodic behavior or a chaotic one

We can correct this is we consider only the cross slope speed, i.e. take the absolute value of $$V$$.

![](/../assets/projects/moguls_of_chaos/bifurcation_diagram_speed.png)

# References

- Lorenz, Edward N. *The Essence of Chaos*. Univ. of Washington Press, 1993.
