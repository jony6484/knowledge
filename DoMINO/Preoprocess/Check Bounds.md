**Script:** `check_bounds.py`

Reports the aggregate bounding box of STL geometry and volume mesh across all cases, with a ready-to-paste `config.yaml` snippet.

### CLI arguments

|Argument|Required|Description|
|---|---|---|
|`--data_dir`|yes|Directory containing `.zarr` case folders|
|`--max_cases`|no|Limit to this many cases (faster for large datasets)|

### Usage

```bash
python check_bounds.py --data_dir /data/zarr_train
```

### Example output

```
STL surface bounds  (bounding_box_surface):
  config.yaml snippet:
    min: [-0.04, -1.59, -0.13]
    max: [2.94,  1.59,  0.43]

Volume mesh bounds  (bounding_box):
  config.yaml snippet:
    min: [-2.0, -3.7, -2.7]
    max: [7.2,  3.5,  2.3]
```

Paste these values into `config.yaml` under `data.bounding_box` and `data.bounding_box_surface`.