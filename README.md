# TV_time_tracking_face_recognition

Wonder how much time we spend watching TV!
This project aims to build a tracker that measures the time registered family members spend watching TV. Developed on top of [Keras-OpenFace](https://github.com/iwantooxxoox/Keras-OpenFace) (a project converting OpenFace from its original Torch implementation to a Keras version), this tracker learns the faces by ***one-shot learning*** (single picture with a frontal face is required for database registration) and recognizes the registered members who are facing a camera mounted on the TV to enable a timer. When TV is on and whenever the tracker recognizes faces looking toward it, an individual timer gets enabled for that person(s).
***
The OpenFace model was trained by minimizing the triplet loss of multiple triplet pairs of images. Given three images ('anchor': reference, 'positive': same person and 'negative': different person), the training is done so as to achieve:

**d(A,P) - d(A,N) + α < 0**, where d() is the similarity function of the two vectors and α is an arbitrary margin that makes sure the model learns something other than all 0s.

Once the model learns so that the resulting 128D vector represents the good encoding of input, the deployment of this model requires a single image example to learn about that person (one-shot learning). Given K numbers of individuals are registered in a database, a new input face is firstly embedded into the 128D vector and compared to the pre-embedded database faces in a 1:K manner. 
***

## [TV_time_tracking_face_recognition Version 3 (TTT_v3)](https://github.com/Matthew-AI-Dev/TV_time_tracking_face_recognition/blob/master/TV_time_tracking_face_recognition_v3.ipynb)
Multi-face recognition on a video: based on the images stored in the database, TTT_v3 successfully recognizes registered faces on a video with great accuracy. In TTT_v3, the blue bounding boxes (for unregistered faces and falsely-detected faces) are not tracked as they are not needed for the purpose of the developing TV time tracker. Compared to TTT_v2, most helper functions were re-written for clarity and efficiency.

---
### Upcoming for future TTT
* the model will be implemented to a real-time module. 
* the device will be mounted on a TV for a demo!
---
## [TV_time_tracking_face_recognition Version 2 (TTT_v2)](https://github.com/Matthew-AI-Dev/TV_time_tracking_face_recognition/blob/master/TV_time_tracking_face_recognition_v2.ipynb)
Multi-face recognition on an image: based on the images stored in the database, TTT_v2 successfully recognizes registered faces on an image with great accuracy. TTT_v2 also differentiates registered faces from unregistered ones.


## [TV_time_tracking_face_recognition Version 1 (TTT_v1)](https://github.com/Matthew-AI-Dev/TV_time_tracking_face_recognition/blob/master/TV_time_tracking_face_recognition_v1.ipynb)
Single face recognition on an image: based on the images registered in the database, TTT_v1 successfully recognizes the face of the same person.

