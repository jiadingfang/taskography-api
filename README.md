# taskography-api
A simple API for sampling symbolic planning tasks in large-scale 3D scene graphs.

![Taskography-API System Diagram](figures/taskography-api-system.png)

---


## Overview
This repository corresponds to Taskography-API as described in *Taskography: Evaluating robot task planning over large 3D scene graphs*, presented at CoRL2021: [project page](https://taskography.github.io/), [paper link](https://www.chrisagia.com/papers/Taskography-CoRL-2021.pdf). We provide support for the following:

- **Hierarchical-Symbolic Graph Construction.** 
The raw [Gibson](https://3dscenegraph.stanford.edu/database.html) scene graph data is [loaded](https://github.com/taskography/taskography-api/blob/main/taskography_api/taskography/utils/loader.py#L8) from its `.npz` file format encoding before [heuristically](https://github.com/taskography/taskography-api/blob/main/taskography_api/taskography/samplers/task_sampler_base.py) determining the scene's inter- and intra-layer connectivity structure.
- **Task Sampling.** [Problem samplers](https://github.com/taskography/taskography-api/tree/main/taskography_api/taskography/samplers/domains) for auto-generating [PDDLGym](https://github.com/tomsilver/pddlgym) domains of increasing complexity: `Rearrangement(k)`, `Courier(n,k)`, `Lifted Rearrangement(k)`, `Lifted Courier(n,k)`, as described in our paper. Task samplers are modifiable to the degree literal goal conjuctions (k), and for Courier domains, stow capacity (n).
- **Trajectory Sampling.** Scripts for generating state-action trajectory datasets atop PDDLGym environments with your choice of [PDDL planner](https://github.com/agiachris/pddlgym_planners); for purposes of training neurosymbolic learning-to-plan algorithms.
- **Environment Wrappers.** 
Gym wrappers enabling symbolic interaction with 3D scene graphs - in support of online decision making algorithms and reinforcement learning methods. 


## Setup

### System Requirements
This repository has been primarily tested on Ubuntu 16.04, 18.04 and macOS Monterey with Python 3.6. 

### Installation 
One of our package dependencies requires Docker - please follow [these steps](https://docs.docker.com/engine/install/) to install it. We also recommend creating a virtual environment, e.g. with [venv](https://docs.python.org/3/library/venv.html) or [anaconda3](https://anaconda.org/) before proceeding with the following installation steps. 

```bash
# if on macOS
brew install coreutils

git clone https://github.com/taskography/taskography-api.git --recurse-submodules
cd ./taskography_api && pip install .
```


## Instructions 
General instructions

### Basic Usage
Add simple usage examples.


### Extended Usage
Add tips for extended usage.


## Citation
Taskography-API has an MIT [License](https://github.com/taskography/taskography-api/blob/main/LICENSE). If you find this package helpful, please consider citing our work:

```
@inproceedings{agia2022taskography,
  title={Taskography: Evaluating robot task planning over large 3D scene graphs},
  author={Agia, Christopher and Jatavallabhula, Krishna Murthy and Khodeir, Mohamed and Miksik, Ondrej and Vineet, Vibhav and Mukadam, Mustafa and Paull, Liam and Shkurti, Florian},
  booktitle={Conference on Robot Learning},
  pages={46--58},
  year={2022},
  organization={PMLR}
}
```


## References
We would like to credit the developers of several very useful packages.

- [1] "PDDLGym: Gym Environments from PDDL Problems," Tom Silver, Rohan Chitnis, [link](https://github.com/tomsilver/pddlgym) to repository.
- [2] "PDDLGym Planners: Lightweight Python interface for using off-the-shelf classical planners," Tom Silver, Rohan Chitnis, [link](https://github.com/ronuchit/pddlgym_planners) to repository.