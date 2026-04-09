# Pose-landmark-detection-system using mediapipe

An advanced computer vision application that detects, maps, and visualizes human body landmarks in real-time. This project processes both live webcam feeds and pre-recorded video files to accurately map human kinematics using state-of-the-art machine learning models.

​🚀 Project Overview
​Driven by a core interest in machine learning and data visualization, I designed and engineered this entire system from the ground up to explore real-time kinematic tracking. The project establishes a complete computer vision pipeline: capturing frame-by-frame video data, passing it through an asynchronous ML landmarker model, and mathematically mapping the output coordinates back onto the original frame to draw a dynamic skeletal wireframe.
​Whether it's tracking an athlete's form or analyzing yoga poses, this system independently handles the complex background threading and GUI rendering required for smooth, continuous video processing.

​✨ Key Features
​Real-Time Webcam Tracking: Seamlessly captures and processes live video using custom while loops optimized for immediate GUI feedback.
​Video File Processing: Iterates through pre-recorded .mp4 files, automatically calculating timestamps and scaling playback speed according to the source file's native FPS.
​Custom Visualization: Maps 33 distinct 3D body landmarks and actively draws customized connections (skeletal lines) and tracking points (colored dots) over the user's body.
​Robust Thread Management: Engineered to bypass standard GUI freezing issues (particularly on macOS) by tightly coupling the frame reading, ML detection, and OpenCV rendering steps within unified execution cells.

​🛠️ Tech Stack
​This project was developed entirely using:
​Python: The core programming language driving the logic and data flow.
​OpenCV (cv2): Utilized for video capture, frame manipulation, color space conversion (BGR to RGB), and real-time visual rendering.
​MediaPipe: Google's open-source ML framework, used here for its highly accurate, lightweight PoseLandmarker task.
​Jupyter Notebook: Used as the primary development environment for iterative testing and debugging.

​⚙️ How It Works (The Pipeline)
​Frame Capture: OpenCV initializes the VideoCapture object (either webcam 0 or a file path) and extracts frames continuously.
​Preprocessing: Frames are converted from OpenCV's default BGR format to the SRGB format required by the ML model.
​Detection: The image data, along with an auto-calculated timestamp, is fed into the MediaPipe Vision model.
​Coordinate Mapping: The ML model returns normalized coordinates (between 0.0 and 1.0). The script multiplies these by the actual frame height and width to get exact pixel locations.
​Rendering: cv2.circle() and MediaPipe's drawing_utils overlay the data onto the original frame before cv2.imshow() refreshes the screen.
