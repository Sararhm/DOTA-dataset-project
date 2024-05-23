## YOLO Training on datasets from Roboflow

### Overview

This README guides you through setting up and training a YOLO model using the Ultralytics library (YOLO model) and datasets from Roboflow. The steps include installing the required packages, downloading the dataset, training the model, and exporting the trained model.

### Prerequisites

- Python 3.x
- Pip package manager
- Basic familiarity with Python and Jupyter Notebooks(or Goggle Colab)

### Installation

1. **Install Ultralytics**:
   To use the YOLO model from the Ultralytics library, first install it using pip:

   ```bash
   pip install ultralytics
   ```

2. *you can choose to either download the dataset from Roboflow on your invironment (you can make changes) or link the desired workspace into your trainings(you can't make changes)*
   **Export Dataset from Roboflow**:
   To download a dataset from Roboflow Universe, follow these steps:
   - Navigate to the dataset's Roboflow Universe page.
   - Click on the "Download this Dataset" button.
   - Choose the YOLO format, select the version and framework.
   - Use the generated code snippet to download the dataset to your local environment (or click 'show download code' and copy the RAW URL)

Example code:

   ```python
   from roboflow import Roboflow

   rf = Roboflow(api_key='YOUR_API_KEY')
   project = rf.workspace('WORKSPACE').project('PROJECT')
   dataset = project.version(1).download('yolov8')
   ```

   ```bash
   curl -L "https://app.roboflow.com/project/workspace" &gt; roboflow.zip; unzip roboflow.zip; rm roboflow.zip
   ```
   For more detailed instructions, follow this guide: [How to Train YOLOv8 on a Custom Dataset](https://blog.roboflow.com/how-to-train-yolov8-on-a-custom-dataset/)

### Training the Model

To train your model, you can use the following command line or Python script:

- **Command Line**:
(dataset source: https://universe.roboflow.com/class-dvpyb/dota-nbzyn)
 
if you downloaded the dataset use this command:
 ```bash
  yolo train model=yolov8n.pt data={dataset.location}/data.yaml epochs=10 imgsz=320
 ```

  if not, use this command with the direct link(RAW URL):
 ```bash
  yolo train model=yolov8n.pt data='https://universe.roboflow.com/ds/OT0z0fQptc?key=2vy8xrz2I8' epochs=10 imgsz=320
  ```

  You can increase the number of epochs as needed for better accuracy. This dataset is too big to be trained on image size of 640 and I ran out of RAM every time I tried to run it.

- **Python Code**:

  ```python
  from ultralytics import YOLO

  # Load a model(either .yaml or .pt)
  model = YOLO('yolov8n.yaml')  # build a new model from scratch
  model = YOLO('yolov8n.pt')  # load a pretrained model (recommended for training)

  # train the model
  # Use the model
  results = model.train(data={dataset.location}/data.yaml, epochs=1)
  #or the RAW URL link
  results = model.train(data='https://universe.roboflow.com/ds/OT0z0fQptc?key=2vy8xrz2I8', epochs=1)

  # evaluate model performance on the validation set
  results = model.val()
  
  # export the model to ONNX format
  results = model.export(format='onnx')  
  ```

### Downloading the Trained Model

If you are using an online platform like Google Colab and want to download the trained model's results to your local computer, run the following commands:

```bash
zip -r runs.zip /content/runs/
from google.colab import files
files.download('runs.zip')
```

### Conclusion

This setup should help you easily train a YOLO model with custom datasets from Roboflow. Adjust parameters such as epochs and image size based on your computational resources and dataset requirements.
