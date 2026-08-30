1. Discover fields:
```bash
python ./cfdai/src/surface/discover_surface_fields.py --input-dir /workspace/domino/domino_data/physicsnemo_ahmed/cases
```
Output example to put in the config file:
```bash
SURFACE_FIELD_NAMES = {
    "k": "scalar",
    "nut": "scalar",
    "omega": "scalar",
    "p": "scalar",
    "yPlus": "scalar",
    "U": "vector",
    "wallShearStress": "vector",
}
```
SET FIELDS IN THE convert.yaml FILE
2. Convert to zarr:
```bash
/workspace/domino/cfdai/src/surface/convert_to_zarr_surface.py
```
currently set the dirs inside the file, TODO argparse