Codes for our paper entitled Robust Small-Object Detection in Aerial Surveillance viaIntegrated Multi-scale Probabilistic Framework

## Datasets

This project utilizes two custom datasets, `ASS1` and `ASS2`.

* **Dataset Link**:(https://zenodo.org/records/10969885)
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

