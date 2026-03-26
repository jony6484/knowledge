**Script:** `check_areas.py`

Reports STL face area statistics and suggests an `area_weighing_factor` value (≈ 1 / max_area) for `config.yaml`.

### CLI arguments

|Argument|Required|Description|
|---|---|---|
|`--data_dir`|yes|Directory containing `.zarr` case folders|
|`--max_cases`|no|Limit to this many cases|

### Usage

```bash
python check_areas.py --data_dir /data/zarr_train
```

### Example output

```
Across 40 cases:
  max area:  1.84e-02 m²
  mean area: 3.21e-04 m²

  config.yaml snippet:
    model:
      loss_function:
        area_weighing_factor: 54
```

Paste the suggested value into `config.yaml`.