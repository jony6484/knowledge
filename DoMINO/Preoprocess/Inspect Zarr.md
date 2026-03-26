
**Script:** `inspect_zarr.py`

Plots histograms and box plots of every field across all cases. Useful for spotting unit errors, outliers, and understanding the data ranges before training.

### CLI arguments

|Argument|Required|Description|
|---|---|---|
|`--data_dir`|yes|Directory containing `.zarr` folders or `.npy` files|
|`--fields`|no|Only plot fields whose names contain these strings|
|`--max_cases`|no|Limit to this many cases (faster for large datasets)|
|`--save_dir`|no|Save plots as PNG files here instead of showing interactively|

### Usage

```bash
# Plot all fields interactively:
python inspect_zarr.py --data_dir /data/zarr

# Only check velocity and pressure, save to disk:
python inspect_zarr.py --data_dir /data/zarr --fields volume_fields stl_areas --save_dir /data/plots

# Quick check on 5 cases:
python inspect_zarr.py --data_dir /data/zarr --max_cases 5
```