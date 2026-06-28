Chassis: DFRobot Pirate 4WD  https://www.dfrobot.com/product-97.html

Controller: DFRobot RoMeo v1.3  https://www.dfrobot.com/product-656.html

Design Notes:

Note 01:

The Arduino Uno (via the ATmega328P microcontroller) has three internal hardware timers. When you use  and the Servo library together, they consume these timer resources, which can restrict which pins can be used simultaneously.

Timer Allocation:

• Timer 0: Used by core functions like delay(), millis(), and micros().
• Timer 1: Used by the Servo library to generate precise 50Hz signals (usually controlling up to 12 servos). 
• Timer 2: Used by the tone() function, but otherwise manages general hardware PWM.

How They Affect Your Pins 
Because the Servo library overrides Timer 1, it directly disables standard  (PWM) functionality on the pins tied to that timer. 

• Pins Affected by Servo: Pins 9 and 10. You cannot use  on these pins while a servo is attached. 
• Safe Pins for : You can safely use  on Pins 3, 5, 6, and 11. 
• Safe Pins for Servos: You can connect servos to any digital pin (0-13 or analog A0-A5), but it's highly recommended to avoid Pins 9 and 10 so you don't lose half of your PWM capability. [1, 2, 4, 5, 7]  

Would you like to see a sample code sketch for running both simultaneously, or are you trying to troubleshoot a specific issue where your servos are jittering? Let me know and we can dive into it. 
AI responses may include mistakes.

[1] https://forum.arduino.cc/t/what-timers-and-ressources-use-analogwrite/395028
[2] https://forum.arduino.cc/t/servo-with-analogwrite/438505
[3] https://medium.com/vicara-hardware-university/arduino-timers-interrupts-9887e300ef57
[4] https://controllerstech.com/arduino-pwm-analogwrite-tutorial/
[5] https://www.instructables.com/Arduino-Timers-8-Projects/
[6] https://forum.arduino.cc/t/how-does-arduino-control-a-servo-motor-technical-qn/146826
[7] https://forum.arduino.cc/t/using-analogwrite-with-servo/573565

