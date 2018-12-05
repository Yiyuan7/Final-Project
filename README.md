# Final-Project: Scroll Master



### Team: Hanyu Zhang, Yiyuan Feng

### Project Idea

For final project, we build a social media feed scrolling helper. With this helper system, users can scroll social media feeds using body gestures.

The goal of this project is to explore the relationship between human beings and technology, especially mobile devices. People today spend too much time on their phones. Researche shows that the average person spend over 4 hours on his/her phone each day. Thus, we want to create an interactive device that let users view their phones while getting some exercises done.

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
 Plan A: Users will interact with the webcam for pose input and the mechanical arm will be the form of output that interacts with the phone.
 
 Plan B: Users will interact with different types of sensor(e.g hearrate sensor, accelerometer), data will be transmitted to mechanical arm for interaction with the phone. 
 
### Progress 

## Devide and Conquer
# Gesture Recognition with Posenet

# Computer-Arduino Communication with JonnyFive, Express, and Node.JS

## Failures


## Plan A - Failure
 We have succesfully prototype gesture recognition using Posenet and webcam. We use nose and right wrist as two keypoints and calculate the relative position difference between current position and previous position to ouput "scroll up", "stay", and "scroll down". 

## Plan B 

### Final Product

## Architecture diagram

## Demo

 





