**Script:** `train.py`

Reads all settings from `conf/config.yaml` (Hydra). Outputs checkpoints, logs, and TensorBoard events to `outputs/<project.name>/<exp_tag>/`.

### Usage

```bash
# Standard run (reads conf/config.yaml):
python train.py

# Override specific config values without editing the file:
python train.py exp_tag=2 train.epochs=500

# Ovveride config location:
python ./cfdai/ntop_pipeline/train.py 
--config-path "/workspace/domino/cfdai/src/conf/"
--config-name "config" 
exp_tag=0 
train.epochs=500

```

### Key config parameters

|Parameter|Description|
|---|---|
|`exp_tag`|Experiment number — increment for each new run|
|`train.epochs`|Number of training epochs|
|`train.optimizer.lr`|Learning rate|
|`train.lr_scheduler.name`|`MultiStepLR` or `CosineAnnealingLR`|
|`model.model_type`|`volume`, `surface`, or `combined`|
|`model.volume_points_sample`|Points sampled per epoch during training|
|`model.normalization`|`min_max_scaling` or `mean_std_scaling`|