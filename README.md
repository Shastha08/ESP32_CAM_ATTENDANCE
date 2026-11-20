# ESP32-CAM Based Face Recognition Attendance Management System

## 1. Project Overview

The ESP32-CAM Based Face Recognition Attendance Management System is an automated attendance monitoring project developed using Python, OpenCV, YuNet Face Detection and SFace Face Recognition.

The system detects faces through an ESP32-CAM module, identifies registered individuals and automatically records their attendance with IN TIME and OUT TIME.

The system also provides a web-based dashboard to monitor live camera streaming, face recognition status and attendance records for the last 7 days.

## 2. Project Objectives

- Automate the attendance marking process using face recognition.
- Identify registered and unknown individuals.
- Display real-time face detection using coloured bounding boxes.
- Automatically record IN TIME and OUT TIME.
- Maintain attendance records for 7 days.
- Display attendance information through a web dashboard.
- Prevent duplicate attendance entries.

## 3. Hardware Requirements

| Component | Description |
|---|---|
| ESP32-CAM | Camera module |
| USB-to-TTL Converter | ESP32-CAM programming |
| Power Supply | Suitable regulated supply |
| Computer / Laptop | Python execution and monitoring |

## 4. Software Requirements

- Python 3.x
- OpenCV
- Flask
- NumPy
- Pandas (if used by the implementation)
- ESP32-CAM Camera Web Server

### AI Models

- `face_detection_yunet_2023mar.onnx` – Face Detection
- `face_recognition_sface_2021dec.onnx` – Face Recognition
- `Shastha_face.npz` – Registered Face Data

## 5. System Architecture

The system follows this workflow:

1. ESP32-CAM captures live video.
2. Python receives the camera stream.
3. OpenCV processes the captured frames.
4. YuNet detects faces.
5. SFace compares detected faces with registered face data.
6. The system identifies the person.
7. A coloured bounding box is displayed.
8. Attendance is recorded automatically.
9. The web dashboard displays attendance details.

## 6. Face Detection and Identification

The system uses three identification conditions.

### Registered Person – SHASTHA

- Identifies the registered person as SHASTHA.
- Displays a GREEN bounding box.
- Displays the person's name and recognition score.

### Unknown Person

- Displays a RED bounding box.
- Shows the label UNKNOWN.
- Does not mark attendance.

### No Face Detected

- Displays NO FACE status.
- No attendance is recorded.

## 7. Attendance Management

The system automatically manages attendance using IN TIME and OUT TIME.

### Attendance Logic

- First successful recognition: Marks IN TIME.
- After a minimum interval of 5 minutes: Marks OUT TIME on subsequent recognition.
- After OUT TIME is recorded: No additional attendance entry is created for that day.
- Each person has one attendance record per day.

### Attendance Status

- PRESENT – Attendance recorded.
- ABSENT – No attendance recorded.

## 8. Seven-Day Attendance Monitoring

The dashboard maintains attendance information for the latest 7 days.

### Attendance Table

| Date | Name | IN TIME | OUT TIME | Status |
|---|---|---|---|---|
| Day 1 | SHASTHA | Recorded | Recorded | PRESENT |
| Day 2 | SHASTHA | Recorded | Not recorded | PRESENT |
| Day 3 | SHASTHA | - | - | ABSENT |
| Day 4 | SHASTHA | Recorded | Recorded | PRESENT |
| Day 5 | SHASTHA | - | - | ABSENT |
| Day 6 | SHASTHA | Recorded | Recorded | PRESENT |
| Day 7 | SHASTHA | Recorded | Not recorded | PRESENT |

The attendance records are maintained using `attendance.csv`.

## 9. Web Dashboard

The project provides a Flask-based web interface.

### Dashboard Features

- Live ESP32-CAM video streaming.
- Real-time face detection.
- Green box for registered faces.
- Red box for unknown faces.
- NO FACE detection status.
- Recognition score display.
- IN TIME and OUT TIME monitoring.
- Seven-day attendance history.

The dashboard uses AJAX to update status information without reloading the entire webpage.

## 10. Camera Configuration

**ESP32-CAM IP Address:**

`10.43.22.75`

**Camera Stream URL:**

`http://10.43.22.75:81/stream`

**Local Web Dashboard:**

`http://127.0.0.1:5000`

## 11. Project Folder Structure

```text
Face_Recognition_Attendance/
│
├── attendance_web_shastha_fixed.py
├── Shastha_face.npz
├── face_detection_yunet_2023mar.onnx
├── face_recognition_sface_2021dec.onnx
├── attendance.csv
│
└── README.md
```

## 12. Installation and Execution

### Step 1: Install Python Dependencies

```bash
pip install opencv-python
pip install numpy
pip install flask
```

### Step 2: Prepare Project Files

Place the following files in the same project folder:

- Python source code
- Face detection model
- Face recognition model
- Registered face dataset

### Step 3: Configure ESP32-CAM

Connect the ESP32-CAM to the network and verify the camera stream.

### Step 4: Run the Python Application

```bash
python attendance_web_shastha_fixed.py
```

### Step 5: Open the Web Dashboard

Open the browser and enter:
```text
http://127.0.0.1:5000
```
The live camera feed and face recognition results will be displayed.

## 13. Advantages

- Automated attendance monitoring.
- Contactless face recognition.
- Real-time person identification.
- Automatic IN and OUT time recording.
- Seven-day attendance tracking.
- Reduced manual attendance errors.
- Unknown person identification.
- Web-based monitoring.

## 14. Applications

- Educational institutions.
- Colleges and schools.
- Offices and companies.
- Industrial workplaces.
- Employee attendance monitoring.
- Laboratory access monitoring.

## 15. Future Enhancements

- Multiple student registration.
- Database integration using MySQL.
- Cloud-based attendance storage.
- Excel and PDF attendance reports.
- Email notifications.
- Mobile application integration.
- Multiple camera support.
- Advanced employee attendance analytics.

## 16. Author

**Developed By:** SHASTHA CHANDRU S

**Project Title:** ESP32-CAM Based Face Recognition Attendance Management System

**Technologies:** ESP32-CAM, Python, OpenCV, YuNet, SFace, Flask and NumPy.

---

## License

This project is developed for educational and research purposes.
<img width="700" height="1000" alt="esp_cam_project" src="https://github.com/user-attachments/assets/ec22a611-a37a-4496-97bb-612b037b36fd" />
