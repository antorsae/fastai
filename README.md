# Welcome to fastai
> fastai simplifies training fast and accurate neural nets using modern best practices


[![CI-Badge](https://github.com/fastai/fastai/workflows/CI/badge.svg)](https://github.com/fastai/fastai/actions?query=workflow%3ACI) [![PyPI](https://img.shields.io/pypi/v/fastai?color=blue&label=pypi%20version)](https://pypi.org/project/fastai/#description) [![Conda (channel only)](https://img.shields.io/conda/vn/fastai/fastai?color=seagreen&label=conda%20version)](https://anaconda.org/fastai/fastai) [![Build fastai images](https://github.com/fastai/docker-containers/workflows/Build%20fastai%20images/badge.svg)](https://github.com/fastai/docker-containers)

To learn more about the design and motivation of the library, read the [peer reviewed paper](https://arxiv.org/abs/2002.04688).

Note that the docs are in a submodule, so to clone with docs included, you should use:

     git clone --recurse-submodules https://github.com/fastai/fastai

## Installing

You can install fastai with conda (highly recommended; requires [Anaconda](https://www.anaconda.com/products/individual) or [miniconda](https://docs.conda.io/en/latest/miniconda.html): `conda install -c fastai -c pytorch fastai`, or with pip: `pip install fastai`. If you install with pip, you should install PyTorch first by following the PyTorch [installation instructions](https://pytorch.org/get-started/locally/).

Or if you plan to develop fastai yourself, or want to be on the cutting edge, you can use an editable install (if you do this, youu should also use an editable install of [fastcore](https://github.com/fastai/fastcore) to go with it.):

``` 
git clone --recurse-submodules https://github.com/fastai/fastai
cd fastai
pip install -e ".[dev]"
``` 

If you want to browse the notebooks and build the library from them you will need nbdev, which you can install with conda or pip.

To use `fastai.medical.imaging` you'll also need to:

```bash
conda install pyarrow
pip install pydicom kornia opencv-python scikit-image
```

## Tests

To run the tests in parallel, launch:

`nbdev_test_nbs` or `make test`

For all the tests to pass, you'll need to install the following optional dependencies:

```
pip install "sentencepiece<0.1.90" wandb tensorboard albumentations pydicom opencv-python scikit-image pyarrow kornia
```

Tests are written using `nbdev`, for example see the documentation for `test_eq`.

## Contributing

After you clone this repository, please run `nbdev_install_git_hooks` in your terminal. This sets up git hooks, which clean up the notebooks to remove the extraneous stuff stored in the notebooks (e.g. which cells you ran) which causes unnecessary merge conflicts.

Remember that fastai uses [Git submodules](https://git-scm.com/docs/gitsubmodules), so you have to include the flag `--recurse-submodules` in some of your Git commands (`git clone`, `git pull`). Alternatively, you can set the Git configuration option (since Git 2.15):

```
git config --local submodule.recurse true
```

Before submitting a PR, check that the local library and notebooks match. The script `nbdev_diff_nbs` can let you know if there is a difference between the local library and the notebooks.

- If you made a change to the notebooks in one of the exported cells, you can export it to the library with `nbdev_build_lib` or `make fastai`.
- If you made a change to the library, you can export it back to the notebooks with `nbdev_update_lib`.

## Docker Containers

For those interested in offical docker containers for this project, they can be found [here](https://github.com/fastai/docker-containers#fastai).
