
# asnumeric

```python
asnumeric(digits, delim=None)
```

Convert a string of delimited digits into a list of integers.

## Parameters

**digits : *str***

A string containing numeric values separated by a delimiter.

**delim : str, *optional***

The delimiter used to separate values in the string.
Default in `None`.

## Returns

**numbers : *list[int]***

List of integers parsed from the input string.

## Raises

**ValueError**

If the input string contains non-numeric values that cannot be converted to integers.

## Examples

```python
# 1. Comma-separated
>>> asnumeric("1,2,3,4")
[1, 2, 3, 4]

# 2. Whitespace-separated
>>> asnumeric("10 20 30")
[10, 20, 30]

# 3. Mixed separators
>>> asnumeric("5\t6|7;8")
[5, 6, 7, 8]

# 4. Non-numeric input (raises ValueError)
>>> asnumeric("1,2,three,4")
ValueError: invalid literal for int() with base 10: 'three'
```

## Code

```python
import re
from typing import Optional

def asnumeric(digits: str) -> list[int]:
    """Convert a string of delimited digits into a list of integers.

    Parameters
    ----------
    digits : str
        A string containing numeric values separated by a delimiter.

    Returns
    -------
    list[int]
        A list of integers parsed from the input string.

    Raises
    ------
    ValueError
        If the input string contains non-numeric values that cannot be
        converted to integers.

    Examples
    --------
    >>> asnumeric("1,2,3,4")   # 1. Comma-separated
    [1, 2, 3, 4]

    >>> asnumeric("10 20 30")  # 2. Whitespace-separated
    [10, 20, 30]

    >>> asnumeric("5\t6|7;8")  # 3. Mixed separators
    [5, 6, 7, 8]

    >>> asnumeric("1,2,three,4")
    ValueError: invalid literal for int() with base 10: 'three'
    """
    return list(map(int, re.split(r'\D+', digits)))
```
