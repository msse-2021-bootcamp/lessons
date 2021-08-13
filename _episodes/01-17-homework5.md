---
title: "Homework Assignment #5"
teaching: 0
exercises: 120
questions:
- "What is the homework for the fifth day?"
objectives:
- "Add NumPy Monte Carlo Code to your package."
- "Use pytest to write tests for your code."
---


<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.7/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
  
  
## Blog Posts
Today's homework includes a few discussion questions. 
The person writing the group blog post today should include these answers in their post.

## Discussion

1. **Package Interface**: Most often in packages, you will have an additional file called `__init__.py`. 
The `__init__.py` file defines what modules should be imported when your package is imported.
Everyone should read the Python documentation [section on Packages](https://docs.python.org/3/tutorial/modules.html#packages). 

    The `__init__.py` file is a way to define how users will likely interact with your code. 
    Discuss with your group how you think functions should be called in your package.
    For example, as written now, our import is `import mcsim.monte_carlo`. 
    Is that ideal, or would is there a way you think would be better for your users to access your function?

1. **Adding NumPy** : You will notice that much of your code is the same between the two versions.
    Discuss with your group which functions have not changed, and which ones have changed.
    If you were to add your NumPy version of your Monte Carlo code to your package, what is a good way to do it? 

## Tasks

### Adding NumPy Version to Package

Add the NumPy version of your code to your package. 
What is the best way to reduce the amount of repeated code when adding your NumPy functions?

### Adding an `__init__.py` file
Add an `__init__.py` file to your package. 
You should modify the `__init__.py` file to have the interface decided by your group during the discussion.

### Adding an Analysis Module

You have two options for assignment concerning the analysis module. 
You should add another file, `analysis.py` which has functions for analyzing your simulation results.
You must pick one to complete the assignment, or you can do both for an extra challenge!

### Calculation of the pressure

On the [NIST page](https://mmlapps.nist.gov/srs/LJ_PURE/mc.htm) showing benchmarks for the MC of LJ fluids, 
a calculated pressure is also shown. 
Pressure is also a quantity we can calculate from our generated configurations.
For this assignment, you must add the ability to calculate pressure in an analysis module.

The pressure calculation is similar to the energy calcuation.
You will need a tail correction to be calculated based on the number of particles and the box size.
Then the pressure can be calculated according to the equations in reduced units:

$$ P^*_{virial} = -48 [(\frac{1}{r_{ij}})^{12} - (\frac{1}{r_{ij}})^{6}] $$

$$ 
P^* = \frac{1}{3V^*}(3NT^* + P^*_{virial}) 
$$



$$
P_{tail} = \frac{16 \pi N^2}{3 V^{*2}} \left[\frac{2}{3} (\frac{1}{r^*})^9 - (\frac{1}{r^*})^3\right] 
$$

Should this be added to your MC loop, or used as a post-processing analysis? (meaning that coordinates would be saved during similation and you perform calculate these values after)


### Time Averaged RDF
On Day 2, part of your homework was to use the radial distribution function (RDF) to analyze molecular configurations.
Create a module called `analysis.py` and add your radial distribution function.
Usually, when a radial distribution function is used for analysis, it is taken as a time-average.
Create a function, `time_averaged_rdf` which takes a list of molecular configurations and returns the time-averaged radial distribution function.

## Bonus

For this bonus, you should use the expressions for reduced units to derive the reduced unit expressions for pressure, given above.

Quantity    | Expression
------------|------------
Length      | $$L^*=L / \sigma$$
Density     | $$\rho^* = N \sigma^3 / V$$
Energy      | $$U^* = U / \epsilon$$
Pressure    | $$P^* = P \sigma^3 / \epsilon$$
Volume      | $$V^* = V / \sigma^3 $$
Temperature | $$T^* = k_{B} T / \epsilon $$
Time        | $$t^* = t \sqrt{\frac{\epsilon}{ m \sigma^2}}$$

The non-reduced expressions for pressure are:

$$ P = \frac{1}{3V} \left( 3 N k_B T + P_{virial} \right)$$

$$ P_{virial} = \mathbf{f}\left(r_{ij} \right) = -\frac{dU \left(r_{ij} \right)}{dr} = - \frac{48 \epsilon}{r^2_{ij}} \left[\left(\frac{\sigma}{r_{ij}}\right)^{12} -\frac{1}{2}\left(\frac{\sigma}{r_{ij}}\right)^{6} \right] \mathbf{r}_{ij}$$

And the tail correction

$$
P_{tail} = \frac{16 \pi N^2 \epsilon \sigma^3}{3 V^2} 
\left[\frac{2}{3} (\frac{\sigma}{r_c})^9 - (\frac{\sigma}{r_c})^3 \right]
$$

You can turn in your assignment using [this link](https://classroom.github.com/a/GadiK1os).

You should derive your expressions using pencil + paper and upload scans or pictures of your solutions.
To do this problem, you should fill the reduced unit expressions for appropriate quantities, and algebraically simplify the expressions.

This assignment is due in one week, on **August 20, 2021.**

