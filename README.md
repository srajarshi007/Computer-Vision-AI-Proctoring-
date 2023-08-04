# Proctoring-AI

Project to create an automated proctoring system where the user can be monitored automatically through the webcam and microphone. 


### Prerequisites
To run the programs in this repo, do the following:
- create a virtual environment using the command:
  - `python -m venv venv`
- activate the virtual environment
  - `cd ./venv/Scripts/activate` (windows users)
  - `source ./venv/bin/activate` (mac and linux users)
- install the requirements
  - `pip install --upgrade pip` (to upgrade pip)
  - `pip install -r requirements.txt`

Once the requirements have been installed, The programs will run successfully.
Except for the `person_and_phone.py` script which requires a model to be downloaded.

More on that later.


For vision:
```
Tensorflow>2
OpenCV
sklearn=0.19.1 # for face spoofing. 
The model used was trained with this version and does not support recent ones.
```
For audio:
```
pyaudio
speech_recognition
nltk
```


It has five vision based functionalities right now:
1. Track eyeballs and report if candidate is looking left, right or up.
2. Find if the candidate opens his mouth by recording the distance between lips at starting.
3. Instance segmentation to count number of people and report if no one or more than one person detected.
4. Find and report any instances of mobile phones.
5. Head pose estimation to find where the person is looking.


### Face detection
Earlier, Dlib's frontal face HOG detector was used to find faces. However, it did not give very good results. 

It is implemented in `face_detector.py` and is used for tracking eyes, mouth opening detection, head pose estimation, and face spoofing.


### Facial Landmarks
Dlib's facial landmarks model was used but it did not give good results when face was at an angle. 
It is implemented in `face_landmarks.py` and is used for tracking eyes, mouth opening detection, and head pose estimation.


### Eye tracking
`eye_tracker.py` is to track eyes. However, it was written using dlib.


### Mouth Opening Detection
`mouth_opening_detector.py` is used to check if the candidate opens his/her mouth during the exam after recording it initially. It's explanation can be found in the main article, however, it is using dlib which can be easily changed to the new models.


### Person counting and mobile phone detection
`person_and_phone.py` is for counting persons and detecting mobile phones. YOLOv3 is used in Tensorflow 2.


### Head pose estimation
`head_pose_estimation.py` is used for finding where the head is facing. 

