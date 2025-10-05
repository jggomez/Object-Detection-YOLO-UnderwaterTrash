# Underwater Trash Detection using YOLOv11

This notebook demonstrates the process of fine-tuning a YOLOv11 object detection model to identify underwater trash.

## Steps:

1.  **Download Data**: The dataset for underwater trash detection is downloaded using the `kagglehub` library. The dataset path is: `/kaggle/input/underwater-trash-detection/utd2.v8i.yolov8`.
    - Train images: 7308, Train labels: 7308
    - Val images: 1795, Val labels: 1795
    - Test images: 473, Test labels: 473

2.  **Data Exploration**: The downloaded data is explored to understand the directory structure and the number of images and labels in the training, validation, and test sets.

3.  **Create YAML File**: A YAML file is created to configure the dataset for YOLOv11 training, specifying the paths to the training, validation, and test images, as well as the class names ('Bio', 'Rov', 'Trash').

4.  **Fine-tuning YOLOv11**: The `ultralytics` library is used to load a pre-trained YOLOv11 model (`yolo11s.pt`) and fine-tune it on the underwater trash dataset for 30 epochs with an image size of 640.

5.  **Evaluate Training Results**: The training results are evaluated by examining the generated plots, such as the loss curves and confusion matrix, to assess the model's performance and check for overfitting.
    - Best Epoch's Validation Metrics: mAP50-95(B): 0.7017, mAP50(B): 0.9381
    - The model shows decreasing loss and increasing performance without overfitting.
    - Confusion Matrix Analysis: Strong at detecting "Trash" but struggles with background confusion, often classifying it as "Trash". Low confusion between actual object classes.

6.  **Generate Predictions**: The fine-tuned model is used to generate predictions on the test set images using the best weights from training.

7.  **Visualize Predictions**: Individual predictions are visualized by displaying images with the predicted bounding boxes and class labels.

## Comparison with other YOLOv11 Models (YOLOv11n, YOLOv11s, YOLOv11m)

- **Overall Performance (mAP50-95):** YOLOv11s (0.65) outperforms YOLOv11m (0.5791) and YOLOv11n (0.5867).
- **mAP50:** All models perform well (YOLOv11s: 0.93, YOLOv11m: 0.8877, YOLOv11n: 0.8905).
- **Confusion Matrix Analysis:** Consistent struggle with background confusion across models. YOLOv11s has higher correct "Trash" detections.
- **Training Time:** YOLOv11s is faster and uses fewer resources compared to YOLOv11m.

In summary, the YOLOv11s model demonstrates superior performance and efficiency for this underwater trash detection dataset.

## Author

* **Juan Guillermo Gómez**
* Linkedin: [@jggomezt](https://www.linkedin.com/in/jggomezt/)
