**Commands to train, validate and predict DOTA dataset on YOLO model**

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
Export your model: You can export to any format using the format argument, i.e. format='onnx' or format='engine'.
Visualize:       https://netron.app
```bash
yolo export model=yolov8n-obb.pt format=onnx  # export official model
yolo export model=path/to/best.pt format=onnx  # export custom trained model
```
Predict or validate directly on exported models.
```bash 
yolo predict model=yolov8n-obb.onnx
```
 
download the compiled result file
```bash
!zip -r runs.zip /content/runs/
from google.colab import files
files.download('runs.zip')
```
