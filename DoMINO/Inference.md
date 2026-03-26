**Script:** `run_inference.py`

Loads a trained checkpoint and predicts `[Vx, Vy, Vz, P]` on a new STL geometry. Outputs a VTI file (grid-based) or VTU file (scattered points).

### CLI arguments

|Argument|Required|Default|Description|
|---|---|---|---|
|`--stl`|yes|—|Path to input STL file|
|`--checkpoint`|yes|—|Directory containing `.mdlus` checkpoint files|
|`--output`|no|`predicted_volume.vtu`|Output file path (`.vti` for grid, `.vtu` for points)|
|`--stl_scale`|no|`1.0`|Scale STL coordinates (use `0.001` for mm → m)|
|`--vti_resolution`|no|from config|Grid resolution `NX NY NZ` (only for `.vti` output)|
|`--num_points`|no|`500000`|Number of points to predict (only for `.vtu` output)|
|`--inlet_velocity`|no|from config|Override inlet velocity (m/s)|
|`--air_density`|no|from config|Override air density (kg/m³)|
|`--config`|no|auto-detected|Path to `config.yaml`|
|`--scaling`|no|from config|Path to `scaling_factors.pkl`|
|`--batch_size`|no|from config|Points per inference batch|

### Usage

**VTI output (grid-based, recommended for ParaView):**

```bash
python run_inference.py \
    --stl        /data/new/mesh.stl \
    --checkpoint outputs/RAF_CFD/2/models \
    --output     /data/predicted.vti \
    --stl_scale  0.001 \
    --vti_resolution 128 64 64
```

**VTU output (scattered points):**

```bash
python run_inference.py \
    --stl        /data/new/mesh.stl \
    --checkpoint outputs/RAF_CFD/2/models \
    --output     /data/predicted.vtu \
    --stl_scale  0.001 \
    --num_points 500000
```

### Output VTI arrays

|Array|Type|Description|
|---|---|---|
|`velocity_time_avg`|vector (3-component)|Time-averaged velocity [Vx, Vy, Vz]|
|`pressure_time_avg`|scalar|Time-averaged pressure|
|`ImplicitField`|scalar|Fluid domain mask (−1 everywhere)|

> **Note:** The script auto-detects the latest checkpoint in the `--checkpoint` directory. The config and scaling factors are read from the checkpoint directory automatically (saved there by `train.py`), so `--config` and `--scaling` overrides are usually not needed.