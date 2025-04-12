---
title: Welcome
tags:
---

# EGR 314 - Embedded System Design Project II

---

![](pcb-board.jpg)

## STEM Weather Station Project

**Team Number:** 303  

**Team Members:** Cade Clonts, Jahmel Garduno, Daniel Resnick

**Preparation Date:** Febuary 21, 2025  

**Semester and Year:** Spring 2025  

**University:** Arizona State University 

**Professor:** K. Nichols

## EGR314 Spring 2025 Project Summary

---

This semester, teams will design and build an interactive, web-enabled STEM-themed display that demonstrates a scientific or engineering concept. The intended audience is K-12 students, and projects must be modular, standards-based, and capable of communication over a custom UART daisy chain network.

Each team member is responsible for designing an individual PCB-based subsystem, contributing to one of four key functions:

**Sensing** – Gathering data from sensors via SPI/I2C

**Actuation** – Controlling an output device via SPI/I2C

**Human-Machine Interface (HMI)** – Displaying system data & user control via OLED/pushbuttons

**Internet Communication** – Enabling bidirectional data transfer via MQTT or an approved alternative

Teams must use Cadence or Altium for PCB design and follow strict surface-mount component requirements. Individual subsystems must function independently before integrating into the team's daisy chain network, ensuring proper data handling and hardware safety.

Final Deliverables Include:

**Individual:** A complete "datasheet" with schematics, PCB layout, software, and API documentation

**Team:** A system-level design report, team repository, and a fully functional integrated system

**Final Demo:** Teams will showcase their project at the Innovation Showcase on May 2, 2025

The project emphasizes hands-on engineering, modular design, embedded systems, and real-time communication, preparing students for practical challenges in electrical and computer engineering.

### __Team Role__

---

My role in the team is the bidirectional internet communication subsystem using MQTT protocol. For this subsystem, I will be using an ESP32-S3-WROOM-1-N4 module mounted on a custom PCB. This system will facilitate communication between the sensor, actuator, and human interface subsystems through UART connections. A UART connection will also be implemented for the human interface, complementing the wireless interface device that communicates over the MQTT protocol. This subsystem will be responsible for sending and receiving data over MQTT with the human interface device and transferring sensor and actuator data. My focus will be on maintaining smooth and reliable data flow across the system, enabling precise interaction between the different subsystems.

### __Links__
Name | Link
-----|------------
Team Website   | [link](https://egr314-2025-s-303.github.io/EGR314-2025-S-303/)
Cade Clonts   | [link](https://cclonts2.github.io/)
Jahmel Garduno | [link](https://jahmelg10.github.io/)
Daniel Resnick | [link](https://drez85.github.io/)

### __My Assignments__
Assignment | Link
-----|------------
Block Diagram   | [link](https://cclonts2.github.io/block-diagram/)
Component Selection | [link](https://cclonts2.github.io/component-selection/)
Schematic Design | [link](https://cclonts2.github.io/board-design/Index/)
