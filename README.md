# 7-SEGMENT-DISPLAY-Digital-CLOCK-
Make a 7 real time clock with seven segment display with ardunio 
7-Segment Digital Clock with 12/24 Hour Mode (Arduino)

Description

This Arduino project displays real-time clock values (hours, minutes, seconds) on a 6-digit 7-segment common-anode display.

The clock runs using the Arduino’s internal millis() function as a timer.

It supports both 12-hour and 24-hour formats, toggled using an external interrupt (push button).

Time can be set via Serial input in the format: HH:MM:SS.

After setting, the clock continues running automatically.

A colon (decimal point) is used for separating hour/minute and minute/second sections.


Hardware Requirements

Arduino Uno (or compatible board)

6-digit 7-segment common-anode display

8 segment pins (a,b,c,d,e,f,g,dp) connected to digital pins 3–10

6 digit select pins connected to analog pins A0–A5

Push button connected to pin 2 (with INPUT_PULLUP) for switching 12/24-hour mode


How It Works

1. Time Setting via Serial:
Send HH:MM:SS over Serial (9600 baud). The code converts it to milliseconds and starts the timer.


2. Time Counting:
Uses Arduino's millis() to calculate elapsed time (readTime = millis() / 1000).
Automatically resets after 24 hours (if (millis() >= 86400000)).


3. 12/24 Hour Switch:
Interrupt (attachInterrupt) toggles state between 12-hour and 24-hour format.


4. Display Multiplexing:
Each digit is updated in quick succession using segOutput(), creating the illusion of all digits being on simultaneously.



Functions

segClear() – Turns off all segments.

segOutput(d, Number, dp) – Displays a single digit with optional decimal point.

switchFn() – Interrupt handler to toggle between 12/24 hour modes.


Why Output Screenshot is Not Available

The code was originally written and tested on an online Arduino simulation platform (e.g., Tinkercad/Wokwi), where it successfully executed and displayed the clock output as expected.
However, the project was not saved on the platform at that time, so the simulation file and its direct output are unavailable now.

We are manually re-applying the same code on hardware (or another environment) to replicate the results. The core logic remains unchanged, and the output is the same as previously achieved:

The 6-digit 7-segment display correctly showed HH:MM:SS.

The 12/24-hour mode switching worked via the interrupt button.

Time counting and updating worked as intended.

