# gcn-core

Graph convolutional networks for node classification: the contribution of graph structure and the effect of oversmoothing.

The project aims to implement a graph convolutional network (GCN, Kipf & Welling, 2017) from scratch in PyTorch, using sparse matrix operations, and to study it on standard citation graphs (Cora, CiteSeer, PubMed):

- comparing the GCN with a multilayer perceptron (MLP) that sees only node features, to estimate the contribution of the graph structure;
- studying how accuracy and the distinguishability of node representations change as the network gets deeper (oversmoothing).

PyTorch Geometric is used to load the datasets and will serve as a reference implementation for checking the custom GCN layer.

## Completed stages

### 01 – Cora data overview

Inspect the raw files, node features, paper categories, public split, citation links and connected components of Cora, with summary statistics and example neighbourhoods.

- Notebook: [Cora data check](01-cora-baseline/01_cora_data_check.ipynb)
- [Open in Colab](https://colab.research.google.com/drive/1aSnxOKviDIXvcYxp-2mX75mObVc6iJ5a)

### 02 – CiteSeer and PubMed data overview

Inspect CiteSeer and PubMed using the public Planetoid splits, compare their features and graph structure, and summarise the three datasets. The CiteSeer analysis distinguishes test nodes outside the largest component from test nodes in components without training nodes.

- Notebook: [CiteSeer and PubMed data check](02-citeseer-pubmed-overview/02_citeseer_pubmed_data_check.ipynb)
- [Open in Colab](https://colab.research.google.com/drive/1SWRS49rCZ3_rRd0LlwucmyKv5OMez96O)

## Planned next stage – GCN layer implementation

Implement a custom GCN layer in PyTorch with sparse matrix operations and check it against a reference implementation on small graphs before training on Cora.

## Running in Google Colab

Google Colab is the main way to run the notebooks of both stages; a CPU runtime is sufficient. Each notebook installs what it needs in its first cells.

1. Open the Colab link of the stage.
2. Choose **File → Save a copy in Drive** to work in your own copy.
3. Choose **Runtime → Run all** to run all cells from top to bottom.

## Running locally (optional)

`pyproject.toml` and `uv.lock` define the dependencies for running the notebooks locally. Colab uses its own runtime and the setup cells inside the notebooks, not `uv.lock`, so the two environments are not identical.

1. Install [uv](https://docs.astral.sh/uv/).
2. From the root of the downloaded or cloned project, run:

   ```bash
   uv sync --locked
   ```

3. Open the notebook of a stage in VS Code with the Python and Jupyter extensions.
4. Select the kernel of the project environment `.venv`.
5. Run all cells.

Datasets are downloaded on the first run into `data/Planetoid`, relative to the working directory of the kernel.
