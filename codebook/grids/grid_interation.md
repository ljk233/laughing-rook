
# Iterating Over the Rows and Columns of a Grid

How to efficiently iterate over both the rows and columns of a grid.

## Row Iteration

Iterate over the rows of a grid by using a simple `for` loop.

```python
>>> grid = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
>>> for row in grid:
...     print(row)
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]
```

## Column iteration

Iterate over the columns of a grid by *zipping* the grid.

```python
>>> for column in zip(*grid):
...     print(column)
(1, 4, 7)
(2, 5, 8)
(3, 6, 9)
```

If the grid has unequal row lengths, then we can use `itertools.zip_longest`.

```python
>>> from itertools import zip_longest
>>> ragged_grid = [[1, 2, 3], [4, 5], [7, 8, 9]]
>>> for column in zip_longest(*ragged_grid):
...     print(column)
(1, 4, 7)
(2, 5, 8)
(3, None, 9)
```

A different value can be returned by passing an argument for *fillvalue*.

## Row and column iteration

Iterate over both the rows by *chaining* them together using `itertools.chain`.

```python
>>> from itertools import chain
>>> for line in chain(*grid, *zip(*grid)):
...     print(line)
[1, 2, 3]
[4, 5, 6]
[7, 8, 9]
(1, 4, 7)
(2, 5, 8)
(3, 6, 9)
```

## Flattening the Grid

Iterate over the items of a list by flattening it using using `itertools.chain`.

### Flattening the Grid Row-Wise

```python
>>> from itertools import chain
>>> grid = [[1, 2], [4, 5]]
>>> for entry in chain.from_iterable(grid):
...     print(entry)
1
2
3
4
```

### Flattening the Grid Column-Wise

Flatten the grid column-wise by using using `zip` along with `chain`.

```python
>>> from itertools import chain
>>> grid = [[1, 2], [4, 5]]
>>> for entry in chain.from_iterable(zip(*grid)):
...     print(entry)
1
4
2
5
```

## See alo

[[]]
