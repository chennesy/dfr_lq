# dfr_lq

topic modeling library quarterly

## Unfinished

* Work in progress using LDA topic modeling on Library Quarterly articles via JSTOR DFR.
* Code unfinished. Documentation incomplete.

## Install system library dependencies

### Mac

### Ubuntu

```bash
apt install build-essential libxml2-dev libcurl4-openssl-dev
```

## anyenv

We use [anyenv](https://github.com/anyenv/anyenv) to install Python and (optionally) node.js, to
keep the languages we use for this project separate from any system languages installed by the local OS.
The files `.node-version` and `.python-version` specify which version of these languages we use for
this project.

## nodenv or ndenv

Installing node.js is optional, but JuptyerLab will noisily complain if it is not installed. We
use either [nodenv](https://github.com/nodenv/nodenv) or [ndenv](https://github.com/riywo/ndenv).

## pyenv, venv, and poetry 

To install and manage Python versions we use [pyenv](https://github.com/pyenv/pyenv), and to manage
dependencies we use [poetry](https://poetry.eustace.io/). While alternative tools will work, we document
here only the tools we use. We will document the use of other tools if demand arises.

One way to set up all these tools to work together, for a new project, is to follow the workflow below.
Note that we prefer to put virtual environments inside the project directory. Note also that we use the
built-in `venv` module to create virtual environments, and we name their directories `.venv`, because
that is what `poetry` does and expects.

* Install pyenv.
* `pyenv install $python_version`
* `mkdir $project_dir; cd $project_dir`
* Create a `.python-version` file, containing `$python_version`.
* `pip install poetry`
* `poetry config virtualenvs.in-project true`
* `poetry install` (Or should this be `poetry update`? Does it matter?)
* `source ./.venv/bin/activate`

Now running commands like `poetry install` or `poetry update` should install packages into the virtual
environment in `./.venv`. Don't forget to `deactivate` the virtual environment when finished using it.
If the project virtual environment is not activated, `poetry run` and `poetry shell` will activate it.
When using `poetry shell`, exit the shell to deactivate the virtual environment.

We even install `jupyterlab` via `poetry`. So to start Jupyter in the right virtual environment, run it
in the `$project_dir`, after activating its virtual environment, as described above: `jupyter lab`

## R

What follows are instructions for first-time setup of an R environment for this project. These
need additional instructions for setup of the project after we add the packrat files (see below).

### Install R

There is no rbenv-style installer for R, and thus no anyenv support. Instead, install R according to 
these instructions:

* [Linux](https://cran.r-project.org/bin/linux/)
* [Mac](https://cran.r-project.org/bin/macosx/)

### packrat for R package management

We use [packrat](https://rstudio.github.io/packrat/) (similar to poetry for Python) to install R packages
in the project directory, to prevent conflicts with any other R packages installed on the machine. From
the CLI in the project directory, run `R` to start an R session. Then install and initialize packrat:

```R
install.packages('packrat')
packrat::init()
```

It may also be necessary to ensure that packrat mode is on when installing packages:

```R
packrat::on()
```

#### Install IRKernal for JupyterLab

Still in the R session, install [IRkernel](https://irkernel.github.io/installation/) (an R kernel) for JupyterLab:

```R
install.packages('IRkernel')
IRkernel::installspec()
```

#### Install other R packages

Again in the R session, install R package dependencies:

```R
install.packages('jstor')
install.packages('tidyverse')
```

#### Take a snapshot

This will update `packrat/packrat.lock` with version information for each package installed, and put the source code
for all packages in `packrat/src/`:

```R
packrat::snapshot()
```
