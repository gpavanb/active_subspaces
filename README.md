# Description

[Active subspaces](http://activesubspaces.org) are part of an emerging set of tools for discovering low-dimensional structure in a given function of several variables. Interesting applications arise in deterministic computer simulations of complex physical systems, where the function is the map from the physical model's input parameters to its output quantity of interest. The active subspace is the span of particular directions in the input parameter space; perturbing the inputs along these *active* directions changes the output more, on average, than perturbing the inputs orthogonally to the active directions. By focusing on the model's response along active directions and ignoring the relatively inactive directions, we *reduce the dimension* for parameter studies---such as optimization and integration---that are essential to engineering tasks such as design and uncertainty quantification.

This library contains Python tools for discovering and exploiting a given model's active subspace. The user may provide a function handle to a complex model or its gradient with respect to the input parameters. Alternatively, the user may provide a set of input/output pairs from a previously executed set of runs (e.g., a Monte Carlo or Latin hypercube study). Essential classes and methods are documented; see documentation below. We also provide a set of [Jupyter](http://jupyter.org/) notebooks that demonstrate how to apply the code to a given model.

To see active subspace in action on real science and engineering applications, see the [Active Subspaces Data Sets](https://github.com/paulcon/as-data-sets) repository, which contains several Jupyter notebooks applying the methods to study input/output relationships in complex models.

# Status

[![Build Status](https://travis-ci.org/paulcon/active_subspaces.svg?branch=master)](https://travis-ci.org/paulcon/active_subspaces)

# Requirements and Dependencies

* [numpy](http://www.numpy.org/)
* [scipy](http://www.scipy.org/), >= 0.15.0
* [matplotlib](http://matplotlib.org/)
* [Gurobi](http://www.gurobi.com/) is an _optional_ dependency. The same functionality is accomplished with SciPy's [optimize](http://docs.scipy.org/doc/scipy/reference/optimize.html) package, albeit less accurately (particularly in the quadratic programs).

If you wish to use Gurobi, you will need to install it separately by following the instructions contained in their quick-start guides for [Windows](http://www.gurobi.com/documentation/6.5/quickstart_windows.pdf), [Linux](http://www.gurobi.com/documentation/6.5/quickstart_linux.pdf), or [Mac](http://www.gurobi.com/documentation/6.5/quickstart_mac.pdf). To test your installation of Gurobi, start a python interpreter and execute the command `import gurobipy`. If there is no import exception, the active subspaces library will be able to use Gurobi.

We had some initial trouble getting the Gurobi Python interface working with Enthought Python; Gurobi formally supports as subset of Python distributions, and Enthought is not one of them. However, we were able to get the interface working by following instructions in this [thread](https://groups.google.com/forum/#!searchin/gurobi/canopy/gurobi/ArCkf4a40uU/R9U1XFuMJEkJ).

# Installation

### The Active Subspaces Package

To install the active subspaces package, open the terminal/command line and clone the repository with the command

```bash
git clone https://github.com/paulcon/active_subspaces.git
```

Navigate into the `active_subspaces` folder (where the `setup.py` file is located) and run the command

```bash
python setup.py install
```

You should now be able to import the active subspaces library in Python scripts and interpreters with the command `import active_subspaces`.

This method was tested on Windows 7 Professional, and Ubuntu 14.04 LTS, and Mac OSX El Capitan with the [Enthought](https://www.enthought.com/) Python distrubution (Python 2.7.11, NumPy 1.10.4, SciPy 0.17.0, and matplotlib 1.5.1).

# Usage

For detailed examples of usage and results, see the Jupyter notebooks contained in the `tutorials/test_functions` and `tutorials/AS_tutorial` directories, the [active subspaces website]
(http://activesubspaces.org/applications/), and the Active Subspaces data sets [repo](https://github.com/paulcon/as-data-sets).

The core class is the Subspaces class contained in the `subspaces.py` file. An instance of this class can compute the active subspace with a variety of methods that take either an array of gradients or input/output pairs. It contains the estimated eigenvalues (and bootstrap ranges), subspace errors (and bootstrap ranges), eigenvalues, and an array of the eigenvectors defining the active subspace. The `utils/plotters.py` file contains functions to plot these quantities and produce summary plots that show model output against the first 1 or 2 active variables. The `utils/response_surfaces.py` file contains classes for polynomial and radial-basis approximations that can be trained with input/output pairs. Both classes can predict the value and gradient at input points and have a coefficient of deterimination (R-squared) value that measures goodness-of-fit. The `integrals.py` and `optimizers.py` files contain functions for integrating and optimizing functions of the active variables; these rely on classes from the `domains.py` file.

# Documentation

Documentation can be found on [ReadTheDocs](http://active-subspaces.readthedocs.io/en/latest/).

# Testing

We are using Travis CI for continusous intergration testing. You can check out the current status [here](https://travis-ci.org/paulcon/active_subspaces).

To run tests locally:

```bash
> python test.py
```
# Community Guidelines

If you have contributions, questions, or feedback, use the [Github repo](https://github.com/paulcon/active_subspaces) or contact 
[*Paul Constantine*](http://inside.mines.edu/~pconstan/).
