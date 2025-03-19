---
title: Welcome
tags:
---

# EGR 314 - Embedded System Design Project II

![](learn-embedded-system-design.jpg)

## STEM Weather Station Project

**Team Number:** 303  

**Team Members:** Cade Clonts, Tyler Dean, Jahmel Garduno, Daniel Resnick

**Preparation Date:** Febuary 21, 2025  

**Semester and Year:** Spring 2025  

**University:** Arizona State University 

**Professor:** K. Nichols

### __Team Role__
My role in the team is the bidirectional internet communication subsystem using MQTT protocol. For this subsystem, I will be using an ESP32-S3-WROOM-1-N4 module mounted on a custom PCB. This system will facilitate communication between the sensor, actuator, and human interface subsystems through UART connections. A UART connection will also be implemented for the human interface, complementing the wireless interface device that communicates over the MQTT protocol. This subsystem will be responsible for sending and receiving data over MQTT with the human interface device and transferring sensor and actuator data. My focus will be on maintaining smooth and reliable data flow across the system, enabling precise interaction between the different subsystems.

### __Links__
Name | Link
-----|------------
Team Website   | [link](https://egr314-2025-s-303.github.io/EGR314-2025-S-303/)
Cade Clonts   | [link](https://cclonts2.github.io/)
Tyler Dean | [link](https://ty-357.github.io/)
Jahmel Garduno | [link](https://jahmelg10.github.io/)
Daniel Resnick | [link](https://drez85.github.io/)

### __My Assignments__
Assignment | Link
-----|------------
Block Diagram   | [link](https://cclonts2.github.io/charts/)
Component Selection | [link](https://cclonts2.github.io/component-selection/)
Schematic Design | [link](https://cclonts2.github.io/board-design/Index/)


### __Code__

-[code1](code-blink-time-output.txt)
-[code2](code-duty-cycle.txt)


#include "mcc_generated_files/mcc.h"

uint16_t time_ms = 0; uint16_t time_s = 0; float time = 0; uint8_t duty_cycle = 50; // Start at 50% duty cycle

void timer_callback(void){ time_ms++; if (time_ms >= 1000) { time_ms -= 1000; time_s++; IO_RD2_Toggle(); } }

void update_pwm_duty(uint8_t duty) { if (duty > 100) duty = 100; // Limit max duty cycle if (duty < 0) duty = 0; // Limit min duty cycle }

void pin_up(void){ if (duty_cycle < 100) { duty_cycle += 5; update_pwm_duty(duty_cycle);

    // Debugging message
    char buffer[32];
    sprintf(buffer, "Duty Up: %d%%\n", duty_cycle);
    for (int i = 0; buffer[i] != '\0'; i++) {
        putch(buffer[i]);  
    }
}
}

void pin_down(void){ if (duty_cycle > 0) { duty_cycle -= 5; update_pwm_duty(duty_cycle);

    // Debugging message
    char buffer[32];
    sprintf(buffer, "Duty Down: %d%%\n", duty_cycle);
    for (int i = 0; buffer[i] != '\0'; i++) {
        putch(buffer[i]);  
    }
}
}

/* Main application */ void main(void) { // Initialize the device SYSTEM_Initialize(); EUSART2_Initialize(); // Initialize EUSART2 for serial communication

IOCCF1_SetInterruptHandler(pin_up);
IOCCF2_SetInterruptHandler(pin_down);

// Enable global interrupts and peripheral interrupts
INTERRUPT_GlobalInterruptEnable();
INTERRUPT_PeripheralInterruptEnable();

TMR2_SetInterruptHandler(timer_callback);
TMR2_Start();
update_pwm_duty(duty_cycle); // Set initial PWM value

// Debugging: Confirm initialization
char init_msg[] = "System Initialized\n";
for (int i = 0; init_msg[i] != '\0'; i++) {
    putch(init_msg[i]);
}

while (1)
{
    time = time_s + (time_ms / 1000.0);
    
    // Prepare the time string
    char buffer[32];
    sprintf(buffer, "t= %.2fs\n", time);

    // Send the time string over UART
    for (int i = 0; buffer[i] != '\0'; i++) {
        putch(buffer[i]);  
    }

    __delay_ms(500);
}
}
