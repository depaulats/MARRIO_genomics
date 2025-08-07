# Intalling Miniconda

"[Miniconda](https://www.anaconda.com/docs/getting-started/miniconda/main) is a free, miniature installation of Anaconda Distribution that includes only conda, Python, the packages they both depend on, and a small number of other useful packages."

Installing it is simple. Just run the commands below to download the latest version and run the installation (which will be deleted afterwards).

```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh
```

After that you need to close and reopen your terminal application to then initialize conda on all available shells by running:

```
conda init --all
```

Now your shell will be set on the `(base)` environment, which you should not use for installing packages to avoid generating conflicts with default softwares (e.g. Python).

## Managing environments

"With [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html), you can create, export, list, remove, and update environments that have different versions of Python and/or packages installed in them."

### Creating an environment

```
conda create --name your-environment
```

When conda asks you to proceed, type `y`.

### Activating an environment

To activate `(your-environment)`:

```
conda activate your-environment
```

### Deactivating an environment

To return to `(base)`:

```
conda deactivate
```

### Removing an environment

To remove `your-environment` from you computer and all packages in it: 

```
conda remove --name your-environment --all
```

To check if `your-environment` was removed, and all others still in your system run:

```
conda info --envs
```

To install packages in an environment you can do it during its creation or after activating an existing one.

Conda suggests you to install all the programs at the same time to avoid dependency conflicts. However we are not going to individually install the programs we need, but software packages curated and depositted in a repository, such as [Bioconda](https://bioconda.github.io/).

To install packages with Bioconda first you need to perfomr a one-time set up:

```
conda config --add channels bioconda
conda config --add channels conda-forge
conda config --set channel_priority strict
```

Then you can activate `your-environment` and install `your-package`:

```
conda activate your-environment
conda install bioconda::your-package
```

You you know which package you are looking for, you can just search their names in any search engine find anything you might need, including the terms "github" or "bioconda" in the search.

Otherwise you can follow the [tutorials](https://github.com/depaulats/MARRIO_genomics/blob/main/tutorials.md).

In the next step you will find [how to download NGS data](https://github.com/depaulats/MARRIO_genomics/blob/main/seq_dump.md).
