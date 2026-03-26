Edit `conf/config.yaml` with the values from the previous steps:

```yaml
data:
  input_dir: /path/to/zarr_train          # from split_zarr.py
  input_dir_val: /path/to/zarr_val        # from split_zarr.py
  scaling_factors: /path/to/scaling_factors/scaling_factors.pkl
  bounding_box:                           # from check_bounds.py
    min: [-2.0, -3.7, -2.7]
    max: [7.2,  3.5,  2.3]
  bounding_box_surface:                   # from check_bounds.py
    min: [-0.04, -1.59, -0.13]
    max: [2.94,  1.59,  0.43]

model:
  loss_function:
    area_weighing_factor: 54              # from check_areas.py

variables:
  volume:
    solution:
      # Column order must match VOLUME_FIELD_NAMES in convert_to_zarr.py
      U_time_avg: vector   # columns 0, 1, 2
      p_time_avg: scalar   # column 3

exp_tag: 1   # increment this for each new training run
```

> **Important:** The variable names and order under `variables.volume.solution` must exactly match the column order used in `convert_to_zarr.py`.