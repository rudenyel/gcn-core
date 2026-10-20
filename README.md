# gcn-core

Graph convolutional networks for node classification: the contribution of graph structure and the effect of oversmoothing.

The project implements a graph convolutional network (GCN, Kipf & Welling, 2017) from scratch in PyTorch, using sparse matrix operations, and studies it on standard citation graphs (Cora, CiteSeer, PubMed):

- comparing the GCN with a multilayer perceptron (MLP) that sees only node features, to estimate the contribution of the graph structure;
- studying how accuracy and the distinguishability of node representations change as the network gets deeper (oversmoothing).

PyTorch Geometric is used to load the datasets and as a reference implementation for checking the custom GCN layer.

## Current stage – Cora data overview

Explore the paper categories, binary word features, citation links and public split of Cora through summary statistics, example nodes and edges, and visualizations.

- Notebook: [`01-cora-baseline/01_cora_data_check.ipynb`](01-cora-baseline/01_cora_data_check.ipynb)
- [Open in Colab](https://colab.research.google.com/drive/1aSnxOKviDIXvcYxp-2mX75mObVc6iJ5a)

## Next stage – GCN layer implementation

Prepare the features and normalized adjacency matrix, implement a GCN layer in PyTorch, and compare it with a reference implementation.

## Running in Google Colab

Google Colab is the main way to run the notebooks; a CPU runtime is sufficient. The notebook installs what it needs in its first cells.

1. Open the Colab link of the stage.
2. Choose **File → Save a copy in Drive** to work in your own copy.
3. Choose **Runtime → Run all** to run all cells from top to bottom.

## Running locally (optional)

`pyproject.toml` and `uv.lock` define the dependencies for running the notebooks locally. Colab uses its own runtime and the setup cells inside the notebook, not `uv.lock`, so the two environments are not identical.

1. Install [uv](https://docs.astral.sh/uv/).
2. From the root of the downloaded or cloned project, run:

   ```bash
   uv sync --locked
   ```

3. Open the notebook in VS Code with the Python and Jupyter extensions.
4. Select the kernel of the project environment `.venv`.
5. Run all cells.

Datasets are downloaded on the first run into `data/Planetoid`, relative to the working directory of the kernel.
