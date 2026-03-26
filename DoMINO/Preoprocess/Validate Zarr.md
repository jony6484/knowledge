
**Script:** `validate_zarr.py`

Checks every `.zarr` case for correct keys, shapes, dtypes, NaN/Inf values, and geometry consistency. Run this before doing anything else with your data.

### CLI arguments

|Argument|Required|Description|
|---|---|---|
|`--data_dir`|yes|Directory containing `.zarr` case folders|
|`--verbose` / `-v`|no|Print per-case stats (velocity range, pressure range, point counts)|

### Usage

```bash
python validate_zarr.py --data_dir /data/zarr
python validate_zarr.py --data_dir /data/zarr --verbose
```

### Expected output

```
Validating 50 cases in /data/zarr

  PASS  0.zarr
  PASS  1.zarr
  FAIL  2.zarr
        ! volume_fields contains 12 NaN values

Result: 49 passed, 1 failed
```
