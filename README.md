# Final-Project: Scroll Master



### Team: Hanyu Zhang, Yiyuan Feng

### Project Idea

For final project, we build a social media feed scrolling helper. With this helper system, users can scroll social media feeds using body gestures.

The goal of this project is to explore the relationship between human beings and technology, especially mobile devices. People today spend too much time on their phones. Reseaches show that the average person spend over 4 hours on his/her phone each day. Thus, we want to create an interactive device that lets users view their phones while getting some exercises done.

The system will leverage PoseNet by Tensorflow to analyze gesture data that is captured by a webcam. The pose data is then used to control a mechanical arm, which interacts with the phone accordingly. For example, if user put his/her arms up, the mechanical arm will scroll up the social media feed.

### Paper Prototype

The paper prototype demonstrates the set up and interaction of our product idea. 
<p align="center">
<img width="750" src="https://github.com/Yiyuan7/Final-Project/blob/master/Presentation%20Sources/IMG_6602.JPG">
</p>


### Verplank Diagram 
<p align="center">
<img width="850" src="https://github.com/Yiyuan7/Final-Project/blob/master/Verplank.jpg">
</p>

### Expected Parts
 * USB Webcam
 * Arduino 
 * Servo Motors x2
 * Computer with a web browser
 * A Projector and screen(maybe) to display interaction on the phone

### Interaction Plan

Users will interact with the webcam for pose input and the mechanical arm will be the form of output that interacts with the phone.

### Progress 

Our product idea consists of both software and hardware components. For the software part, we will take advantage of PoseNet, a machine learning model, to generates pose estimation and calculate the changes between poses to output an action signal to hardware. For the hardware part, we will build a robotic arm that would swipe up and down the phone for users. 

#### Step 1: Gesture Recognition with Posenet

There are multiple ways to get data on gestures. When designing the product, we had to possible plans. Plan A is to get real-time data from gesture recognition machine learning models and plan B is to get data from sensors. The drawback of plan B is users need to wear sensors with wires all over the place. Thus, we decided to go with Plan A for a more seamless user experience. After some research, we found out PoseNet, which is machine learning model that returns a pose with confidence score and an array of keypoints, each with a score and position. We used the Tensorflow.js version of PoseNet so it fits into Node.js which is later used to communicate with Arduino. 

The idea is to identify three physical actions that correspond to three common actions people perform on the phone, namely swipe up, down, and like. We defined three keypoints and the following mappings:
 * Left hand up -> Swipe Up
 * Head down -> Swipe Down
 * Right hand up -> Like

We extracted x,y coordinates of these three keypoints and calculated the difference between previous position and current posision to identify a change in gesture. 

#### Step 2: Robotic Arm for Swiping 

The mechanical part of the product was to build a robotic arm to swipe the phone physically. The plan was to have one servo as a "wrist" sweeping a skylus and another servo to move the skylus up and down on the phone.

#### DIY stylus
 
We made our own stylus by using a cotton swap, aluminum foil paper, and water. We wrapped aluminum foil paper around the cotton swab and sticked two wires in. We then added a drop of water onto the tip of cotton swab to keep the skylus conductive.
 
 Demo: working stylus
  <p align="left">
  <img height = "400" src="https://github.com/Yiyuan7/Final-Project/blob/master/stylus.gif">
  </p>

 
#### Servo Movement
 
Our major challenge is to figure out the sequence of movements. We start with using servo.sweep and later figured out the flow of movement for two servos to work together. 
 
 Initial design of servo
 <p align="left">
 <img height = "400" src="https://github.com/Yiyuan7/Final-Project/blob/master/initial.jpg">
 </p>
 
 Final design of servo
 <p align="left">
 <img  width = "600" src="https://github.com/Yiyuan7/Final-Project/blob/master/final.JPG">
 </p>
 
 Sequence of servo movement
 <p align="left">
 <img  width = "600" src="https://github.com/Yiyuan7/Final-Project/blob/master/servo.JPG">
 </p>
 

#### Step 3: Computer-Arduino Communication with JonnyFive, Express, and Node.JS

Since results from step 1 are in browser, we wanted to establish the connection between browser and arduino so that gesture change can be used to control robotic arm. To achieve so, we used Johnny-Five framework to control Arduino with JavaScript. The overall architecture diagram is illustrated below.

#### Architecture diagram
<p align="left">
 <img  width = "800" src="https://github.com/Yiyuan7/Final-Project/blob/master/arch.png">
</p>


#### Step 4: Refining Interaction

When we first programmed the javascript, we wrote client.js to emit signals to server.js to trigger servo movement as soon as a gesture movement is detected. This created a problem for servos. If users move quickly and keep moving in a short amount of time, servos would not have enought time to complete the whole sequence of movement. Thus, we added a time counter in the program to tell Arduino that it only needs to execute one action in every 30s. We also adjusted how long each servo complete one action and calibrated the position of servos to make sure the swiping action goes well. 


#### Failures
* Originally, we planned to put everything in raspberry pi but it turned out be really slow. Thus, we decided to use computer instead.
* It took us a while to figure out the movement of servos. In the middle of the project, we implemented a software-heavy plan which let users to play a browser based game with gestures. The plan was dissuared by the teaching team.
* We wanted to design three actions for robotic arm, namely swipe up, swipe down, and like. We wanted to use a right thumb up for like. However, the like function works on and off. The like function is called, servo 2 will shake rapidly. We couldn't figure out the reason for this abnormal behavior in the end and decided to remove this action. 
* Demo: Like action  
  <p align="left">
  <img height = "300" src="https://github.com/Yiyuan7/Final-Project/blob/master/like.gif">
  </p>



### Final Product

#### Demo Video
[![](http://img.youtube.com/vi/tl9ORVKfWog/0.jpg)](http://www.youtube.com/watch?v=tl9ORVKfWog "")

#### Human Interaction Demo
[![](http://img.youtube.com/vi/bykkYmpXzU0/0.jpg)](http://www.youtube.com/watch?v=bykkYmpXzU0 "")
 





