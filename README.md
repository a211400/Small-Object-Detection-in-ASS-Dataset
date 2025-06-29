Small-Object-Detection

## Datasets

This project utilizes two custom datasets, `ASS1` and `ASS2`.

* **Download Link**: [Baidu Netdisk: ASS\_Datasets.rar (Access Code: bx8r)](https://pan.baidu.com/s/1zr8CpxCXKXAYFqj7SOBYGw?pwd=bx8r)
* **Recommendation**: For broader accessibility and easier reproduction of our work, we recommend you upload the dataset to a service like Google Drive or Dropbox and provide the shareable link here.
* **Directory Structure**: After downloading and extracting the files, please place the dataset folders in the project'--

This is an enhanced implementation based on the official [Ultralytics YOLOv11](https://github.com/ultralytics/ultralytics) repository. This project aims to improve the performance of the object detection model, especially for small objects, by integrating advanced neural network modules and a specialized loss function.

This repository contains the source code for our academic paper.


* **Directory Structure**: After downloading and extracting the files, please place the dataset folders in the project's root directory. Ensure the structure is as follows:

  ````
  .
  ├── ultralytics/
  ├── datasets/
  │
  ```   ├── ASS1/
  │   │   ├── ASS1.yaml
  │   │   ├── images/
  │   │   └── labels
  ```/
  │   └── ASS2/
  │       ├── ASS2.yaml
  │       ├── images/
  │       └── labels/
  ```└── README.md
  ...
  ````

## Setup

1. **Clone the Repository**

   ```bash
   git clone 
   ```

2. **Install Dependencies**

   ```bash
   pip install ultralytics
   ```

## Usage

We provide a detailed workflow for training, validation, and prediction.

### 1. Training

We employ two distinct training strategies:

* **Training from Scratch on the ASS1 Dataset**:
  This command uses our custom `yolo11.yaml` configuration file to train the model on the ASS1 dataset for 300 epochs. The `pretrained=False` flag ensures that the model weights are initialized randomly.

  ````bash
  yolo detect train model=ultralytics/cfg
  ```/models/11/yolo11.yaml data=datasets/ASS1/ASS1.yaml epochs=300 imgsz=64
  ```0 batch=16 pretrained=False project=runs/ASS1 name=yolo11n
  ````

---

````
```bash
yolo detect train model=ultralytics/cfg/models/11/yolo11.yaml data=datasets/ASS1/ASS1.yaml epochs=300 imgsz=640 batch=16 pretrained=False project=runs/ASS1 name=yolo11n
````

* **Transfer Learning on the ASS2 Dataset**:
  Given the smaller size of the ASS2 dataset, we use the best weights (`best.pt`) from the model trained on ASS1 as pretrained weights. This fine-tuning approach helps to prevent overfitting.

  ````bash
  # Note: Please replace 'runs/ASS1/
  ```yolo11n_from_scratch/weights/best.pt' with the actual path to the weights generated in the previous step.
  ```yolo detect train model=ultralytics/cfg/models/11/yolo11.yaml data=datasets/ASS2/ASS2.yaml epochs=300 imgsz=640 batch=16 pretrained="runs/ASS1/yolo11n/weights/best.pt" project=runs/ASS2 name=yolo11n
  ````

### 2. Validation

Evaluate the performance of the trained models on the validation set.

* **Evaluate on the ASS2 Validation Set**:

  ````bash
  #
  ``` Validate the model that was fine-tuned on ASS2
  yolo detect val model=runs/ASS2/yolo11n/weights/best.pt data=datasets/ASS2/ASS2.yaml imgsz=640 project=runs/val name=ASS2_val
  ````

  ```bash
  # Validate the model that was fine-tuned on ASS2
  yolo detect val model=runs/ASS2/yolo11n/weights/best.pt data=datasets/ASS2/ASS2.yaml imgsz=640 project=runs/val name=ASS2_val
  ```

### 3. Prediction

We provide two custom scripts for running inference.

* **`predict1.py`**: 
  ````bash
  python predict1.py
  ````
* **`predict2.py`**: 

  ```bash
  python predict2.py
  ```
