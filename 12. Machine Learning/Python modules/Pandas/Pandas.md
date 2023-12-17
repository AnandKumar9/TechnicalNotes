##### Extracting specific rows/columns (`iloc`)

Overe here `:` in first argument indicates that all the rows should be extarcted, `:-1` in second argument indicates all columns except the last should be extracted. ([Reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iloc.html))

```
import pandas as pd

dataset = pd.read_csv('Data.csv')
X = dataset.iloc[:, :-1].values
```

```
df.iloc[1:3, 0:3]

      a     b     c
1   100   200   300
2  1000  2000  3000
```

