Install YOLO
```bash
pip install ultralytics
```

Train YOLOv8 on a custom dataset
```bash
yolo obb train model=yolov8s.pt data={dataset.location}/data.yaml epochs=100 imgsz=640
```

Validate with a new model
```bash
yolo obb mode=val model={HOME}/runs/detect/train/weights/best.pt data={dataset.location}/data.yaml
```

Predict with a custom model
```bash
yolo obb mode=predict model={HOME}/runs/detect/train/weights/best.pt conf=0.25 source={dataset.location}/test/images
```
