# DLPS-Final-Project
Study on Enforcing Symmetry in Physics-Informed Neural Networks: A Lie Theory Perspective
# Abstract
Physics-Informed Neural Networks (PINNs) embed governing physical laws di-
rectly into the training loss, enabling mesh-free solutions to partial differential
equations (PDEs). When a problem exhibits continuous rotational symmetry —
as is the case for PDEs posed on concentric annuli with uniform boundary con-
ditions — standard PINNs provide no intrinsic mechanism to exploit it. This
work investigates four symmetry-enforcement strategies grounded in Lie theory
across two benchmark problems: the steady-state heat (Laplace) equation and
the Helmholtz equation, both on concentric annuli. The four strategies are: (1)
a full-domain baseline with no constraint, (2) a quarter-domain formulation with
Neumann boundary conditions on cut faces, (3) a quarter-domain formulation
with a Lie-derivative soft penalty, and (4) full-domain architectural encoding
via 4-fold reflection averaging. For the heat equation, architectural encoding
achieves the best accuracy (relative L2 error of 0.0018%) and the quarter-domain
approaches reduce training time by ∼44%. For the Helmholtz equation, the stan-
dard tanh network failed regardless of network size due to gradient vanishing in
the second-order PDE loss. Replacing tanh with sinusoidal activations (SIREN)
resolved this and reduced the error from ∼4% to ∼0.85% across all approaches.
However, the PDE residual still stalls at a flat basin, and L-BFGS provides no fur-
ther improvement, indicating a persistent optimisation pathology specific to the
Helmholtz operator. These results demonstrate that symmetry enforcement and
activation function design are complementary requirements, and that the stan-
dard Adam + L-BFGS pipeline is insufficient for the Helmholtz equation even
with an appropriate activation function.


## Overview
This repository investigates symmetry-enforcement strategies in Physics-Informed Neural Networks (PINNs) using Lie theory. The study focuses on solving the steady-state heat (Laplace) and Helmholtz equations on concentric annuli, comparing different methods for exploiting rotational symmetry.

## Environment
The notebooks are designed and tested to run in **Google Colab**. All required dependencies are installed within the first cell of each notebook.

## Project Structure

The project is divided into two main directories based on the governing equations studied. Both studies explore the four strategies described in the abstract (Full-domain baseline, Quarter-domain Neumann, Quarter-domain Lie-derivative, and Architectural Encoding).

### 1. Heat Equation (Laplace)
**Folder:** `SourceCode_HeatEquation`

This folder contains four separate `.ipynb` files, one for each specific symmetry-enforcement study:
* `Heat_FullDomain.ipynb`
* `Heat_Quarter_Neumann.ipynb`
* `Heat_Quarter_Lie.ipynb`
* `Heat_Architectural_Encoding.ipynb`

### 2. Helmholtz Equation
**Folder:** `SourceCode_HelmholtzEquation`

The Helmholtz study is contained within a **single `HelmzPINNs.ipynb` file**. This notebook is interactive and includes all four symmetry cases, which can be toggled via options within the code.

## Usage

1. **Upload:** Open the desired notebook from the folders above in **Google Colab**.
2. **Execute:** Run the cells in order.
3. **Configuration:** For the Helmholtz notebook, ensure you select the specific study case or activation function you wish to test in the configuration section of the code.

---
