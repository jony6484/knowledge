**Script:** `check_coords.py`

Compares the spatial extents of your training zarr data, the config bounding boxes, and an optional inference STL side by side. Run this if you suspect a coordinate system or unit mismatch.

### CLI arguments

|Argument|Required|Description|
|---|---|---|
|`--zarr_dir`|yes|Training zarr directory|
|`--config`|yes|Path to `config.yaml`|
|`--stl`|no|Path to an inference STL to compare|
|`--n_cases`|no|Number of zarr cases to sample|

### Usage

```bash
python check_coords.py --zarr_dir /data/zarr_train --config conf/config.yaml
python check_coords.py --zarr_dir /data/zarr_train --config conf/config.yaml --stl /data/new/mesh.stl
```