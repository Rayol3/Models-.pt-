# YOLOv11m Pothole Segmentation Model (V6)

This repository contains the trained weights and metrics for a YOLOv11m-seg model trained on a custom pothole dataset.

## Model Details
- **Architecture:** YOLOv11m-seg (Medium, Segmentation)
- **Training Epochs:** 100 (Extended training from V6)
- **Dataset:** Unified Pothole Dataset (Includes multiple sources)
- **Framework:** Ultralytics YOLOv8/11

## Performance
The model was validated on two datasets:
1. **Internal Validation Set:** Reasonable performance on the standard validation split.
2. **Ninja Dataset (External Test):** The model showed poor generalization (mAP 0.0) on the "Dataset 1 (Simplex)" test set, likely due to domain shift or label format differences (converted from bbox to poly).

## Files
- `best.pt`: The best trained weights.
- `results.csv`: Training metrics logs.
- `confusion_matrix_normalized_val.png`: Normalized confusion matrix on the validation set.
- `confusion_matrix_ninja_test.png`: Confusion matrix on the external "Ninja" test set.

## Usage
```python
from ultralytics import YOLO

model = YOLO('best.pt')
results = model.predict('path/to/image.jpg', save=True, show=True)
```
