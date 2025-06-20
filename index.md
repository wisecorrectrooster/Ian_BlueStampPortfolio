# Rock Paper Scissors
Replace this text with a brief description (2-3 sentences) of your project. This description should draw the reader in and make them interested in what you've built. You can include what the biggest challenges, takeaways, and triumphs from completing the project were. As you complete your portfolio, remember your audience is less familiar than you are with all that your project entails!


You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Ian C. | Northgate High School |STEM| 9th grader

<img src="IanC.jpg" width="50%" height="50%">
  
# Final Milestone <!--- DIDNT DO -->

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone   <!--- DIDNT DO -->

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/y3VAmNlER5Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal
- What has been surprising about the project so far
- Previous challenges you faced that you overcame
- What needs to be completed before your final milestone 

# First Milestone

<iframe width="560" height="315" src="https://www.youtube.com/embed/SNgfvdcwz_M?si=wfufoF-CKIxGiGew" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

  My project is a rock paper scissors machine where it randomly chooses one of the servos to spin. It will then have a popsicle stick attached to it with a rock, paper, or scissor drawn on it. I chose this project as it was interesting looking and around my level. So far, I learned how to code Arduino in which I made it spin one of the three servos randomly. It works when something is 20 centimeters or less and the servos spin with a popsicle stick attached to it. For some reason, the code doesn't run unless it is connected to the computer thorough a USB cable. The next step for me is to have the code automatically run without it having to be wired to my computer.


# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser. 


# Code

```c++
#include <Servo.h>


// HC-SR04 sensor pins
#define TRIG_PIN 12
#define ECHO_PIN 11


// Servo objects
Servo servo_3;
Servo servo_6;
Servo servo_9;


void setup() {
 Serial.begin(9600);


 // Sensor pins
 pinMode(TRIG_PIN, OUTPUT);
 pinMode(ECHO_PIN, INPUT);


 // Attach servos
 servo_3.attach(3);
 servo_6.attach(6);
 servo_9.attach(9);


 // Set to neutral
 servo_3.write(90);
 servo_6.write(90);
 servo_9.write(90);


 randomSeed(analogRead(0)); // Seed random
}


void loop() {
 float distance = readDistance();


 Serial.print("Distance: ");
 Serial.print(distance);
 Serial.println(" cm");


 // Only trigger servo if distance is valid and <= 20
 if (distance > 0 && distance <= 20) {
   int randomServo = random(1, 4); // 1 to 3


   switch (randomServo) {
     case 1:
       servo_3.write(179);
       delay(1000);
       servo_3.write(90);
       break;


     case 2:
       servo_6.write(179);
       delay(1000);
       servo_6.write(90);
       break;


     case 3:
       servo_9.write(179);
       delay(1000);
       servo_9.write(90);
       break;
   }


   delay(500); // Short pause after action
 }


 delay(200); // General delay between checks
}


// Reads distance in cm
float readDistance() {
 digitalWrite(TRIG_PIN, LOW);
 delayMicroseconds(2);
 digitalWrite(TRIG_PIN, HIGH);
 delayMicroseconds(10);
 digitalWrite(TRIG_PIN, LOW);


 long duration = pulseIn(ECHO_PIN, HIGH, 30000); // 30ms timeout
 if (duration == 0) return -1; // No echo


 float distance = duration * 0.0343 / 2;
 return distance;
}

```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |


# Starter Project
First ever project, where I learned how to solder and how lightbulbs work. The sliders choose intensity of the 3 different lightbulbs in the LED and change its color. I put the LED the the wrong way and this caused the green slider to not work. After a couple minutes of trying, no one could remove it. Although the green slider doesn't work, the colors still change when I move the sliders.

<img src="IMG_5720.jpeg" width="50%" height="50%">
