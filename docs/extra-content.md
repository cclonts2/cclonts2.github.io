



#include "mcc_generated_files/mcc.h"

uint16_t time_ms = 0;
uint16_t time_s = 0;
float time = 0;
uint8_t duty_cycle = 50;  // Start at 50% duty cycle

void timer_callback(void){
    time_ms++;
    if (time_ms >= 1000) {
        time_ms -= 1000;
        time_s++;
        IO_RD2_Toggle();
    }
}

void update_pwm_duty(uint8_t duty) {
    if (duty > 100) duty = 100;  // Limit max duty cycle
    if (duty < 0) duty = 0;      // Limit min duty cycle
}

void pin_up(void){
    if (duty_cycle < 100) {
        duty_cycle += 5;
        update_pwm_duty(duty_cycle);
        
        // Debugging message
        char buffer[32];
        sprintf(buffer, "Duty Up: %d%%\n", duty_cycle);
        for (int i = 0; buffer[i] != '\0'; i++) {
            putch(buffer[i]);  
        }
    }
}

void pin_down(void){
    if (duty_cycle > 0) {
        duty_cycle -= 5;
        update_pwm_duty(duty_cycle);
        
        // Debugging message
        char buffer[32];
        sprintf(buffer, "Duty Down: %d%%\n", duty_cycle);
        for (int i = 0; buffer[i] != '\0'; i++) {
            putch(buffer[i]);  
        }
    }
}

/*
                         Main application
 */
void main(void)
{
    // Initialize the device
    SYSTEM_Initialize();
    EUSART2_Initialize(); // Initialize EUSART2 for serial communication
    
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
