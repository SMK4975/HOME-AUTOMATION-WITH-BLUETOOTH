# HOME-AUTOMATION-WITH-BLUETOOTH

*COMPANY*: CODTECH IT SOLUTIONS

*NAME*: SEEPANA MURALIKRISHNA

*INTERN ID*: CT08DF1739

*DOMAIN*: EMBEDDED SYSTEMS

*DURATION*: 8 WEEKS

*MENTOR*: NEELA SANTOSH

# 📱 Task 2: Home Automation Using Bluetooth (Simulated in Wokwi)

## 📘 Objective

The aim of this project is to design and simulate a **Bluetooth-controlled home automation system** using an **Arduino Uno**. The project allows a user to control electrical devices (represented by LEDs) using command-based inputs. Since direct Bluetooth simulation is not supported in Tinkercad or Wokwi, we simulate the **Bluetooth HC-05 module** using **Serial Monitor input**, which mimics the commands a Bluetooth app would send to an Arduino. The core goal is to show how devices can be controlled wirelessly with simple serial commands, making the system ideal for controlling lights, fans, or appliances remotely via mobile apps or terminals.


## 💻 Software Used

* **Wokwi Arduino Simulator** – A free, browser-based online Arduino simulator. It allows for real-time simulation of Arduino hardware and code execution. While it does not directly support HC-05 Bluetooth modules, it allows us to simulate the behavior using the built-in Serial Monitor.
* **Arduino IDE Syntax** – The code is written using the standard Arduino C/C++ syntax, compatible with the Arduino IDE.


## 🧰 Components Used

| Component                 | Quantity    |
| ------------------------- | ----------- |
| Arduino Uno               | 1           |
| LED (to simulate devices) | 2           |
| 220Ω Resistor (for LEDs)  | 2           |
| Breadboard (optional)     | 1           |
| Jumper Wires              | As required |

> Note: The HC-05 Bluetooth module is **not available** in Wokwi. Instead, we simulate it using Wokwi's **Serial Monitor** to send commands.


## 🔌 Circuit Connections

Two LEDs are used to simulate devices (e.g., a bulb and a fan). These are connected to digital pins of the Arduino as outputs.

### LED Connections

| LED  | Anode (+) → Arduino Pin | Cathode (–) → GND via Resistor |
| ---- | ----------------------- | ------------------------------ |
| LED1 | D2                      | GND with 220Ω resistor         |
| LED2 | D3                      | GND with 220Ω resistor         |

### Arduino Power

* 5V and GND rails are connected internally in Wokwi (no external power source needed).

No Bluetooth module is physically connected, as **Serial Monitor** is used for input.


## 🧠 Working Principle

In a real-world home automation system using the HC-05 Bluetooth module, the Arduino listens for incoming characters via serial communication and triggers devices accordingly. In this simulation, the **Serial Monitor** is used to send the same characters that a Bluetooth app would transmit.

When a user types a specific character (e.g., 'A', 'a', 'B', or 'b') into the Serial Monitor and hits Enter, the Arduino receives it through the `Serial.read()` function. Based on the command:

* `A` turns ON device 1 (LED1)
* `a` turns OFF device 1 (LED1)
* `B` turns ON device 2 (LED2)
* `b` turns OFF device 2 (LED2)

The Arduino then sets the appropriate pin HIGH or LOW to switch the device on or off. This simulates wireless control over home appliances using command-based serial communication.


## 💻 Arduino Code

```c
char data = 0;

void setup() {
  Serial.begin(9600);      // Initialize Serial Monitor
  pinMode(2, OUTPUT);      // Device 1 (LED)
  pinMode(3, OUTPUT);      // Device 2 (LED)
  Serial.println("Bluetooth Automation Ready");
}

void loop() {
  if (Serial.available()) {
    data = Serial.read();

    if (data == 'A') {
      digitalWrite(2, HIGH);  // Turn ON LED1
    } else if (data == 'a') {
      digitalWrite(2, LOW);   // Turn OFF LED1
    } else if (data == 'B') {
      digitalWrite(3, HIGH);  // Turn ON LED2
    } else if (data == 'b') {
      digitalWrite(3, LOW);   // Turn OFF LED2
    }
  }
}
```


## 🧪 Simulation Output

When the simulation runs in Wokwi:

* Sending `A` in the Serial Monitor turns ON LED1.
* Sending `a` turns OFF LED1.
* Sending `B` turns ON LED2.
* Sending `b` turns OFF LED2.

This behavior mimics how an Arduino would behave with a real Bluetooth module receiving commands from a mobile app.


## ▶️ Steps to Simulate in Wokwi

1. Visit [https://wokwi.com/](https://wokwi.com/)
2. Click **“Start New Project”** and select **Arduino Uno**
3. Add 2 LEDs and connect:

   * LED1 anode → D2, cathode → GND via 220Ω resistor
   * LED2 anode → D3, cathode → GND via 220Ω resistor
4. Paste the provided code into the code editor.
5. Click **“Start Simulation”**
6. Open the **Serial Monitor** tab at the bottom
7. Type the following commands one at a time and press Enter:

   * `A` → LED1 ON
   * `a` → LED1 OFF
   * `B` → LED2 ON
   * `b` → LED2 OFF


## 🎯 Final Notes

This project demonstrates how home automation can be implemented using serial communication with Arduino. While physical Bluetooth modules like HC-05 are not available in Wokwi, the system logic and code remain the same. The project uses simple character-based commands to turn devices on and off, showing how digital output pins can be used to control home appliances. The simulation is ideal for educational purposes, showcasing Bluetooth logic without needing external hardware. The code is written in C using the Arduino IDE’s structure and fully compatible with real-world deployment by replacing the Serial Monitor with a Bluetooth terminal.
