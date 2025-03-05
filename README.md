This program detects drowsiness using a webcam by analyzing whether a person’s eyes are open or closed. If the eyes remain closed for too long, it triggers an alarm and displays a visual alert.

🛠 Step-by-Step Explanation

1️⃣ Initialize System Components
pygame.mixer.init(): Initializes the sound system to play an alert sound.
Loads the pre-trained drowsiness detection model (drowsiness_detector.h5).
Loads Haar Cascade Classifiers to detect face, left eye, and right eye.

2️⃣ Capture Live Video from Webcam
cv2.VideoCapture(0): Opens the default webcam and starts reading frames.
Each frame is converted to grayscale (cv2.cvtColor) to improve detection accuracy.

3️⃣ Detect Face and Eyes in Each Frame
Haar cascades detect face, left eye, and right eye in the frame.
If an eye is detected, it is cropped, resized (24×24), normalized (0 to 1), and reshaped for the deep learning model.

4️⃣ Predict Eye Status (Open or Closed)
The deep learning model (drowsiness_detector.h5) takes the processed eye image as input and predicts whether it is open (1) or closed (0).
The program does this for both eyes separately.

5️⃣ Update the Drowsiness Score
If both eyes are closed, the score increases.
If any eye is open, the score decreases.
A higher score means the person has kept their eyes closed for too long.

6️⃣ Trigger Alarm for Drowsiness 🚨
If score >= alert_threshold (default 10), it does: 
✅ Saves an alert image (alert.png).
✅ Plays a warning alarm (alarm.wav).
✅ Displays a red warning border around the screen.
Otherwise, the score gradually resets.

7️⃣ Display Live Feedback on Screen
Shows real-time status: "Eyes Open" (green) or "Eyes Closed" (red).
Displays the Drowsiness Score in the corner.
If the user presses "q", the program exits safely.

The Drowsiness Detection System is a crucial safety solution for preventing accidents caused by driver fatigue. Using OpenCV, Deep Learning (CNN), and Haar Cascades, it monitors eye movements in real time and triggers an alarm if drowsiness is detected. This project has significant applications in road safety, fleet management, and workplace monitoring, reducing the risk of fatigue-related incidents. It is lightweight, efficient, and customizable, making it suitable for drivers, machine operators, and security personnel. With potential for mobile and IoT integration, this system can save lives by ensuring alertness during critical tasks. 
