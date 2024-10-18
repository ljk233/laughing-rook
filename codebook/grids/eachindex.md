
# eachindex

```python
eachindex(grid, col_wise=False)
```

Yield the indices of each element in a 2D array-like grid, either row-wise or column-wise.

## Parameters

**grid : *array_like***

A 2D array-like object.

## Yield

**indices : *tuple[int, int]***

A tuple `(i, j)` representing the row and column index of each element in the grid.

## Examples

### Example 1

Row-wise iteration over a grid (default).

```python
>>> grid = [[1, 2], [4, 5]]
>>> for idx in eachindex(grid):
...     print(idx)
(0, 0)
(0, 1)
(1, 0)
(1, 1)
```

### Example 2

Column-wise iteration over a grid.

```python
>>> grid = grid = [[1, 2], [4, 5]]
>>> for idx in eachindex(grid, col_wise=True):
...     print(idx)
(0, 0)
(1, 0)
(0, 1)
(1, 1)
```

## Function

```python
import numpy as np

def eachindex(grid, col_wise):
    """Yield the indices of each element in a 2D array-like grid, either
    row-wise or column-wise.

    Parameters
    ----------
    grid : array_like
        A 2D array-like object.
    row_wise : bool, optional
        If True, then iterate over the grid column by column. Otherwise,
        iterate over the grid row by row. Default is False.

    Returns
    -------
    list[tuple[int, int]]
        A tuple `(i, j)` representing the row and column index of each
        element in the grid.

    >>> grid = [[1, 2], [4, 5]]
    >>> list(eachindex(grid))
    [(0, 0), (0, 1), (1, 0), (1, 1)]
    """
    grid_shape = np.shape(grid)
    for i, j in np.ndindex(grid_shape):
        yield tuple(j, i) if col_wise else (i, j)
```
