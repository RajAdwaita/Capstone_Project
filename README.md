# Yoga pose estimation and Rehabilitation using Google Mediapipe

- [Project summary](#project-summary)
  - [The issue we are hoping to solve](#the-issue-we-are-hoping-to-solve)
  - [How our technology solution can help](#how-our-technology-solution-can-help)
  - [Our idea](#our-idea)
- [Technology implementation](#technology-implementation)
  - [IBM watsonx product(s) used](#ibm-ai-services-used)
  - [Other IBM technology used](#other-ibm-technology-used)
  - [Solution architecture](#solution-architecture)
- [Presentation materials](#presentation-materials)
  - [Solution demo video](#solution-demo-video)
  - [Project development roadmap](#project-development-roadmap)
- [Additional details](#additional-details)
  - [How to run the project](#how-to-run-the-project)
  - [Live demo](#live-demo)
- [About this template](#about-this-template)
  - [Contributing](#contributing)
  - [Versioning](#versioning)
  - [Authors](#authors)
  - [License](#license)
  - [Acknowledgments](#acknowledgments)


## Project summary
The project aims to develop a real-time posture recognition and correction system that aids patients in completing workouts related to their ailment. This system uses computer vision and machine learning techniques to provide patients with automatic, precise, and real-time feedback while performing yoga. The system gathers accurate and inaccurate postures related to the chosen illness or condition, trains a posture detection model using this dataset, and guides the patient through recommended workouts. The system then acquires landmarks on the user's body to form a rough skeletal structure consisting of 33 points covering the entire body. The system calculates angles between certain parts of the body to determine if the yoga is being performed accurately.
The device continuously evaluates the patient's motions throughout yoga sessions and compares them to predetermined proper positions. An alert system is set off when deviations are found, providing instant input on how to fix their form. This feedback system ensures timely instruction for safe and efficient activities.
The user interface provides real-time feedback on yoga technique and progress, enabling patients to take charge of their own rehabilitation. The system aims to prove its effectiveness in enhancing yoga adherence, form correctness, and patient outcomes through extensive testing and validation, including user trials with patients and healthcare professionals.

### The issue we are hoping to solve
The aim of this project is to use computer vision technologies to construct a real- time posture identification and correction system. By helping patients complete their training and rehabilitation activities precisely and securely, this system hopes to improve the therapeutic results. The initiative aims to enable patients to take control of their own rehabilitation while guaranteeing appropriate exercise practices by offering automated supervision and feedback. The need for a technology that can let patients manage their own exercise regimens and rehabilitation program independently while providing the guidance and feedback they need to complete their activities correctly without any human supervision.

### How our technology solution can help
Google created the open-source MediaPipe framework, which lets programmers construct multimedia apps in real time for a range of platforms and gadgets. Advanced computer vision techniques and machine learning models are included, and they are utilized for tasks like position estimation, object identification, and facial recognition. These models are perfect for multimedia applications since they are real-time and very accurate. Additionally, MediaPipe has real-time performance-optimized computer vision algorithms for applications like segmentation, depth estimation, and image and video stabilization. Because the platform's pipeline is modular and easily extendable with custom components, developers may create highly customized applications using it.

### Our idea

When the user starts the system, he will be prompted to such a screen Fig – [2.4], where one has to enter the disease for which rehabilitation is needed. If the particular disease is present in the database, then on clicking the submit button, the list of yoga will be enabled. As soon as the user selects a particular yoga pose, an image demonstrating the pose will be made visible on the screen. Once the user knows how the pose is to be performed, he can click the proceed button, and the corresponding function will be triggered in the backend.
When an individual stands in front of the camera while the model is running, his video feed will be captured and converted into RGB format for processing.
The video input will be recorded using cv2 in order to utilise the MediaPipe Pose Estimation. If there is only one connected camera device, the address for video capture (address) is typically 0. Next, depending on how precise the findings should be, parameters for the pose estimation will be assigned. These parameters include tracking confidence, model complexity, on and off of the static picture mode, and minimum detection and on.

Then, as long as the camera is on or the video is playing, the programme will continuously read the frames from the video input. MediaPipe Pose will then process each frame one after the other to obtain the landmarks.
But before users can view and compare, the camera and video inputs must be visualised. The Red-Green-Blue in the pictures will need to be rearranged because it is actually in the Blue-Green-Red sequence. Additionally, the video will be mirrored for a better visualisation experience because the camera or video feed is not mirrored.

![Image Mediapipe Pose Landmark Map](https://camo.githubusercontent.com/54e5f06106306c59e67acc44c61b2d3087cc0a6ee7004e702deb1b3eb396e571/68747470733a2f2f6d65646961706970652e6465762f696d616765732f6d6f62696c652f706f73655f747261636b696e675f66756c6c5f626f64795f6c616e646d61726b732e706e67)

After processing this feed will be fed to Google Media Pipe, that will make use of the minimum detection and tracking confidence to perform pose estimation by calling the required methods from the pose() class.
The individual can typically be located using the Nose, which is the "landmark 0," which is returned by MediaPipe stance along with a stance prediction based on 33 landmarks. Using the posture landmark submodule, Google MediaPipe displayed the pose landmark graph. Cross-platform settings, such as static picture mode, model complexity, minimum detection confidence, and minimum tracking confidence, are provided by Google MediaPipe Pose and may be applied in many scenarios. For picture input, the static image mode may be turned on; for video stream inputs, it can be turned off.

The model's level of confidence in detecting and tracking the input is determined by the minimum detection and tracking confidence. We may set the minimum detection and tracking confidence with a lower value and set the model complexity configuration to "2" if the posture was very complicated, however this would slow down the procedure pace. Upon detecting the posture from the picture or frame, the model will return coordinates including its width, height, depth, and visibility.

The landmarks will be determined on the body of the user and displayed as live feed on the monitor. Then the user can perform the required yoga pose. A trigonometric function has been prepared that takes any three points as input and calculated the angles between them using the arctan2 function. During the training and the testing phase the angles formed by a certain set of points will be calculated to be used during the dynamic implementation.
While the user performs the yoga pose, the angles formed by the body points that are specifically required for this yoga will be displayed next to the point in the output. If the user is able to correctly perform the yoga, then “OK” will be displayed, otherwise, a sound alert will be triggered to make the user aware that he is out of form. Along with this, the confidence score will also be displayed so that the user can understand what percent of the 32 body points are being captured by the frame.



![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/4007d4df-1e80-41d3-9c68-b3a0315b6f4a)


More detail is available in our [description document](./docs/DESCRIPTION.md).

## Technology implementation

### Google Mediapipe 
A computer vision system using Google's MediaPipe technology for rehabilitation and training requires detailed technical specifications covering technologies, hardware requirements, software specifications, user interaction, and expected functionalities. In this section the requirements, technical , economic and social feasibility have been discussed. This comprehensive breakdown is essential for the project's success. In order to guarantee high accuracy, an excellent user experience, real-time performance, and dependability, the paper explores both functional and non-functional needs. The feasibility assessment confirms the project's viability and revolutionary potential by addressing its technical, economic, and social components. Along with standards and procedures to guarantee adherence to data protection and healthcare legislation, comprehensive hardware and software specifications are offered to steer development.

#### System Specification 
##### Hardware 
- Hardware for the system, such as cameras that can record clear video feeds for posture recognition and correction, is needed.
- Moreover, in order to execute the posture detection model and furnish the user with immediate feedback, computing devices possessing adequate processing capabilities are essential.
- System Requirement: Operating System: Windows 11, CPU: Intel(R) Core(TM) i7-10750H CPU @ 2.60GHz, RAM: 24 GB, and GPU: NVIDIA GeForce GTX 1650 Ti.
- High resolution webcam or integrated camera capable of capturing at least 720p video at 30 FPS.

##### Software
- The creation of the posture detection and correction algorithm utilising machine learning methods and the MediaPipe architecture is part of the software specs.
- To enable communication between the user and the system, an intuitive user interface must be created and put into use.
- Software Requirements : python >=3.8.0, mediapipe 0.8.9.1, opencv-python 4.5.5.62, pandas 1.4.1, and scikit-learn 1.0.2.
- Development Environment - PyCharm, Visual Studio Code, or any python supportive IDE.

## Design 

### System Architecture 
![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/c413c065-5682-406c-8be4-d10306f52c78)

### Data Flow Diagram
![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/85e9a147-d6b9-448c-ae7c-ac92b66b4672)

### Sequence Diagram 
![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/2982637f-1af4-423e-9ad7-f9b855306d88)

## Modules
### Module - 1
 - Capturing Frames through Dynamic/Manual Input
 - Segmentation
 - Converting frames to RGB
### Module - 2
- Acquiring landmarks using Media Pipe
- Drawing Landmark and connections on the video Feed
- Checking body pinpoint offset
- Calculating angles between reference points

     ![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/1d55b1cf-d8a0-461d-be96-bec702335b0d)
  
### Module - 3
- Decision Making


## Testing

### Unit - Testing
- Video Capture Feed
- 
    ![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/2e2cfc0d-232f-41da-87a6-96e0426cf0aa)
- Drawing landmark map on the body

    ![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/48efcfed-9c4f-4b92-92cf-b29432bc0634)
- Draw the landmark map on a 3-D plane

    ![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/ccacf309-2c9d-4724-b866-822477d56974)
### Integration Testing
- Calculating angles at the joints
  
    ![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/0e6d1de7-72ef-4326-a687-8319c40343fa)
- Testing the model


## Results and Discussions
### Confusion Matrix 
![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/6459a756-70fc-45f6-a7c7-3ad555aeef5b)


### Correct Pose for Adho Mukha Savasana
![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/9d9cab40-f90a-4597-a329-eee3f8045089)


### Incorrect Pose for Adho Mukha Savasana
![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/90e28106-442a-496c-acd6-eb551ba6d267)


### How to run the project

- Go To the Code_Base Folder
- Open the DEMO_MEDIAPIPE-FINAL file in an IDE that supports python
- Check that the path of the Audio file is set correctly
- Run the code line by line.
- In case any package / library is not installed, `!pip install (package_name)`
- If webcam permission is not enabled, enable it.
- Once the opening Page pops us, select the options and perform the Yoga pose to obtain the results.
  ![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/c86761a2-dce0-42e2-a044-bcad84020513)






### Live demo


### Authors

<a href="https://github.com/RajAdwaita">
  ADWAITA RAJ MODAK
</a>


