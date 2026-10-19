# Data

| File | Contents |
| :--- | :--- |
| `labeled_corpus_33k.parquet` | All 33,000 audited trajectories with the benchmark verdict and the judge's behavior label (one row per trajectory) |
| `data_dictionary.csv` | Description of every column |

Load it with pandas:

```python
import pandas as pd
df = pd.read_parquet("data/labeled_corpus_33k.parquet")
print(df.groupby(["benchmark", "behavioral_bucket"]).size())
```

The raw agent trajectories (several GB) and the per-file judge outputs (about 220 MB) are too large for git and are not stored here.
