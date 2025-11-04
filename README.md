# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
<img width="1920" height="1140" alt="Screenshot 2025-11-03 140814" src="https://github.com/user-attachments/assets/c9a10dd6-b0c8-4fb8-98b4-e7771aa08ee2" />

2. Click **File → New STM32 Project**.
<img width="1920" height="1140" alt="Screenshot 2025-11-03 141246" src="https://github.com/user-attachments/assets/c12722ca-2fbb-4c96-bdb4-2a86ad480f4b" />
<img width="1920" height="1140" alt="Screenshot 2025-11-03 141343" src="https://github.com/user-attachments/assets/b8483b88-2070-407a-9a91-639fd1008fed" />


3. Select the **target microcontroller** or board and click **Next**.
<img width="1920" height="1140" alt="Screenshot 2025-11-04 193237" src="https://github.com/user-attachments/assets/e4b67867-2f84-4c81-8536-2edcc3f1b0e7" />



4. Name the project.
<img width="1920" height="1140" alt="Screenshot 2025-11-04 193305" src="https://github.com/user-attachments/assets/22f5196e-3e8d-4c47-8e25-4673a170e48e" />

5. The corresponding `.ioc` file will be generated automatically.
<img width="1920" height="1140" alt="Screenshot 2025-11-04 200819" src="https://github.com/user-attachments/assets/97c416d9-64af-4d89-a1b2-f871368bce56" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="1920" height="1140" alt="Screenshot 2025-11-04 201253" src="https://github.com/user-attachments/assets/900505b1-b2a0-4b3c-87fb-0281fc65103f" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/62e86363-3808-49f2-a3d6-73ba4b446595" />
 
8. Edit the generated main program as required.
<img width="1920" height="1140" alt="Screenshot 2025-11-04 201441" src="https://github.com/user-attachments/assets/7c60ec57-a25e-400d-84fb-6668f6baec0a" />


9. Click **Project → Build All**.
<img width="1920" height="1140" alt="Screenshot 2025-11-04 201519" src="https://github.com/user-attachments/assets/d3573460-4f7c-441d-a784-483f26971b02" />

10. Link the **HEX file** using the post-build process.
<img width="1920" height="1140" alt="Screenshot 2025-11-04 201631" src="https://github.com/user-attachments/assets/ddc73179-9e3a-45e2-afb0-9559d8cc66ea" />

11. Click **Debug** and connect the **STM Nucleo Board**.
<img width="1920" height="1140" alt="Screenshot 2025-11-04 202650" src="https://github.com/user-attachments/assets/a9b57f72-cfd0-4b51-bd2e-244d29f42b52" />

13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/8582090e-eea5-4185-8468-77c061ba8b35" />


CASE 2: LED OFF

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/006e007c-daf2-4546-a93d-206b0b41b1f3" />


---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
