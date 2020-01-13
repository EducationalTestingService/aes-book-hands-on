# Introduction

This repository contains resources for the hands-on exercises that are included in Chapter 3 the Morgan Claypool book on _Automated Essay Scoring_ by [Beata Beigman Klebanov](https://sites.google.com/site/beatabeigmanklebanov/) and [Nitin Madnani](https://desilinguist.org).

# What's here

In the book, we used [RSMTool](https://github.com/EducationalTestingService/rsmtool) to build machine learning models to automatically score the essays from the [Automated Student Assessment Prize (ASAP)](https://www.kaggle.com/c/asap-aes) competition – specifically essays from writing tasks 1 and 2.  This repository contains the data, the features, and the RSMTool configuration files that are used in the book.

# Structure

The repository has the following structure:

```
├── data
│   ├── essays
│   ├── features
│   └── rubrics
├── environment.yaml
└── experiments
    ├── 00-all-features
    ├── 01-all-fair-features
    ├── 02-remove-collinear-feature
    ├── 03-remove-insignificant-features
    ├── 04-transform-features
    ├── 05-percent-func-feature
    ├── 06-evaluate-on-heldout-data
    ├── 07-evaluate-on-task-2
    ├── 08-task-2-specific-model
    ├── 09a-train-and-test-on-average-score
    ├── 09a-train-and-test-on-average-score-task2
    ├── 09b-only-test-on-average-score
    ├── 09b-only-test-on-average-score-task2
    └── 10-different-learner
```

The [`data`](data) directory contains: (a) the scoring guidelines or [`rubrics`](data/rubrics) for ASAP writing tasks 1 and 2 (b) the [`essays`](data/essays) from the tasks – split into a training set, a development set, and a test set (b) the [`features`](data/features) extracted from the essays in each of the three datasets to be used for building the automated scoring models via RSMTool.

Each sub-directory under [`experiments`](experiments) contains one of the experiments from the book chapter. For example, the sub-directory [`00-all-features`](experiments/00-all-features) corresponds to section 3.1 from the book chapter entitled *Experiment 0: Use all features*.

# Setup

The easiest way to get started is by first installing the [conda](https://conda.io/en/latest/) package manager for Python. The installation instructions can be found [here](https://conda.io/projects/conda/en/latest/user-guide/install/index.html).

Once `conda` is installed, you can install RSMTool and all its dependencies as follows:

```bash
conda env create -f environment.yaml
```

This will create a conda environment called `aesexpts` that can then be used to run any of the RSMTool experiments. For example, to run the RSMTool experiment contained with all of the features:

```bash
conda activate aesexpts
cd experiments/00-all-features
rsmtool config.json
```

Running this set of commands will produce the final RSMTool evaluation report under `report/all_features_report.html` in the same directory.
