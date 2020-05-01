---
title: 'Installation & Updating'
weight: 10
---
# Installation & Updating

There are two ways to install the LaTeX packages for use in your next scientific contribution.
If you are not too familiar with LaTeX's internal workings, then you probably will want to choose the [basic installation](#basic-installation) method.
For more advanced LaTeX users or those who want to install the LaTeX packages globally, the [advanced installation](#advanced-installation) is the preferred method.


## Basic Installation

To install the LaTeX packages, you simply need to download the most recent release from our [releases page](https://gitlab.com/cable-robots/latex/-/releases) or form the [CI/CD build arifacts](https://gitlab.com/cable-robots/latex/-/jobs/artifacts/master/download?job=dist) and unpack it into your working directory.
Then, use the packages as you would normally use a package in any LaTeX document.
Refer to [Order of Loading Packages](#order-of-loading-packages) to see in which order packages should be loaded in.

## Advanced Installation

It can be cumbersome to add the packages to the directory of each document you are working on.
Not only does it cause a high level of redundancy, it is also a pain to keep the documents up to date.
For this reason, we recommend you to copy the style files downloaded form a release on our GitLab server and move them to a TeX-searched directory.
If your system has `make`, then read the section on [Automatic Installation](#automatic-installation), else you will need to perform the [Manual Installation](#manual-installation)


### Manual Installation

Download the most recent release from our releases page on GitLab (see [Basic Installation](#basic-installation) for that).
Then, open a command line window and type in

```bash
$ kpsewhich --var-value TEXMFHOME
```

Note the value of this directory and navigate into it using your preferred method.
Within the directory, navigate to `tex/latex` and create a new directory called `cablerobot`

```bash
$ cd `(kpsewhich --var-value TEXMFHOME)`/tex/latex
$ mkdir cablerobot
```

Copy all `.sty` files into this directory.
You should now be ready to use the packages in any LaTeX document without any additional steps.


### Automatic Installation

First, clone the repo and change into the directory
```bash
$ git clone https://gitlab.com/cable-robots/latex
$ cd latex
```

Then, simply build the make target `install`

```bash
$ make install
```

If you do not see any errors, you have successfully installed all cable robot packages into your local TeX environment.


## Order of Loading Packages

Since some packages depend on others, the recommended loading order is given below.

```latex
\usepackage{cablerobot-colors}
\usepackage{cablerobot-math}
\usepackage{cablerobot-symbols}
\usepackage{cablerobot-mechanics}
\usepackage{cablerobot-text}
\usepackage{cablerobot-acronyms}
```


## Updating

If you downloaded a release or installed the files manually into your `texmf` directory, simply get a new release and follow the steps in the [Manual Installation](#manual-installation)

If you cloned the repository and have `make` available on your system, you simply need to pull in the most recent updates and install them to your local TeX environment.
Just run the following commands in your local command line in the directory of your clone

```bash
$ git pull oriign master
$ make install
```
