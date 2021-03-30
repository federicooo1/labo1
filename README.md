# Development

Clone this repository.

Create a conda environment with:
> conda env create -f environment.yaml
which creates a `book` environment with all dependencies.

Activate environment with:
> conda activate book

If Jupyter is installed in a different environment, install kernel with:
> ipython ipython kernel install --name "book" --user

To convert a .ipynb file to MyST format:
> jupytext mynotebook.ipynb --to myst

To add MyST metadata to a markdown file:
> jupyter-book myst init mymarkdown.md --kernel book

Only commit MyST notebooks, or markdown files if they include no executable code, to the git repository.
