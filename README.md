# Conda recipes for Brightway and some of my other code

Uses tips and tricks from [Adrian Haas](https://github.com/haasad/brightway2-conda-recipes).

Created originally using `conda skeleton pypi brightway2`, but then modified manually.

Uses `script: python setup.py install --single-version-externally-managed --record record.txt` to avoid pip re-installing things.

Uses Jinja2 variables the same way that [conda-forge does](https://github.com/conda-forge/staged-recipes/blob/master/recipes/example/meta.yaml).

Get SHA256 values from the [pypi warehouse](https://pypi.org/project/brightway2/#files).

## Conda fun and frustration

- voluptuous is need because there isn't a 3.6 release in conda-forge yet outside of Linux
- future is needed because conda-forge doesn't build a 3.6 version of future 0.15.2, which is required by eight
- eight is needed because it doesn't yet build cleanly on conda-forge
- Conda-forge only support conda 4.2, but noarch python builds require 4.3. If you are not careful you will get the wrong one and be completely confused as to why things don't work anymore.
- Somehow installing my packages makes conda think they were installed by pip:

    (install-test) emerson:~ cmutel$ conda install -c conda-forge -c cmutel -c haasad bw2calc
    Fetching package metadata ...............
    Solving package specifications: .

    Package plan for installation in environment /Users/cmutel/miniconda3/envs/install-test-6:

    The following NEW packages will be INSTALLED:

        bw2calc:      1.6.1-py_2         cmutel
        eight:        0.3.3-py_0         haasad
        future:       0.16.0-py36_0      conda-forge
        mkl:          2017.0.1-0
        nose:         1.3.7-py36_2       conda-forge
        numpy:        1.12.1-py36_0
        scipy:        0.19.0-np112py36_0
        stats_arrays: 0.4.1-py_3         cmutel

    Proceed ([y]/n)?

    (install-test) emerson:~ cmutel$ conda list | grep bw
    bw2calc                   1.6.1                      py_2    cmutel
    bw2calc                   1.6.1                     <pip>

I am not even sure that this is possible, much less correct - we are installing with `--single-version-externally-managed`, which I thought would ignore requirements in `setup.py`. Much hilarity ensued...
