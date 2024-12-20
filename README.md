
# PyChow: A Python Implementation of the Chow Test

## Overview

The **Chow Test** is used to determine if there is a structural break in a regression model, often applied in time series or panel data. This implementation provides a simple, reusable interface for performing the test using Python.

---

## Formula

The Chow Test statistic is calculated as follows:

$$
F = \frac{(RSS_\text{combined} - (RSS_1 + RSS_2)) / k}{(RSS_1 + RSS_2) / (N_1 + N_2 - 2k)}
$$

Where:
- $$\( RSS_\text{combined} \)$$: Residual sum of squares for the combined regression model.
- $$\( RSS_1, RSS_2 \)$$: Residual sum of squares for the two separate regressions.
- $$\( k \)$$: Number of parameters (including intercept) in the regression model.
- $$\( N_1, N_2 \)$$: Number of observations in each subset.

The $$\( F \)$$-statistic follows the $$\( F \)$$-distribution with degrees of freedom:
- Numerator: $$\( k \)$$
- Denominator: $$\( N_1 + N_2 - 2k \)$$

---

## Installation

To install PyChow:

```bash
pip install pychow
```

---

## Usage

### Example Code

```python
import pandas as pd
import numpy as np
from pychow import ChowTest

# Example dataset
data = pd.DataFrame({
    'x': np.arange(1, 21),
    'y': np.concatenate([np.arange(1, 11), np.arange(21, 31)])
})

# Perform Chow Test
breakpoint = 10
result = ChowTest.chow_test(data, breakpoint, dependent_var='y', independent_vars=['x'])
print(result)
```

### Output

The result will be a dictionary with the Chow Test statistic and the p-value:

```python
{
    "Chow Test Statistic": 180.0,
    "P-value": 0.0
}
```

### Parameters

- `data`: A Pandas DataFrame containing your dataset.
- `breakpoint`: The index at which the dataset is split into two parts.
- `dependent_var`: Name of the dependent variable (target column).
- `independent_vars`: List of names for independent variables (features).

---

## Features

- Easy-to-use interface.
- Works with any dataset in Pandas DataFrame format.
- Outputs a dictionary with the test statistic and p-value.

---

## Contributing

Feel free to fork the repository, submit pull requests, or open issues for feature requests and bugs.

---

## License

[MIT License](https://github.com/amirbabaei97/pychow/blob/main/LICENSE)
