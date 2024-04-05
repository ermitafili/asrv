# ASRV

This is the repository for development of ASRV.

Problem Statement

Driving is the most dangerous activity that people do on a daily basis, which mainly comes from not following driving regulations and rules. The most common violations are: speeding, driving under influence, illegal parking, not following road signs or signals, which can lead to accidents. The most efficent way to fight this problem, is by addressing every single violation possible, so that people do not become repeat offenders, making the roads a safer place.
-Model Type and Current Performance Metrics

ASRV uses YOLOV8 combined with DeepSORT for object detection, classification and tracking. The YOLOV8 model is optimized with OpenVINOTM for better performance.

Currently this system is trained on the YOLOV8x(extralarge) dataset, based on COCO and a self-driving car dataset from Roboflow. Later in development a custom dataset using images captured by the ASRV system will be used.

LPR is powered by a special instance of YOLOV8 and can detect license plate position. After a photo is captured, an OCR model(Tesseract) is used to register the number plate. Plate detection is realtime while OCR takes 5-10 seconds dependent on photo conditions. Both of these models have deep learning implementations to assist in efficiency and speed. Both models are trained on a license plate dataset.

Speed estimation is calculated in a geometric-based way. Using object detection the system finds the object’s position relative to the street and calculates the estimated speed. This approach is more accurate, especially during sub-optimal conditions.

In normal conditions  for object detection we have observed a detection confidence rate of 75-90% and in sub-optimal conditions 40-60%. During development this can be optimized with a more complex dataset and a image pre-processing model.

The License Plate Detection system has a 70-95% accuracy while the OCR model has 40-60% accuracy in sub-optimal conditions and a 70-90% accuracy in optimal conditions.

The speed estimation model has 75% accuracy in optimal conditions and 50-60% in sub-optimal conditions. Accuracy will increase with a more complex dataset and model.
