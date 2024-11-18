# DC MOTOR POSITION CONTROL CHANGING LOAD USING PID ALGORITHM
An Off-policy Reinforcement Learning Algorithm for Optimal Tracking Control Problem

Full report: [link](https://drive.google.com/drive/folders/19ZD4xyNkR37CUa6bdA6HGHrCjVmCD2ta?usp=drive_link)

## 1. Introduction

In modern life, the control of DC motor position with variable load is a topic of broad interest across numerous fields, from industrial manufacturing, automation, and robotics to applications in healthcare and sports. A precise, reliable, and user-friendly DC motor position control system with variable load can improve the efficiency and accuracy of these applications. Therefore, the team decided to research and write a report on this topic. We designed and built a DC motor position control system with variable load using the STM32 microcontroller, combined with a display interface for output response using QT C++. The team focused on the following objectives:

- Designing a DC motor control circuit to achieve high accuracy and stability.
- Designing a user interface to display the output response of the system.
- Designing a variable load mechanism for the system.
- Testing the accuracy and stability of the system.

## 2. PID Control and Software

In my project, PID controller is used to control the position of DC motor. Specifically, it will calculate the error between the desired position and the actual position of the motor, then adjust the input voltage of the motor to bring the motor to the desired position accurately and stably.

$$u(t) = K_p.e(t) + K_i \int e(t)d(t) + K_d.\frac{d(e(t))}{dt}$$

To calculate the pulse frequency of Servo Motor, you can use the following formula:

Pulse Frequency = 1 / Pulse Cycle
With a pulse cycle of 20ms, the pulse frequency will be:

Pulse Frequency = 1 / 0.02 = 50 Hz
To calculate the pulse width, you can use the following formula:

Pulse Width = (Desired Angle / Total Angle Range) x (Max Pulse Width - Min Pulse Width) + Min Pulse Width
Where:

Desired Angle is the angle you want to rotate the servo motor to.
Total Angle Range is the angular range that the servo motor can rotate (in this case, it is 180 degrees).
Max Pulse Width is the pulse width corresponding to 180 degrees (in this case, it is 2ms).
Min Pulse Width is the pulse width corresponding to 0 degrees (in this case, it is 1ms).

## 3. Hardware system

<p align="center">
  <img src="https://github.com/user-attachments/assets/1eec4d1a-2fbc-46e0-b3fa-c31df2fa5529" />
</p>

<p align="center"> Figure 1. The 3D system design in Inventor</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/4e20bc5c-0c7e-48ad-9bf6-a4696ad50060" width="60%" />
</p>

<p align="center"> Figure 2. System components</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/8235b476-d0d3-4436-afeb-358fd1032b96" width="50%" />
</p>

<p align="center"> Figure 3. Load change mechanism</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/0e65de56-d5d3-4a19-9347-9ec5d2337e22" />
</p>

<p align="center"> Figure 4. System wiring diagram</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/24799d60-d711-469d-a77b-96073e96cff6" width="50%" />
</p>

<p align="center"> Figure 5. Actual system model</p>


## 4. Result

<p align="center">
  <img src="https://github.com/user-attachments/assets/32eda0cc-affb-45f7-aa17-8e270d05e135" width="50%" />
</p>

<p align="center"> Figure 6. Initial setup interface for the system</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/2583d222-b73d-4278-9f45-33932420a836"  width="50%" />
</p>

<p align="center"> Figure 7. Results show current rotation angle values, errors and control signals</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/80ad47a6-55f2-4a9b-9f5d-edd25f1e9cb1" width="50%" />
</p>

<p align="center"> Figure 8. Actual running hardware</p>

## 5. Conclusion

This project presents the design and implementation of a variable load DC motor position control system using an STM32 microcontroller and a Qt C++ user interface. The system utilizes a PID algorithm to achieve precise and stable positioning of the DC motor to a predefined setpoint.
Experimental results demonstrate the stability and responsiveness of the designed control system under variable load conditions. The PID algorithm effectively adjusts the motor's input voltage to maintain accurate positioning while minimizing oscillations and settling time. The user interface is designed for simplicity and ease of use, enabling users to perform control operations and monitor system responses effectively.

# Links to the example headings above

Link to the sample section: [Link Text](#sample-section).

Link to the helpful section: [Link Text](#thisll--be-a-helpful-section-about-the-greek-letter-Θ).

Link to the first non-unique section: [Link Text](#this-heading-is-not-unique-in-the-file).

Link to the second non-unique section: [Link Text](#this-heading-is-not-unique-in-the-file-1).
