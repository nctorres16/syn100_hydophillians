# ECE 16 HW2 Report
Prepared by: Norberto Torres Date: 04/12/2023

__Objective__

The objective of this homework is to go further than the basics of Arduino which we did in the last homework, working with leds and the serial monitor. The homework lets us explore more on the analog side of Arduino with sensors, an OLED display, a buzzing motor, and also how to incorporate sampling into our sensors. The following tutorials and challenges will go indepth with these concepts and components.

**Challenge 1**

For this challenge, we have to build a gesture detector using the accelerometer to see whether the accelerometer is up, down, or in a shaking motion. 

1. The logic of the algorithm consist of three conditions that we look at to tell what state is which. The condtitions either focuses on the position of the z-axis the accelerometer is on, which determines whether the state is rightside up or upside down, or focuses on the rate of change the accelerometer changes position with respect to time. I figured out the rate of change to see when the accelerometer is staying still or is in motion which determines whether it is shaking or not. 

2. To get to this algorithm, I had to perform different tests using the accelerometer to distinguish which state is which. For the first test that I performed was when the accelerometer is still to test when it is either rightside up or upside down. What I did to perform this test was to keep track of the values of the axis through a graph and at first keep the accelerometer still then flip it to the next state. Through this test I found that only one axis is what help differentiates the two gestures, which was the vertical z-axis. The GIF shows the first test performed.

![GIF](./Fig/c1_first_test.gif)

The second test was to check how when it is in a shaking motion. The test performed was doing the shaking motion and observing from the graph of the axis to see what is happen. The takeaway from this test was that the shaking gesture depends on the movement of the accelerometer so when the values of the accelerometer changes. The GIF shows the second test performed.

![GIF](./Fig/c1_second_test.gif)

The third test was to debug the shaking condition of the algorithm. What happens at this part of the process was that the when fliping the accelerometer, so going from up to down, the algorithm treats this flipping motion as a shaking motion. So to debug this algorithm, I keep flipping to adjust the values of my variable "deltaTime" and also the values of the derivative for each axis. One thing that I got from this test was that to help the algorithm differentiate from flipping to shaking, I made my algorithm ignore the rate of change for the vertical z-axis and by this it made my algorithm less sensitive to vertical motion. The GIF below shows the third test performed. 

![GIF](./Fig/c1_third_test.gif)

3. Two things that can confuse my algorithm would be when whether I am shaking or flipping the accelerometer and also differentiating a small shake versus a big shake. I think that my algorithm incorporates fast movements as my way of determining shaking. I used this rate of change and changed the parameters to adjust the difference between still and zero motion and when there is motion. I debugged the part of differentiating when is it flipping or when it is shaking. However, the parameters of the conditions when measuring the rate of change of the axises can be high enough where small shakes are not incorporated to the shaking gestures. 

4. 
![GIF](./Fig/c1.gif)

The GIF above is the full test of this challenge.

**Challenge 2**

For this challenge, we have to build a timer where we can add time with a button, a buzzer when the timer goes to 0, and a button that will reset the buzzer after buzzing and the timer to 0. 

1. The image below is the full finite state machine of the code for this challenge.

![IMAGE](./Fig/c2_FSM.jpg)


2. The GIF below shows the sequence of adding 5 seconds to the timer, then letting it count to 0, then the motor buzzes, then we press the reset button.

![GIF](./Fig/c2_part_1.gif)


3. The GIF below shows the sequence of adding 10 seconds to the timer, then letting it count to 5, then pressing the reset button which should reset the timer to 0.

![GIF](./Fig/c2_part_2.gif)

4. The GIF below shows the sequence of pressing the reset button when the timer is 0, then adding 5 seconds to the timer, then letting it count to 0, then letting the motor buzz, then pressing the reset button to stop the motor.

![GIF](./Fig/c2_part_3.gif)

5. The GIF below shows the sequence of adding 10 seconds to the timer, then letting it count to 5 seconds, then add another 5 seconds, then letting it count down to 0, then the motor buzzes, then we press the reset button to stop the motor from buzzing.

![GIF](./Fig/c2_part_4.gif)

**Challenge 3**

For this challenge, we created a prototype design, using a cup, of a gestured controlled timer. In the code, we incorporated parts our gesture detection and timer designs from previous challenges. The design condition goes as follows, if the cup is up then no buttons are pressed and usually the timer will start to countdown. If the cup is down, then the timer will start counting up a second for every 300ms. Then if we shake the cup, the timer will reset to 0 and the buzzer motor will turn off. 

1. The images below show the design of the cup gestured controlled timer. In the bottom of the cup, the accelerometer is placed there where it is going to be stationary rightside up when the lip of the cup is facing the ground and when the base of the cup is facing the ground, the accelerometer is going to be upside down. The OLED display is placed in a hole of the side of the cup to see the timer value and the buzzer motor is sticked on the inside of the cup. Everything else like the breadboard, the arduino nano, and the battery pack are all stuffed inside of the cup. 

![IMAGE](./Fig/Norberto_Torres_Outside.jpg)

The image above is the outside view of the design for the gesture controlled timer. 

![IMAGE](./Fig/Norberto_Torres_Inside.jpg)

The image above is the inside view of the design for the gesture controlled timer. 

2. The GIF below shows the sequence of adding 5 seconds to the timer, then letting it count to 0, then the motor buzzes, then we shake the cup to reset.

![GIF](./Fig/c3_part_1.gif)

 The GIF below shows the sequence of adding 10 seconds to the timer, then letting it count to 5, then shaking the cup which would reset the timer to 0.

![GIF](./Fig/c3_part_2.gif)

 The GIF below shows the sequence of shaking the cup when the timer is 0, then adding 5 seconds to the timer, then letting it count to 0, then letting the motor buzz, then shaking the cup to stop the motor.

![GIF](./Fig/c3_part_3.gif)

 The GIF below shows the sequence of adding 10 seconds to the timer, then letting it count to 5 seconds, then add another 5 seconds, then letting it count down to 0, then the motor buzzes, then we shake the cup to stop the motor from buzzing. 

![GIF](./Fig/c3_part_4.gif)

3. The motor buzzer on and vibrating did not cause any problems with the gesture detection because the code implemented for this design has been debugged to the point to adjust to the sensitivity of the shaking motion and the flipping motion of the gesture detector. Therefore, by adjusting these things, the vibration of the cup caused by the motor buzzer does not cause any problem to the design.