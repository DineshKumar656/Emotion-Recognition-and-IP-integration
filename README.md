## Usage Examples

### 1. Real-Time Emotion Recognition from Webcam

This example captures video from your webcam and performs emotion recognition on each frame using the `facial_emotion_recognition` library.

```python
from facial_emotion_recognition import EmotionRecognition
import cv2

er = EmotionRecognition(device='cpu')
cam = cv2.VideoCapture(0)

while True:
    success, frame = cam.read()
    frame = er.recognise_emotion(frame, return_type='BGR')
    cv2.imshow("Frame", frame)
    key = cv2.waitKey(1)
    if key == 27:  # Press ESC to exit
        break
cam.release()
cv2.destroyAllWindows()
```

---

### 2. Stream Video from an IP Camera

This example shows how to read and display frames from an IP camera using OpenCV and `imutils`. No emotion recognition is performed here.

```python
import urllib.request
import cv2
import numpy as np
import imutils

url = 'http://192.168.1.7:8080/shot.jpg'

while True:
    imgPath = urllib.request.urlopen(url)
    imgNp = np.array(bytearray(imgPath.read()), dtype=np.uint8)
    frame = cv2.imdecode(imgNp, -1)
    frame = imutils.resize(frame, width=450)
    cv2.imshow("Frame", frame)
    if ord('q') == cv2.waitKey(1):  # Press 'q' to exit
        exit(0)
```

---

### 3. Emotion Recognition on IP Camera Stream

This example streams video from an IP camera and applies emotion recognition to each frame.

```python
from facial_emotion_recognition import EmotionRecognition
import urllib.request
import cv2
import numpy as np
import imutils

er = EmotionRecognition(device='cpu')
url = 'http://192.168.1.8:8080/shot.jpg'

while True:
    imgPath = urllib.request.urlopen(url)
    imgNp = np.array(bytearray(imgPath.read()), dtype=np.uint8)
    frame = cv2.imdecode(imgNp, -1)
    frame = er.recognise_emotion(frame, return_type='BGR')
    frame = imutils.resize(frame, width=500)
    cv2.imshow("Frame", frame)
    key = cv2.waitKey(1)
    if key == 27:  # Press ESC to exit
        break

cv2.destroyAllWindows()
```

---

**Note:**  
- Make sure you have the required dependencies installed: `facial_emotion_recognition`, `opencv-python`, `imutils`, and `numpy`.
- Replace the IP address in the `url` variable with your own IP camera's address.
- For emotion recognition, ensure your webcam or IP camera provides a clear frontal view of faces.

demo:
<img width="1919" height="1079" alt="Screenshot 2025-09-28 180018" src="https://github.com/user-attachments/assets/940fcf81-e3c8-4331-8fce-9cb8fb6655cd" />
<img width="1891" height="1079" alt="Screenshot 2025-09-28 180028" src="https://github.com/user-attachments/assets/fd3d0d44-fd3b-4560-846a-b4fc2bfc8f89" />
<img width="1282" height="1076" alt="Screenshot 2025-09-28 180048" src="https://github.com/user-attachments/assets/98533076-874b-498b-a28c-7a296340e59a" />
<img width="1286" height="1049" alt="Screenshot 2025-09-28 180107" src="https://github.com/user-attachments/assets/10d8c44a-53d1-45e1-8845-f01b27439d28" />
<img width="1269" height="1036" alt="Screenshot 2025-09-28 180125" src="https://github.com/user-attachments/assets/1ec34741-1a14-4d71-9b18-c816433f5e6f" />
<img width="1253" height="1053" alt="Screenshot 2025-09-28 180145" src="https://github.com/user-attachments/assets/96033360-d3ed-45b3-96d2-dd7d5babb5dc" />
<img width="1267" height="1042" alt="Screenshot 2025-09-28 180159" src="https://github.com/user-attachments/assets/2c2e96d4-0a3b-49db-89d5-a43a18824da1" />






