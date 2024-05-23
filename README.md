Install YOLO
```bash
pip install ultralytics --quiet
import ultralytics
from ultralytics import YOLO
ultralytics.checks()
```

Train YOLOv8 on a custom dataset
```bash
yolo obb train model=yolov8n-obb.pt data=DOTAv1.yaml epochs=10 imgsz=640
```

Validate with a new model
```bash
yolo obb mode=val model=/content/runs/obb//train/weights/best.pt data=DOTAv1.yaml
```

Predict the test images
```bash
yolo obb predict model=/content/runs/detect/train/weights/best.pt conf=0.25 source=/content/datasets/DOTAv1/images/test
```

If you want to specify what object should be predicted use classes=[int]
Identify only the planes in the pictures:
```bash
!yolo obb predict model=/content/runs/obb/train/weights/best.pt conf=0.25 source=/content/datasets/DOTAv1/images/test save=True classes=0
```
