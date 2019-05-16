# scHypoth_e15-p23
==============================

Explore hypothalamic cell lineages dynamics and trajectories with scRNA-seq (10X) and CreERT2 knock-in mouse model for lineage tracing.

## Project Organization
--------------------

    .
    ├── AUTHORS.md
    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data`
    │                         or `make train`
    ├── README.md          <- The top-level README for developers using
    │                         this project.
    ├── config.yaml
    ├── _workflowr.yml
    ├── analysis
    │   └── _site.yml
    ├── bin
    ├── binder
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org
    │                         for details
    ├── envs
    │
    ├── models             <- Trained and serialized models, model predictions,
    │                         or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number
    │                         (for ordering), the creator's initials,
    │                         and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── R
    ├── references         <- Data dictionaries, manuals, and all other
    │                         explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in
    │                         reporting
    │
    ├── requirements.txt   <- The requirements file for reproducing
    │                         the analysis environment, e.g.
    │                         generated with `pip freeze > requirements.txt`
    ├── rules
    │
    ├── setup.py           <- makes project pip installable (pip install -e .)
    │                         so src can be imported
    ├── Snakefile
    ├── src                <- Source code for use in this project.
    │   ├── __init__.py    <- Makes src a Python module
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   ├── make_dataset.py
    │   │   └── Snakefile
    │   │
    │   ├── features       <- Scripts to turn raw data into features for
    │   │                     modeling
    │   │   └── build_features.py
    │   │
    │   ├── models         <- Scripts to train models and then use trained
    │   │   │                 models to make
    │   │   │                 predictions
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization  <- Scripts to create exploratory and results
    │       │                 oriented visualizations
    │       └── visualize.py
    │
    └── tox.ini            <- tox file with settings for running tox;
                              see tox.testrun.org



# R + Python Binder Template

This repo builds on the [r binder](https://github.com/binder-examples/r) and [jupyter lab binder](https://github.com/binder-examples/jupyterlab) and is complementary to the [multi-language-demo binder](https://github.com/binder-examples/multi-language-demo) with examples on using both R and python in both Jupyter Lab and RStudio.

 - Launch in Jupyter Lab: [![Binder](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/binder-examples/r_with_python/master?urlpath=lab)
 - Launch in RStudio: [![Binder](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/binder-examples/r_with_python/master?urlpath=rstudio)

Example files included:

 - `python_example_for_Jupyter.ipynb` - Notebook file using a python kernel for working in Jupyter
 - `R_example_for_Jupyter.ipynb` - Notebook file using an R kernel for working in Jupyter
 - `python_example_for_RStudio.Rmd` - RMarkdown file with python code chunks for working in RStudio
 - `R_example_for_RStudio.Rmd` - RMarkdown file with R code chunkcs for working in RStudio

Note: to mix R and python in a single Jupyter notebook, use cell magic as demonstrated in the [multi-language-demo](https://github.com/binder-examples/multi-language-demo) binder examples. To mix R and python in a single RMarkdown file (and exchange information between them), make use of [reticulate](https://rstudio.github.io/reticulate/). The latter requires [RStudio 1.2+](https://www.rstudio.com/products/rstudio/download/preview/) to work interactively, which is not yet installed as the default binder version (i.e. interactive python and python plots will not yet work in RMarkdown and the above example file uses reticulate for plotting in the knitted file).

## Binder Setup

Modify the files in the `binder` sub-directory to specify required dependencies for R and python. Binder will generate a docker image for your repository after every change to the repo and then will re-use the docker image on subsequent launches. This means that the first time you launch binder for the latest version of your branch, it may take some time to launch (especially with a lot of R dependencies which are all compiled from source) but will be fast for everyone else afterwards. Switching between `RStudio` vs. `Jupyter Lab` as the IDE is accomplished easily by changing the binder link as described below - the required dependencies for both are automatically installed and do not need to be explicitly listed in the respective configuration files.

**Important**: binder will *only* work for public repositories. If your repository is private, you will have to make it public in the repository settings before you can launch it in binder.

### R
 - modify the `binder/runtime.txt` file to specify which R date snapshot should be used (the [MRAN](https://mran.microsoft.com/documents/rro/reproducibility) network keeps a daily snapshot)
 - modify the `binder/install.R` file to make sure all dependencies are specified. Dependencies can be from CRAN, bioconductor or GitHub. Since GitHub hosted libraries are not part of the MRAN snapshot, it is best to specify a commit or release tag to ensure that a compatible version of the package is installed in the binder.

### Python

 - modify the `binder/environment.yml` file to specify the dependencies. The file is a standard [conda environment config file](https://conda.io/docs/user-guide/tasks/manage-environments.html#create-env-file-manually) and thus supports conda packages, version definitions, multiple source channels as well as pip installations.
 - modify the `binder/postBuild` file for any JupyterLab extensions or other direct install commands

## Binder Link

### Jupyter Lab

 - modify the following link to launch your repo in an RStudio binder (`USER`, `REPO`, `BRANCH`): `http://mybinder.org/v2/gh/USER/REPO/BRANCH?urlpath=lab`
 - modify the following markdown code to create a launch badge like the one at the top this README: `[![Binder](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/USER/REPO/BRANCH?urlpath=lab)`

### RStudio

 - modify the following link to launch your repo in an RStudio binder (`USER`, `REPO`, `BRANCH`): `http://mybinder.org/v2/gh/USER/REPO/BRANCH?urlpath=rstudio`
 - modify the following markdown code to create a launch badge like the one at the top of this README: `[![Binder](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/USER/REPO/BRANCH?urlpath=rstudio)`

--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>
