# Dataset Information

The datasets used for Part B (Tasks 2 and 3) are synthetic binary classification
datasets generated directly within the Jupyter Notebooks using `scikit-learn`'s
`make_classification` and `make_circles` functions.

No external files are required to be downloaded. The datasets are automatically
generated at runtime when you execute the cells in the notebooks.

## Usage

The `make_classification` dataset is used in Tasks 2.1, 2.2, 2.3, and 3.1 to
generate a controlled noisy binary classification problem. The `make_circles`
dataset is used exclusively in Task 3.2 to demonstrate the failure mode.

### Task 2 and Task 3.1 — Noisy Binary Classification
```python
from sklearn.datasets import make_classification
import numpy as np

X, y = make_classification(n_samples=1000, n_features=20, n_informative=15,
                            n_redundant=2, n_classes=2, flip_y=0.1, random_state=42)
# Convert labels 0, 1 -> -1, 1 for margin-based algorithm
y = np.where(y == 0, -1, 1)
```

### Task 3.2 — Failure Mode (Concentric Circles)
```python
from sklearn.datasets import make_circles

X, y = make_circles(n_samples=500, noise=0.05, factor=0.5, random_state=42)
# Convert labels 0, 1 -> -1, 1
y = np.where(y == 0, -1, 1)
```

## Rationale

Since the original paper's core contribution is handling noisy, non-separable
data streams, the `make_classification` dataset is injected with 10% label noise
(`flip_y=0.1`) to serve as a controlled testbed for the Soft Margin formulation
in SCW-I. The `make_circles` dataset is used in Task 3.2 to demonstrate the
affine hyperplane failure mode, directly connecting to Assumption 3 identified
in Task 1.2.