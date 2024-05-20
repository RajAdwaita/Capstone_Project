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

After processing this feed will be fed to Google Media Pipe, that will make use of the minimum detection and tracking confidence to perform pose estimation by calling the required methods from the pose() class.
The individual can typically be located using the Nose, which is the "landmark 0," which is returned by MediaPipe stance along with a stance prediction based on 33 landmarks. Using the posture landmark submodule, Google MediaPipe displayed the pose landmark graph. Cross-platform settings, such as static picture mode, model complexity, minimum detection confidence, and minimum tracking confidence, are provided by Google MediaPipe Pose and may be applied in many scenarios. For picture input, the static image mode may be turned on; for video stream inputs, it can be turned off.

The model's level of confidence in detecting and tracking the input is determined by the minimum detection and tracking confidence. We may set the minimum detection and tracking confidence with a lower value and set the model complexity configuration to "2" if the posture was very complicated, however this would slow down the procedure pace. Upon detecting the posture from the picture or frame, the model will return coordinates including its width, height, depth, and visibility.

The landmarks will be determined on the body of the user and displayed as live feed on the monitor. Then the user can perform the required yoga pose. A trigonometric function has been prepared that takes any three points as input and calculated the angles between them using the arctan2 function. During the training and the testing phase the angles formed by a certain set of points will be calculated to be used during the dynamic implementation.
While the user performs the yoga pose, the angles formed by the body points that are specifically required for this yoga will be displayed next to the point in the output. If the user is able to correctly perform the yoga, then “OK” will be displayed, otherwise, a sound alert will be triggered to make the user aware that he is out of form. Along with this, the confidence score will also be displayed so that the user can understand what percent of the 32 body points are being captured by the frame.

![Video transcription/translaftion app](https://developer.ibm.com/developer/tutorials/cfc-starter-kit-speech-to-text-app-example/images/cfc-covid19-remote-education-diagram-2.png)
![image](https://github.com/RajAdwaita/Capstone_Project/assets/76047644/48cc3d6b-176d-4a67-9734-8ff0e8e70c92)


More detail is available in our [description document](./docs/DESCRIPTION.md).

## Technology implementation

### IBM watsonx product(s) used

_INSTRUCTIONS: Included here is a list of IBM watsonx products. Remove any products you did not use. Leave only those included in your solution code. In your official submission on the Call for Code Global Challenge web site, you are required to provide details on where and how you used each IBM watsonx product so judges can review your implementation. Remove these instructions._

**Featured watsonx products**

- [watsonx.ai](https://www.ibm.com/products/watsonx-ai) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

- [watsonx.governance](https://www.ibm.com/products/watsonx-governance) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

- [watsonx Assistant](https://cloud.ibm.com/catalog/services/watsonx-assistant) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

### Other IBM technology used

INSTRUCTIONS: List any other IBM technology or IBM AI services used in your solution and describe how each component was used. If you can provide details on where these were used in your code, that would help the judges review your submission.

**Additional IBM AI services (Remove any that you did not use)**

- [Watson Machine Learning](https://cloud.ibm.com/catalog/services/watson-machine-learning) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

- [Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

- [Natural Language Understanding](https://cloud.ibm.com/catalog/services/natural-language-understanding) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

- [Speech to Text](https://cloud.ibm.com/catalog/services/speech-to-text) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

- [Text to Speech](https://cloud.ibm.com/catalog/services/text-to-speech) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

- [Language Translator](https://cloud.ibm.com/catalog/services/language-translator) - WHERE AND HOW THIS IS USED IN OUR SOLUTION

### Solution architecture

REPLACE THIS EXAMPLE WITH YOUR OWN, OR REMOVE THIS EXAMPLE

Diagram and step-by-step description of the flow of our solution:

![Video transcription/translaftion app](https://developer.ibm.com/developer/tutorials/cfc-starter-kit-speech-to-text-app-example/images/cfc-covid19-remote-education-diagram-2.png)

1. The user navigates to the site and uploads a video file.
2. Watson Speech to Text processes the audio and extracts the text.
3. Watson Translation (optionally) can translate the text to the desired language.
4. The app stores the translated text as a document within Object Storage.

## Presentation materials

_INSTRUCTIONS: The following deliverables should be officially posted to your My Team > Submissions section of the [Call for Code Global Challenge resources site](https://cfc-prod.skillsnetwork.site/), but you can also include them here for completeness. Replace the examples seen here with your own deliverable links._

### Solution demo video

[![Watch the video](https://raw.githubusercontent.com/Liquid-Prep/Liquid-Prep/main/images/readme/IBM-interview-video-image.png)](https://youtu.be/vOgCOoy_Bx0)

### Project development roadmap

The project currently does the following things.

- Feature 1
- Feature 2
- Feature 3

In the future we plan to...

See below for our proposed schedule on next steps after Call for Code 2024 submission.

![Roadmap](./images/roadmap.jpg)

## Additional details

_INSTRUCTIONS: The following deliverables are suggested, but **optional**. Additional details like this can help the judges better review your solution. Remove any sections you are not using._

### How to run the project

INSTRUCTIONS: In this section you add the instructions to run your project on your local machine for development and testing purposes. You can also add instructions on how to deploy the project in production.

### Live demo

You can find a running system to test at...

See our [description document](./docs/DESCRIPTION.md) for log in credentials.

---

_INSTRUCTIONS: You can remove the below section from your specific project README._

## About this template

### Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

### Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags).

### Authors

<a href="https://github.com/Call-for-Code/Project-Sample/graphs/contributors">
  <img src="https://contributors-img.web.app/image?repo=Call-for-Code/Project-Sample" />
</a>

- **Billie Thompson** - _Initial work_ - [PurpleBooth](https://github.com/PurpleBooth)

### License

This project is licensed under the Apache 2 License - see the [LICENSE](LICENSE) file for details.

### Acknowledgments

- Based on [Billie Thompson's README template](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2).
