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
On Day 2, part of your homework was to use the radial distribution function to analyze molecular configurations.
Create a module called `analysis.py` and add your radial distribution function.
Usually, when a radial distribution function is used for analysis, it is taken as a time-average.
Create a function, `time_averaged_rdf` which takes a list of molecular configurations and returns the time-averaged radial distribution function.