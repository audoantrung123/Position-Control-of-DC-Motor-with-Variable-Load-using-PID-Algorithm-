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

**PID Tuning**

**Goal:** To find the optimal values for the Proportional (Kp), Integral (Ki), and Derivative (Kd) gains in our PID controller, we aim to achieve the following:

* **Fast Rise Time:** The system should reach the target position quickly.
* **Minimal Overshoot:**  Avoid oscillations or excessive swings around the target position.
* **Quick Settling Time:** The system should stabilize at the target position rapidly.
* **Zero Steady-State Error:** Eliminate any remaining offset or difference between the desired and actual position.

**Manual Tuning:**

Here's a basic manual tuning process you can follow:

1. **Start with zero gains:**  Begin with Kp = 0, Ki = 0, and Kd = 0.
2. **Increase Kp:** Gradually increase the proportional gain (Kp) until you observe oscillations in the system's response.
3. **Dampen oscillations:** Reduce Kp slightly to dampen the oscillations.
4. **Reduce overshoot and settling time:** Increase the derivative gain (Kd) to further reduce overshoot and settling time.
5. **Eliminate steady-state error:** If a steady-state error persists, gradually increase the integral gain (Ki) to eliminate it.

**Influence of PID Gains on System Response**

This table summarizes the general effects of increasing the Proportional (Kp), Integral (Ki), and Derivative (Kd) gains on a system's response:

| Parameter | Rise Time | Overshoot | Settling Time | S.S. Error |
|---|---|---|---|---|
| Kp | Decrease | Increase | Small Change | Decrease |
| Ki | Decrease | Increase | Increase | Eliminate |
| Kd | Small Change | Decrease | Decrease | None    |

**Key Takeaways:**

* **Kp (Proportional Gain):**  Increasing Kp generally leads to a faster response (decreased rise time) but can also increase overshoot and make the system less stable. It helps reduce steady-state error.
* **Ki (Integral Gain):** Increasing Ki can eliminate steady-state error but may also increase overshoot and settling time.
* **Kd (Derivative Gain):** Increasing Kd helps reduce overshoot and settling time, improving system stability. It has a minor effect on rise time and no effect on steady-state error.

This table provides a general guideline for PID tuning. However, the optimal values for Kp, Ki, and Kd will depend on the specific characteristics of your system and the desired performance.

**To calculate the pulse frequency of Servo Motor, you can use the following formula:**

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


## 3. Hardware system and Program flow

**Components:**

* **STM32 Microcontroller:**  The brain of the system, running a PID control algorithm to precisely control the motor's position.
* **Encoder:** Provides feedback to the STM32 about the motor's actual position.
* **Servo Motor:**  Used to introduce a variable load, simulating real-world conditions where the load on the motor might change.
* **Qt C++ GUI:** A user interface on a PC for visualization and monitoring of the system's performance. This GUI displays data and graphs related to the motor's position, speed, and other parameters.

**Process:**

1. **Read Encoder Data:** The STM32 continuously reads data from the encoder to monitor the motor's current position.
2. **Calculate Motor Parameters:** The STM32 calculates important parameters like the motor's speed and acceleration based on the encoder data.
3. **Send Data to PC:**  The calculated parameters are sent from the STM32 to a PC via USART communication.
4. **Display Data and Graphs:** The Qt C++ GUI on the PC receives the data from the STM32 and displays it in a user-friendly way, including graphs that visualize the motor's performance.
   
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

<p align="center">
  <img src="https://github.com/user-attachments/assets/be4eb045-f384-428d-8f59-e25a1f70864e" width="50%" />
</p>
<p align="center"> Figure 6. Program Flow</p>

## 4. Result

<p align="center">
  <img src="https://github.com/user-attachments/assets/32eda0cc-affb-45f7-aa17-8e270d05e135" width="50%" />
</p>

<p align="center"> Figure 7. Initial setup interface for the system</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/2583d222-b73d-4278-9f45-33932420a836"  width="50%" />
</p>

<p align="center"> Figure 8. Results show current rotation angle values, errors and control signals</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/80ad47a6-55f2-4a9b-9f5d-edd25f1e9cb1" width="50%" />
</p>

<p align="center"> Figure 9. Actual running hardware</p>

## 5. Conclusion

This project presents the design and implementation of a variable load DC motor position control system using an STM32 microcontroller and a Qt C++ user interface. The system utilizes a PID algorithm to achieve precise and stable positioning of the DC motor to a predefined setpoint.
Experimental results demonstrate the stability and responsiveness of the designed control system under variable load conditions. The PID algorithm effectively adjusts the motor's input voltage to maintain accurate positioning while minimizing oscillations and settling time. The user interface is designed for simplicity and ease of use, enabling users to perform control operations and monitor system responses effectively.


