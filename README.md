Abstract 
Any computer needs a mouse, which is a necessary addition. It is a Human-Computer Interaction innovation. In general, two types of computer mice are on the market: wired and wireless. Both versions make use of additional hardware and battery power. The implemented virtual mouse will replace the physical mouse, and the only hardware requirement is a webcam, albeit most PCs already have one built in. The webcam records the hand gestures, and computer vision is used to identify the fingertips and other hand landmarks. The computer cursor then executes the desired actions in accordance with the hand movement.

Introduction
Traditional mouse devices come with extra hardware components that must be carried around with the computer and connected each time, whether wired or wireless. Some but not most computers come with a touch screen. This virtual mouse is presented as a remedy for this issue. This virtual mouse, based on computer vision, may be used whenever the computer is turned ON and takes the place of the physical mouse without altering the internal hardware configuration of the computer.
Python is the basis for the artificial intelligence (AI) digital mouse source code, and Pycharm IDE is utilized to create the solutions. The two most essential packages for this project are OpenCV and Mediapipe. In addition, the packages math, time, pyautogui and numpy, and are used. To recognize hand gestures and features (landmarks of the hand), use the mediapipe program. It can instantly recognize 21 3D hand landmarks from a single frame. Images are captured and processed using the OpenCV library.


Methods 

The project's basic steps are listed below;
•	Frames from the webcam's video feed are retrieved.
•	Identification of the hands and their initial position; estimation of the palm's bounding boxes.
•	Recognizing landmarks of the hand.
•	Using the "click" and "move mouse pointer" functions.

Two modules are used: 
•	Hand Tracking 
o	Initialization.
o	Finding hand-point positions 
o	Hand Detection
o	Find the number of raised fingers.
•	Virtual Mouse 
o	Mouse Pointer Movement 
o	Clicking function



Hand Tracking module
Initialization
 
The following parameters are initialized at initialization.

static_image_mode – The program processes the supplied pictures like a video stream if false is selected. The first input photographs will attempt to find hands; if successful, it will further localise the hand landmarks. The ideal way to handle a batch of static, potentially unrelated photographs is to set the value of hand detection to true, which runs on every incoming image.

MAX_NUM_HANDS - Maximum hands to be detected.

MIN_DETECTION_CONFIDENCE - The hand detection model must produce a minimum confidence value of [0.0, 1.0] before the detection can be deemed successful.

MIN_TRACKING_CONFIDENCE - The hand landmarks must have a minimum confidence value ([0.0, 1.0]) from the landmark-tracking model to be regarded as successfully tracked. Otherwise, hand detection will be automatically activated on the input image afterwards.
The media pipe (MULTI_HAND_LANDMARKS) produced a list of 21 hand landmarks, each comprising the letters x, y, and z. The width and height of the image normalise x and y to [0.0, 1.0]. The origin of the landmark depth, denoted by the letter z, is the depth at the wrist.


Hand detection
 
This method involves the identification of 21 hand landmarks and the drawing of links between them. The RGB image was created from the original BGR format. Each coordinate (x, y, and z coordinates) is extracted, and the results are run through a "for loop" several times. The procedure gave back the hand's recognized image.



Position detection
 
 
This method returns the hand landmarks' location in relation to the width and height of the taken image and the limits of the identified hand (as a rectangle). In the following phases, the x and y values (cx, cy) are utilized to specify the precise locations of the fingertips.





Fingers movement
 
Raised fingers are recognized using this technique. If the thumb finger is lifted, the x coordinates between landmarks 3 and 4 (thumb finger) are used to determine this. Other fingers' y coordinates are used to determine if they are elevated.
 
The procedure finally produces a list of binary values associated with the fingertips (finger raised or not).
 


Distance detection
 
The length between the two fingertips that are provided, along with their x and y coordinates about the width and height of the photographed object, are returned by this method. The "click" operation uses this length in the following stages.
















Virtual Mouse
This module carries out the mouse function. In addition to the packages used in the hand-tracking module, the "pyautogui" package is utilised to automate mouse control during hand-tracking module interactions.

 
The image's dimensions captured are wCam and HCam, respectively.

 

To save recorded video, an object called "cap" is defined. The video frames' width and height are indicated by "cap.set"'s IDs 3 and 4.
The "hand Tracking Module" is defined as the "detector" of an object. The pyautogui.size() method returns the wScr and hScr dimensions of the screen resolution. The curser's movement can be more fluid using the Smooth, pLocX, pLocY, clocX, and clocY variables.




The index and middle fingers' coordination is then determined as follows:
 
Curser moving mode:
First, check whether only the index finger is raised; Convert the coordinates of the tip of the index figure to the ratio of the screen. Then the cursor is moved using "pyautogui.moveTo()" method.
 

The "clicking" action is performed with both the index and middle fingers. The left clicking feature is enabled when the distance between the tips of those two fingers is less than the present value. The right clicking feature is enabled when the index, middle and ring finger is raised. The double-clicking feature is enabled when the thumb and index finger is raised.
 

Results
Hand Tracking
•	Hand detection with landmarks.
•	Detecting positions (landmarks)
 
 
 

•	Detecting raised fingers
 
 
 







•	Identifying the distance between the middle finger and index finger
 

Virtual Mouse 



Conclusions and Future Work

The hand tracking and virtual mouse modules made up the main parts of this project. Programming is done using OOP. The hand's position is determined from the video feed's image frames, and the hand's 21 landmarks are then used to derive the fingertips' coordinates. Cursor movement and clicking actions are done by the fingertips (Index and Middle figure).

The following difficulties are noted throughout the project:
•	Smoothing cursor movement
•	Smaller icon clicks
