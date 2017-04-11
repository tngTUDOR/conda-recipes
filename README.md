# Conda recipes for Brightway and some of my other code

Uses tips and tricks from [Adrian Haas](https://github.com/haasad/brightway2-conda-recipes).

Created originally using `conda skeleton pypi brightway2`, but then modified manually.

Uses `script: python setup.py install --single-version-externally-managed --record record.txt` to avoid pip re-installing things.

Uses Jinja2 variables the same way that [conda-forge does](https://github.com/conda-forge/staged-recipes/blob/master/recipes/example/meta.yaml).

Get SHA256 values from the [pypi warehouse](https://pypi.org/project/brightway2/#files).
