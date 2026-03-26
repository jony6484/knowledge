**Script:** `compute_statistics.py`

Computes mean, std, min, and max across the training dataset and saves them to `scaling_factors.pkl`. This file is required by both training and inference.

### CLI arguments

|Argument|Required|Default|Description|
|---|---|---|---|
|`--data_dir`|yes|—|Training zarr directory|
|`--output`|yes|—|Path to save `scaling_factors.pkl`|
|`--config`|no|`conf/config.yaml`|Path to config file|
|`--max_samples`|no|from config|Max data points to sample (lower = faster, less accurate)|
|`--force`|no|off|Recompute even if `.pkl` already exists|

### Usage

```bash
python compute_statistics.py \
    --data_dir /data/zarr_train \
    --output /data/scaling_factors/scaling_factors.pkl
```

### Output

- `scaling_factors.pkl` — loaded by training and inference
- `scaling_factors_summary.txt` — human-readable report of all statistics

> **Note:** Make sure `data.scaling_factors` in `config.yaml` points to the same path as `--output`.