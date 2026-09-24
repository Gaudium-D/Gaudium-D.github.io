# Gaudium-D.github.io
This is DSCI 521 Milestone2 and Milestone3


## Project Description

This repository contains a personal website built with Quarto and hosted using GitHub Pages.

The website includes two computational blog posts:

1. **Penguin Body Mass Analysis:** An R-based analysis of body mass differences across three penguin species using the Palmer Penguins dataset.

2. **Iris Petal Length Analysis:** A Python-based analysis of petal length differences across three Iris species using the Iris dataset from scikit-learn.

Both posts contain executable code, summary statistics, visualizations, and explanations of the analysis.

The project uses `uv` to manage Python dependencies and `renv` to manage R dependencies, allowing the computational analyses to be reproduced.

## Prerequisites

Python dependencies are specified in `pyproject.toml` and locked in `uv.lock`.

R dependencies are recorded in `renv.lock`.

The R package `renv` is automatically bootstrapped when the project is opened in R.

## Build Instructions

The following instructions describe how to reproduce the website from a fresh clone of the repository.

### 1. Clone the repository

Open Git Bash or a terminal and run:

```bash
git clone https://github.com/Gaudium-D/Gaudium-D.github.io.git
```

Navigate to the project root directory:

```bash
cd Gaudium-D.github.io
```

All subsequent terminal commands should be executed from this directory unless otherwise specified.

### 2. Set up the Python environment

Install the Python version specified by the project:

```bash
uv sync --locked
```

This command creates the project virtual environment and installs the Python dependencies.

The Python environment includes Jupyter, ipykernel, pandas, matplotlib, and scikit-learn.

The `uv.lock` file records the resolved package versions.

### 3. Set up the R environment

Start R from the project root directory.

```bash
R
```

If R is not available directly from Git Bash, open RStudio and set the working directory to the project root.

Run the following command in the R console:

```r
renv::restore()
```

The project automatically bootstraps `renv` through `.Rprofile` and `renv/activate.R`.

The `renv::restore()` command installs the R packages recorded in `renv.lock`.

These packages include `palmerpenguins`, `dplyr`, and `ggplot2`.

Once the environment has been restored, verify its status:

```r
renv::status()
```

Exit the R console:

```r
q()
```

If prompted to save the workspace, select "No".


### 4. Render the website

Return to Git Bash or your terminal.

Make sure you are in the project root directory.

Run:

```bash
uv run --locked quarto render
```

This command renders the entire Quarto website using the project's Python environment.

The R code is executed using the project's renv environment.

### 5. View the website locally

After rendering, the generated website is located in:

```text
docs/
```

Open the following file in a web browser:

```text
docs/index.html
```

Alternatively, start a local preview from the project root:

```bash
uv run --locked quarto preview
```

Open the local URL displayed by Quarto in your browser.

The published website is available at:

https://gaudium-d.github.io/

## Data Sources

### Palmer Penguins

The R blog uses the Palmer Penguins dataset, available through the `palmerpenguins` R package.

Source: https://allisonhorst.github.io/palmerpenguins/

The dataset contains measurements of Adelie, Chinstrap, and Gentoo penguins.

The dataset is distributed under the CC0 license.

The R analysis loads the dataset directly from the installed R package. No separate data file needs to be downloaded.

### Iris Dataset

The Python blog uses the Iris dataset bundled with scikit-learn.

Source: https://scikit-learn.org/stable/datasets/toy_dataset.html#iris-plants-dataset

The dataset contains measurements of three Iris species: Setosa, Versicolor, and Virginica.

The analysis loads the dataset using `sklearn.datasets.load_iris()`.

No separate data file needs to be downloaded.


## Repository Structure

```text
Gaudium-D.github.io/
├── _quarto.yml
├── README.md
├── index.qmd
├── about.qmd
├── blog.qmd
├── pyproject.toml
├── uv.lock
├── styles.css
├── .python-version
├── renv.lock
├── .Rprofile
├── renv/
│   └── activate.R
├── posts/
│   ├── first-weeks/
│   │   └── index.qmd
│   ├── penguin-analysis/
│   │   └── index.qmd
│   └── iris-analysis/
│       └── index.qmd
├── images/
│   └── Chizuru_Hishiro2.jpg
└── docs/
    ├── about.html
    ├── blog.html
    ├── index.html
    ├── .nojekyll
    ├── images/
    ├── posts/
    │   ├── first-weeks/
    │   │    ├──index.qmd
    │   │    └──orientation_day.jpg
    │   ├── iris-analysis/
    │   │    ├──index.qmd
    │   │    └──index_files/
    │   │       └──figure-html/
    │   │           └──fig-iris-petal-length-output-1.png
    │   └── penguins-analysis/
    │        ├──index.qmd
    │        └──index_files/
    │           └──figure-html/
    │               └──fig-penguin-mass-1.png
    └── site_libs/
```

The `posts/` directory contains the source files for the computational blog posts.

The `docs/` directory contains the rendered website used by GitHub Pages.

The `.venv/` directory and the local R package library are excluded from version control.

## Reproducibility

The project uses two separate dependency management systems:

- Python dependencies are managed with `uv` and locked in `uv.lock`.
- R dependencies are managed with `renv` and locked in `renv.lock`.

The website can be rebuilt by restoring both environments and running the Quarto rendering command from the repository root.