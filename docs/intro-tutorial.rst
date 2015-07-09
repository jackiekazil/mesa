Introduction to Mesa - Tutorial
================================

Getting started with Mesa is easy. In this doc, we will present Mesa’s
architecture and core features. To illustrate their use, we will describe and build a simple agent-based model, drawn from econophysics and presenting a statistical mechanics approach to wealth distribution [Dragulescu2002]_.

The rules of our tutorial model:

- There are some number of agents.
- All agents begin with 1 unit of money.
- Every step fo the model, an agent gives 1 unit of money (if they have it) to some other agent.

Despite its simplicity, this model yields results that are often unexpected to those not familiar with it. For our purposes, it also easily demonstrates Mesa's core features.

Let's get started.


Installation
------------

The first thing you need to do is to install Mesa. We recommend doing this in a `virtual environment`_. Make sure your work space is pointed to Python3. Mesa requires Python3 and does not work in < Python3 environments.

To install Mesa, simply:

.. code-block:: bash

    $ pip install mesa

When you do that, it will install the following packages and dependencies.

- mesa
- tornado
- numpy
- pandas


Overview of Modules
------------

There are three module types in Mesa.

1. modeling
2. analysis
3. visualization

TODO: Insert image


Modeling module
~~~~~~~~~~~~~~

To build a model, you need the following:

* **Model class** to store the model-level parameters and serve as a container for the rest of the components

* **Agent class(es)** which describe the model agents

* **Scheduler** which controls the agent activation regime, and handles time in the model in general

* **space** components describing the space and/or network the agents are situated in


Analysis modules
~~~~~~~~~~~~~~

* Data collectors use to record data from each model run
* Batch runners for automating multiple runs and arameter sweeps


Visualization modules
~~~~~~~~~~~~~~

* displays model in a browser window in various ways
* displays model as grid
* displays model graphs
* displays model controls



Building a sample model
------------

Now that we understand a little bit about the components,let's use those components to build a model. To begin building the example model described at the top of this page -- we first *create two classes: one for the model object itself and one the model agents*.

**Agent**

In our example, each agent has a single ...

* variable: How much money it currently has
* action: Give a unit of money to another agent

.. code-block:: python

    from mesa import Model, Agent

    class MoneyAgent(Agent):
        """ An agent with fixed initial wealth."""
        def __init__(self, unique_id):
            self.unique_id = unique_id                   # 1.
            self.wealth = 1

    class MoneyModel(Model):
        """A model with some number of agents."""
        def __init__(self, N):
             self.num_agents = N
             # The scheduler will be added here
             self.create_agents()

        def create_agents(self):
            """Method to create all the agents."""
            for i in range(self.num_agents):
                a = MoneyAgent(i)
                # Now what? See below.

1. Each agent should have a unique identifier, stored in the ``unique_id`` field.




** THIS DOC IS IN PROGRESS **




.. _`virtual environment`: http://docs.python-guide.org/en/latest/dev/virtualenvs/

.. [Dragulescu2002] Drăgulescu, Adrian A., and Victor M. Yakovenko. “Statistical Mechanics of Money, Income, and Wealth: A Short Survey.” arXiv Preprint Cond-mat/0211175, 2002. http://arxiv.org/abs/cond-mat/0211175.



