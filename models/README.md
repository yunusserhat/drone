# Model Checkpoints

This directory should contain the trained model checkpoints.

## Structure

```
models/
├── yolov9e/
│   └── best.pt
├── yolov10x/
│   └── best.pt
├── yolov11x/
│   └── best.pt
├── yolov12x/
│   └── best.pt
└── rfdetr_large/
    ├── checkpoint_best_ema.pth
    └── checkpoint_best_total.pth
```

## Download

The pretrained checkpoints are available on Hugging Face:

🤗 **[yunusserhat/drone-grsl-models](https://huggingface.co/yunusserhat/drone-grsl-models)**

### Quick Download (All Models)

```bash
pip install huggingface_hub
huggingface-cli download yunusserhat/drone-grsl-models --local-dir .
```

### Download Specific Models

```bash
# RF-DETR Large
huggingface-cli download yunusserhat/drone-grsl-models rfdetr_large/checkpoint_best_ema.pth --local-dir .

# YOLOv12x
huggingface-cli download yunusserhat/drone-grsl-models yolov12x/best.pt --local-dir .

# YOLOv11x
huggingface-cli download yunusserhat/drone-grsl-models yolov11x/best.pt --local-dir .
```

### Model Sizes

| Model | File | Size |
|-------|------|------|
| RF-DETR Large (EMA) | `rfdetr_large/checkpoint_best_ema.pth` | 1.5 GB |
| RF-DETR Large (Total) | `rfdetr_large/checkpoint_best_total.pth` | 518 MB |
| YOLOv9e | `yolov9e/best.pt` | 112 MB |
| YOLOv10x | `yolov10x/best.pt` | 62 MB |
| YOLOv11x | `yolov11x/best.pt` | 110 MB |
| YOLOv12x | `yolov12x/best.pt` | 114 MB |

## Training Your Own Models

If you want to train the models yourself:

### YOLO Models

```bash
# Train YOLOv9e
python scripts/train_yolo.py --model yolov9e --yaml_path configs/dataset.yaml --epochs 1000

# Train YOLOv10x
python scripts/train_yolo.py --model yolov10x --yaml_path configs/dataset.yaml --epochs 1000

# Train YOLOv11x
python scripts/train_yolo.py --model yolov11x --yaml_path configs/dataset.yaml --epochs 1000

# Train YOLOv12x
python scripts/train_yolo.py --model yolov12x --yaml_path configs/dataset.yaml --epochs 1000
```

### RF-DETR

```bash
python scripts/train_rfdetr.py --dataset_dir /path/to/coco/dataset --epochs 500 --batch 8
```

## Note on Large Files

Model checkpoints are typically 100MB-500MB each. For GitHub:

1. Use Git LFS (Large File Storage):
   ```bash
   git lfs install
   git lfs track "*.pt"
   git lfs track "*.pth"
   git add .gitattributes
   ```

2. Or provide download links instead of committing large files directly.
