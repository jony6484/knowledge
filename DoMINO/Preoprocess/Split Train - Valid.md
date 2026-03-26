**Script:** `split_zarr.py`

Moves `.zarr` cases from a single directory into separate `zarr_train/` and `zarr_val/` directories.

### CLI arguments

|Argument|Required|Default|Description|
|---|---|---|---|
|`--zarr_dir`|yes|—|Source directory with all `.zarr` cases|
|`--train_dir`|no|`<zarr_dir>/../zarr_train`|Output train directory|
|`--val_dir`|no|`<zarr_dir>/../zarr_val`|Output val directory|
|`--val_pct`|no|`0.2`|Fraction of cases for validation (e.g. `0.2` = 20%)|
|`--random`|no|off|Shuffle cases randomly before splitting|
|`--seed`|no|`42`|Random seed for reproducibility (used with `--random`)|

### Usage

```bash
# Default: 20% val, deterministic (sorted order):
python split_zarr.py --zarr_dir /data/zarr

# Random 20% val split, reproducible:
python split_zarr.py --zarr_dir /data/zarr --val_pct 0.2 --random --seed 42

# Custom output directories:
python split_zarr.py --zarr_dir /data/zarr --train_dir /data/train --val_dir /data/val
```
