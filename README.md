# Setup Instructions for the Hands-On Session on IBR Graphs

These instructions explain how to set up the software needed to run the notebook using the **Anaconda/Miniconda route**.

The notebook requires **SageMath** for symbolic mathematics and **Z3** for feasibility and validity checks. It should be run with a **SageMath Jupyter kernel**, not a standard Python kernel.

## 1. Install Anaconda or Miniconda

If you do not already have Anaconda or Miniconda installed, install one of them first:

- Anaconda: <https://www.anaconda.com/download>
- Miniconda: <https://docs.conda.io/en/latest/miniconda.html>

Miniconda is sufficient and usually the lighter option.

## 2. Create a SageMath Environment

Open a terminal, Anaconda Prompt, or Miniconda Prompt and run:

```bash
conda create -n sage-env -c conda-forge sage python=3.11
```

When prompted, type `y` to proceed.

## 3. Activate the Environment

```bash
conda activate sage-env
```

You should now see `(sage-env)` at the beginning of your terminal prompt.

## 4. Install Jupyter and Z3

With the environment activated, run:

```bash
conda install -c conda-forge jupyterlab notebook z3-solver
```

This installs:

- JupyterLab and Jupyter Notebook
- the Python package `z3-solver`, used by `import z3`

## 5. Start Jupyter

From the same activated environment, run either:

```bash
jupyter lab
```

or:

```bash
jupyter notebook
```

A browser window should open automatically.

## 6. Select the SageMath Kernel

When opening the notebook, make sure the selected kernel is a **SageMath** kernel.

Do **not** use the standard Python kernel, because the notebook uses Sage-specific commands such as:

```python
Integer(...)
ZZ(...)
SR(...)
var(...)
solve(...)
```

These are not available in ordinary Python.

## 7. Test the Installation

Run the following cell in the notebook:

```python
import z3

x = var("x")
y = z3.Real("y")

print("SageMath and Z3 are working.")
```

If this cell runs without errors, the setup is complete.

## Troubleshooting

### `ModuleNotFoundError: No module named 'z3'`

Make sure you activated the correct environment and installed `z3-solver`:

```bash
conda activate sage-env
conda install -c conda-forge z3-solver
```

### `NameError: name 'var' is not defined`

You are probably using a standard Python kernel. Switch the notebook kernel to **SageMath**.

### Jupyter does not show a SageMath kernel

Try starting Jupyter from the activated Sage environment again:

```bash
conda activate sage-env
jupyter lab
```
