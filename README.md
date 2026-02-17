# 🔐 Secure Ultrasonic Distance Measurement using FPGA  
### Hardware Encryption + Hamming Error Detection + Custom UART (Vivado RTL Design)

![Vivado](https://img.shields.io/badge/Tool-Xilinx%20Vivado-blue)
![Language](https://img.shields.io/badge/Language-Verilog-green)
![Hardware](https://img.shields.io/badge/Platform-FPGA-orange)
![Communication](https://img.shields.io/badge/Protocol-UART-yellow)

---

## 📌 Abstract

This project implements a **secure ultrasonic distance measurement system** completely in hardware using Verilog HDL.  
The system measures distance using an HC-SR04 ultrasonic sensor, encrypts the measured data using a lightweight hardware encryption algorithm, applies **Hamming (12,8) error detection**, and transmits the protected data via a custom-designed UART transmitter.

The entire architecture is implemented in **Xilinx Vivado (RTL design)** without using any embedded processor.

---

## 🎯 Project Objectives

- Real-time ultrasonic distance measurement on FPGA  
- Lightweight hardware-friendly encryption implementation  
- Hamming (12,8) error detection capability  
- Custom UART transmitter with baud rate generator  
- Secure and reliable serial communication  

---


---

## ⚙️ Hardware Requirements

| Component | Description |
|------------|------------|
| FPGA Board | ZedBoard / 100 MHz FPGA board |
| Ultrasonic Sensor | HC-SR04 |
| USB-to-TTL Converter | For UART communication |
| Voltage Divider | Required for Echo pin (5V → 3.3V) |
| Jumper Wires | For connections |

---

## 🧠 Working Principle

### 1️⃣ Ultrasonic Measurement

- FPGA generates a **10 µs trigger pulse**
- Echo pulse width is measured using a 100 MHz clock counter
- Distance is calculated using:


---

### 2️⃣ Lightweight Encryption Algorithm

The 8-bit distance value undergoes:

1. Nibble swap  
2. Rotate left (2 bits)  
3. XOR with key `0x93`  
4. S-box substitution  
5. Rotate left (1 bit)  
6. Bit swap  
7. Final XOR with key `0xD2`  

✔ Fully combinational  
✔ Low resource usage  
✔ Hardware optimized  

---

### 3️⃣ Hamming (12,8) Error Detection

- 8-bit encrypted data  
- 4 parity bits added  
- Total 12-bit protected output  

Parity equations:

- P1 = d0 ⊕ d1 ⊕ d3 ⊕ d4 ⊕ d6
- P2 = d0 ⊕ d2 ⊕ d3 ⊕ d5 ⊕ d6
- P3 = d1 ⊕ d2 ⊕ d3 ⊕ d7
- P4 = d4 ⊕ d5 ⊕ d6 ⊕ d7

### Capabilities

- Detects single-bit errors  
- Corrects single-bit errors  
- Detects double-bit errors  

---

### 4️⃣ Custom UART Transmitter

- Baud Rate: **9600**
- Clock Frequency: 100 MHz
- Frame Format:
  - 1 Start bit
  - 8 Data bits
  - 1 Stop bit

Baud period calculation:


### Capabilities

- Detects single-bit errors  
- Corrects single-bit errors  
- Detects double-bit errors  

---

### 4️⃣ Custom UART Transmitter

- Baud Rate: **9600**
- Clock Frequency: 100 MHz
- Frame Format:
  - 1 Start bit
  - 8 Data bits
  - 1 Stop bit

### Baud period calculation:
--Bit_Period = 100,000,000 / 9600


Each reading represents:

Encrypted Distance + Hamming Protected Data

---

## 🔍 Design Highlights

- 100% RTL implementation  
- No embedded processor  
- Parallel encryption logic  
- Error detection capability  
- Modular and scalable design  

---

## 📊 Advantages

- Secure data transmission  
- Reliable communication  
- Low latency  
- Lightweight FPGA implementation  
- Suitable for IoT and embedded applications  

---

## ⚠ Limitations

- Custom encryption (not AES standard)  
- Single-bit error correction only  
- UART bandwidth limitations  

---

## 🔮 Future Improvements

- AES-128 hardware encryption  
- Hamming decoder implementation  
- CRC-based error detection  
- Wireless transmission (LoRa / WiFi)  
- LCD display integration  
- Zynq PS integration  

---

## 🚀 Applications

- Secure IoT sensor nodes  
- Industrial automation  
- Robotics systems  
- Defense monitoring  
- Embedded secure measurement devices  

---
 

---





