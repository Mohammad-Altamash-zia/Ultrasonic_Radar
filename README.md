# 📡 Autonomous Ultrasonic Radar Scanner

An autonomous 180-degree radar system that scans its surroundings, measures distances, and visualizes physical objects in real-time. 

This project bridges hardware and software by pairing an Arduino microcontroller with a custom Java-based graphic visualizer built in the Processing IDE. 

## 🚀 Demo
*(Include a screenshot or a GIF of your radar screen and hardware working here)*

## 🛠️ Hardware Stack
*   **Microcontroller:** Arduino Uno
*   **Sensor:** HC-SR04 Ultrasonic Sensor
*   **Actuator:** SG90 Micro Servo Motor
*   **Power Supply:** 7.2V Li-ion Battery Pack (2S)
*   **Misc:** Breadboard, Male-to-Male & Female-to-Male Jumper Wires

## ⚡ Engineering Note: Power Isolation
During initial testing, powering the SG90 servo directly from the laptop's USB port via the Arduino caused current spikes. This triggered a USB brownout, crashing the serial data transmission. 

**The Solution:** I implemented an isolated power delivery system. A separate 7.2V Li-ion battery pack is wired directly to the breadboard to power the servo motor (the "muscle"), while the Arduino (the "brain") is powered via USB. A common ground was established between the battery, breadboard, and Arduino, resulting in a perfectly stable data stream.

## 💻 Software Stack
*   **Embedded C/C++:** Runs on the Arduino to control the servo sweeps, calculate echo ping durations, and send `Angle,Distance.` packets over Serial communication.
*   **Java (Processing):** Reads the incoming serial data, parses the strings, and maps the coordinates to draw a real-time, sweeping green radar graphic that paints objects red upon detection.

## ⚙️ How to Run the Project
1.  **Hardware Assembly:** Connect the servo data pin to Digital Pin 10, the sensor Trig to Pin 8, and the sensor Echo to Pin 9. Ensure the 5V and GND rails are properly isolated and grounded.
2.  **Arduino Setup:** Open the `Arduino_Code` folder, upload the `.ino` sketch to your Arduino Uno via the Arduino IDE.
3.  **Processing Setup:** Open the `Processing_Code` folder, open the `.pde` sketch in the Processing IDE. 
4.  **Port Configuration:** Ensure the `myPort = new Serial(this, "COMX", 9600);` line in the Processing sketch matches your specific Arduino COM port.
5.  **Run:** Hit "Run" in Processing to launch the visualizer.

## 👨‍💻 About the Developer
**Mohammad Altamash Zia** 
Computer Science Engineering (Class of 2028) at Invertis University. 
Passionate about bridging software and the physical world through Robotics, IoT, and Embedded Systems.
