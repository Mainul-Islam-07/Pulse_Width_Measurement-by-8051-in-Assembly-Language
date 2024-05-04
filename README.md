# Pulse_Width_Measurement-by-8051/8052-in-Assembly-Language
Microcontroller Programming using Assembly language to measure frequency , duty cycle and generate frequency (0-65536Hz)

The project is done both using proteus simulation as well as Using Hardware ( 8051 microcontroller Board )

![IMG (2)](https://github.com/Mainul-Islam-07/Pulse_Width_Measurement-by-8051-in-Assembly-Language/assets/78782260/66452286-26b4-43f3-8ff5-5c41cb072dfa)


The above figure contains the hardware required to run the tests as well as monitoring the outputs. This is like a testbench. Here link analyser is the alternate of using an oscilloscope as its too expensive . Arduino mega is used to generate frequencies and provide to the 8051 microcontroller board.


Features:

Mandatory Features:


1. Measure the frequency and duty cycle of a signal and display it on the
LCD. If it is less/more than 50Hz sound an alarm and specify the
difference on the LCD.


2. Take two signals, measure their frequencies and generate a new signal
equal to the sum of those frequencies.


3. Continuously carry out the above tasks and LED 1 should be turned on
when the first task is being carried out, and LED 2 should be turned on
when the second task is being carried on.

Optional Features:


1. The Microcontroller will run in 2 modes. One of them is trigger mode.
This feature can halt or pause the microcontroller from executing when
needed using external pins. This is done using 2 pins with spdt switches.
One switch halt the measuring of frequencies only but will be generating
frequency. The other switch will halt all process of the microcontroller by
infinitely looping.


2. 3 Led’s will blink depending upon the frequency of the second signal
being larger, equal or less than the frequency of the first signal.


![image](https://github.com/Mainul-Islam-07/Pulse_Width_Measurement-by-8051-in-Assembly-Language/assets/78782260/497ff916-a8fb-4e70-9860-699c6d62280a)



![image](https://github.com/Mainul-Islam-07/Pulse_Width_Measurement-by-8051-in-Assembly-Language/assets/78782260/c9c4ab1c-370a-4d80-b1e0-b4251d25a157)

Here, 1st external signal comes to Port P3.4. 2nd external signal comes to Port P3.5. Generated signal is passed out through Port P2.6. A buzzer is connected to Port P3.0. 
The port that is used to halt measuring frequencies is P3.3. Whereas the port that is used to halt everything is port P2.7. 

In simulation LED D0-D7 connected to port P1 but in hardware simulation, its Port P0. P2.0,P2.1,P2.2 are used for Controlling LED’s by connecting them to RS, RW and Enable pin of LED.
LED’s are connected in P2.3, P2.4, P2.5 and P3.1, P3.2. The first 3 LEDs indicates whether one frequency is greater , equal or smaller than the other one. The later two LEDs indicate the task 3 of mandatory features. 

A oscilloscope was used to check whether the generated signal matches with the expected signal.
The remaining connections are used to make the microcontroller running properly, like connecting oscillators with proper capacitor, power etc. 


Problems Faced but solved (or possible to solve) and tips :

1)	Had to figure out the memory location of the timer 2 , manually labelled the memory locations as mide doesn’t recognize their names; and used it accordingly. For this, we had to go through INTEL and ATMEL datasheet of 8052 microcontroller.

2)	When working with high frequencies (>10KHz) , using machine cycles for other purposes becomes significant in calculations (which we used to ignore but they do consume some machine cycles) and when calculations contain very less number of machine cycle , those unconsidered machine cycles ends up creating about 5% error in worst case scenario.
Eg. (10000hz shows 10010hz – 0.1 percent error) 

3)	When proteus crashes in middle of the work, the whole project files gets corrupted. Its better to make multiple iterations while working to be able to start working from the previous checkpoints.

4)	The closest machine cycle to represent one second using loop is 921660 machine cycles (14d*F004h) which is 2 machine cycle more than the actual 921658 machine cycles. So for large frequencies, creates about 3% error in worst case scenario.

5)	Hardware LEDs and alarms are active low. We used to forget that and had to debug for hours. It is very important to remember.

6)	Improper stack PUSH POP made debug a lot harder. 







