The notebooks here are based on those which were provided during the [2020 Winter School on Synchronization](https://complex-systems-turkey.github.io/) based on the [hands on material](https://github.com/noddslab/Winter-School-on-Synchronization) during 6-8 March 2020.
This workshop was guided by [Deniz Eroğlu](http://www.deroglu.com/) by Assistant Professor at Kadir Has University.
The main source material related to this workshop are:

* Strogatz, Steven H. Nonlinear Dynamics and Chaos: with Applications to Physics, Biology, Chemistry, and Engineering. CRC Press, 2018 (specifically Chapter 9: Lorenz Equations, but the whole book is a delight.)
* Eroglu, Deniz, Jeroen SW Lamb, and Tiago Pereira. “Synchronisation of chaos and its applications” Contemporary Physics 58.3 (2017): 207-243.

While reviewing what we learned from the workshop we refactored the juypter notebooks utilized during the workshop.
Our main focus during refactoring was to abstract the key concepts for expressivity and ease of manipulation.
The workshop started with fundamental concepts of numerical integration and approximators of different degrees.
This was followed by linear and nonlinear dynamical systems of 1-2-3 dimensions, Lorenz oscillators, and synchronization of chaos.
Finally, networks were utilized to examine the structure of coupled Lorenz systems.

To elegantly handle these concepts, we introduce some central computational components that may be composed in various ways. For example:

   * integration  may rely on alternative approximation methods while retaining the same iterative procedure in different methods such as the Euler’s  and Heun’s methods.
   Thus, we abstracted out the computation of approximation and integration (integrate). In this manner we pass the desired approximator to the integration function.

```python
integrate(euler, f=f, x=x0, t=ts)
integrate(heun, f=f, x=x0, t=ts)
integrate(rk4, f=f, x=x0, t=ts)
```

   for Euler, Heun, and Runge-Kutta methods.

   * The behavior of a network of systems depends on the individual dynamics of each subsystem as well as the nature of the interaction and topology of the network.
   Depending on our problem, the subsystems, the topology of the network or the type of interaction can change.
   Thus, in the 3rd notebook we developed a meta function that builds a dynamical system rule (that can readily used in our integration scheme) for **the whole network** given these individual components.

```python
couple_identical_network(
   f=lorenz_system,
   A=adjacency_matrix,
   h=coupling_matrix_or_function,
   alpha=coupling_strength)
```

We wanted to share these notes for whatever they may be worth. If you have any questions or comments please contact us at [GitHub repository](https://github.com/complex-systems-turkey/winter-2020-synchronization).

* [Oğuz Kaan Yüksel](https://github.com/okyksl)
* [Enis Simsar](https://github.com/enisimsar)
* [Galip Ümit Yolcu](https://github.com/gumityolcu)
* [Suzan Üsküdarlı](https://github.com/uskudarli)
