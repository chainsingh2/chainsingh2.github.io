# Behave BDD project for object detection
This project demonstrates object detection and vehicle tracking using the YOLO model and Behave BDD framework. It captures a live video feed, detects objects in the video, tracks vehicles, and counts the number of vehicles that enter a defined intersection box.

## Project Structure
The project directory structure is organized as follows:
```
project_root/
│
├── features/
│ ├── myfeature.feature
│ └── steps/
│    └── steps.py
│
├── behave.ini
├── coco
├── tracker.py
├── video.mp4
└── yolov8s.pt
```
## Set-Up


### Features

- **features/myfeature.feature**: This feature file defines the behavior scenario for object detection and vehicle tracking.

- **features/steps/steps.py**: The step definitions for the scenarios are implemented in this Python file.

### Configuration

- **behave.ini**: Behave configuration file with settings for test execution and reporting.

### Data and Models

- **coco**: Placeholder directory for datasets or other data needed for the project.

- **video.mp4**: A sample video file used for testing.

- **yolov8s.pt**: The YOLOv8 model file used for object detection.

### Tracker

- **tracker.py**: This Python module implements the object tracking logic.

## Usage

To run the BDD tests and demonstrate object detection and vehicle tracking:

1. Ensure you have Python installed on your system.

2. Install the required dependencies by running:

   ```bash
   pip install behave opencv-python pandas ultralytics allure-behave
    ```
3. Run Behave with the Allure formatter to execute the BDD tests and generate Allure report: 
 -  This will create Allure report files in the allure-results directory.
   
    ```bash 
    behave -f allure_behave.formatter:AllureFormatter -o allure-results ./features
    ```
4. Serve the Allure reports locally:
    
    This will start a local web server and open a web browser displaying the generated Allure reports. You can access the reports by navigating to the provided URL (usually something like http://localhost:port).
    The tests will simulate object detection and vehicle tracking in the provided video feed.
    
    ```bash
    allure serve allure-results
    ```
