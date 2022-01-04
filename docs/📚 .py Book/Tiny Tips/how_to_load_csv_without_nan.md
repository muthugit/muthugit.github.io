# [Pandas] Load CSV without replacing empty value to `nan`

In pandas the usual `pd.read_csv` load the CSV and replacing empty values to `nan`. If that needs to be override, pandas has the boolean option `keep_default_na`. If it is `False` then the pandas won't apply `nan` on the data

Example

```python
import pandas as pd
pd.read_csv("/tmp/data.csv", keep_default_na=False)
```