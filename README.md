## Conda recipes ##

This repository contains the [conda](https://conda.anaconda.org/trigfa) build recipes for a few packages I find useful.

### Build instructions

First you need anaconda-client and anaconda-build installed:

``` bash
conda install anaconda-client conda-build

```

Then clone the repository:

``` bash
git clone git@github.com:trigfa/conda_recipes.git

cd conda_recipes
cd <required package to build>

```
Switch off automatic upload to anaconda cloud and then build the package

``` bash


conda config --set anaconda_upload no
conda build .

```
The built packages built in are placed in a subdirectory of Anaconda's conda-bld directory. You can check where the resulting file was placed with the --output option:

``` bash
conda build . --output
```
Upload the files to the anaconda cloud using the command:

``` bash
anaconda login
anaconda upload /path/to/conda-package.tar.bz2
```
To build for other platforms you can use:

``` bash
conda convert --platform all /path/to/conda-package.tar.bz2
```
This will create directories named "win-32", "osx-64" etc. cd into each directory and then upload the .tar.bz2 file contained in each using:

```bash
anaconda upload ./conda-package.tar.bz2
```
