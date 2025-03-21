# How to install sageMath on linux (Ubuntu) ?

### 1. Install a <code>conda</code> Installation ([miniforge](https://github.com/conda-forge/miniforge)):
Example for <code>uname=Linux</code> and <code>uname -m=x86_64</code>, read more about [versions](https://github.com/conda-forge/miniforge).
  1. Use <code>curl</code> or <code>wget</code>:
```
curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```

```
wget "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
```
  2. Run the install script with:
```
bash Miniforge3-$(uname)-$(uname -m).sh
```


### 2. Clone <code>sage</code> repo ([sagemath](https://doc.sagemath.org/html/en/installation/conda.htmlhttps://github.com/conda-forge/miniforge)):
```
git clone https://github.com/sagemath/sage.git && cd sage
```

### 3. setup for build sage lib:
1. Optionally, set the build parallelism for the Sage library. Use whatever the meaningful value for your machine is - no more than the number of cores:
```
export SAGE_NUM_THREADS=24
```

2. Create and activate a new conda environment with the dependencies of Sage and a few additional developer tools:
```
conda env create --file environment-dev-3.11-linux.yml --name sage-dev
conda activate sage-dev
```

### 4. build sage lib:
Bootstrap the source tree and install the build prerequisites and the Sage library:
```
./bootstrap
pip install --no-build-isolation --config-settings editable_mode=compat -v -v --editable ./src
```

### 5. Verify that Sage has been installed:
```
sage -c 'print(version())'
SageMath version 10.2.beta4, Release Date: 2023-09-24
```
### 6. (opt) Install JupyterLab with pip:
```
pip install jupyterlab
```
To start JupyterLab:
```
jupyter lab
```
### 7. Install the classic Jupyter Notebook:
```
pip install notebook
```
To run the notebook:
```
jupyter notebook
```
## Read offical doc by problems and issues:
- conda: https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html
- miniforge: https://github.com/conda-forge/miniforge
- sagemath: https://doc.sagemath.org/html/en/installation/conda.htmlhttps://github.com/conda-forge/miniforge
- jupyter: https://jupyter.org/install
