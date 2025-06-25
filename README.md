# One Step at a Time: Self-supervised Dual Hypergraph Similarity Learning for Curricular Graph Structure Learning

<p align="left">
  <img src='https://img.shields.io/badge/Python-3.12.9-blue'>
  <img src='https://img.shields.io/badge/PyTorch-2.4.0+cu118-blue'>
  <img src='https://img.shields.io/badge/PyTorch_Geometric-2.6.1-brightgreen'>
  <img src='https://img.shields.io/badge/PyTorch_Scatter-2.1.2+pt24cu118-brightgreen'>
  <img src='https://img.shields.io/badge/PyTorch_Sparse-0.6.18+pt24cu118-brightgreen'>
</p>

---

## Description

This repository contains the code for the paper "One Step at a Time: Self-supervised Dual Hypergraph Similarity Learning for Curricular Graph Structure Learning" (DARLING).

## Requirements

### Package Versions

- python==3.12.9
- torch==2.4.0+cu118
- torch_geometric==2.6.1
- torch_scatter==2.1.2+pt24cu118
- torch_sparse==0.6.18+pt24cu118
- dgl==2.4.0+cu118
- numpy==2.1.2
- pandas==2.2.3
- multiset==3.2.0

### Hardware Requirements

- NVIDIA GPU >= 24GB VRAM x1
- RAM >= 8GB x1

## Notes & Usage

### Directory & File Structure

The current directory structure of this repository is as follows:

```
DARLING/
├── README.md
├── main_tune_darling_anc_alt.py
├── main_tune_darling_ori_alt.py
├── scripts/
│   ├── cora_ori_alt_iter.sh
│   ├── pubmed_anc_alt_iter.sh
|── model/
│   ├── difficulty_measurer.py
│   ├── gnns.py
│   ├── graph_learner.py
|   ├── self_supervision.py
├── utils/
│   ├── ...
```

- The code of the graph structure curriculum module is located at `./model/difficulty_measurer.py`.
- The code of the GNNs & HNNs is located at `./model/gnns.py`.
- The code of the multi-view graph structure enhancement module  is located at `./model/graph_learner.py`.
- The code of the self-supervised dual hypergraph similarity learning module is located at `./model/self_supervision.py`.
- The dataset-related code and other stuff are located in the `./utils` directory.

You should use the `main_tune_darling_ori_alt.py` or `main_tune_darling_anc_alt.py` to run the training and evaluation process. The shell scripts in the `./scripts` directory are provided for convenience, which will call the corresponding python scripts with the tuned hyperparameters.

### Two Versions of Python Scripts

There are **two versions** of the python scripts, one is for the small datasets, e.g., `Cora`, `Citeseer`, and the other is for the large datasets, e.g., `Pubmed`, `Minesweeper`, `Amazon-ratings`, and `Roman-empire`. The code for the large datasets uses the anchor technique borrowed from [IDGL](https://github.com/hugochan/IDGL) to scale the training process.

### Datasets

We borrow the dataset-related code from the awesome repository [OpenGSL](https://github.com/OpenGSL/OpenGSL). 

*You don't need to install the OpenGSL package, we have already included the necessary code in this repository. Just run the scripts, and the datasets should be downloaded automatically.*

### Running Scripts

The running scripts are located in the [`./scripts`](./scripts) directory for reference.

To train and evaluate the model on small datasets, you can run the provided script directly, just like this:

```bash

python ./scripts/cora_ori_alt_iter.sh
```

To train and evaluate the model on large datasets, you can run the provided script directly, just like this:

```bash
python ./scripts/pubmed_anc_alt_iter.sh
```

In addition, the search space of the hyperparameters is added in the `main_tune_darling_ori_alt.py` and `main_tune_darling_anc_alt.py` scripts, which can be used for hyperparameter tuning on your own platform for better reproducibility. 

## Acknowledgements

We borrow some code from this awesome repository [OpenGSL](https://github.com/OpenGSL/OpenGSL).

We also reference the hypergraph-related code from [HypeBoy](https://github.com/kswoo97/hypeboy), [TriCL](https://github.com/wooner49/TriCL), and [UniGNN](https://github.com/OneForward/UniGNN).

**We thank the authors for their great work!**

