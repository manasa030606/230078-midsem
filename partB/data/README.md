# Dataset Information

The dataset used for Part B (Tasks 2 and 3) is a synthetic binary classification dataset generated directly within the Jupyter Notebooks using `scikit-learn`'s `make_classification` and `make_circles` functions.

No external files are required to be downloaded. The datasets are automatically generated at runtime when you execute the cells in the notebooks. 

## Rationale
Since the original paper's contribution is explicitly evaluating performance on non-separable and noisy data streams, the `make_classification` dataset is injected with a 10% label noise (`flip_y=0.1`) to serve as a controlled testbed for the Soft Margin formulation in SCW-I. The `make_circles` dataset is used exclusively in Task 3.2 to demonstrate the affine hyperplane failure mode.
