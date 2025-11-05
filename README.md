# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.
  <img width="558" height="401" alt="image" src="https://github.com/user-attachments/assets/115dade6-103d-408a-9872-0aef88a9f0ea" />

2. Click **File → New STM32 Project**.
   <img width="1616" height="829" alt="image" src="https://github.com/user-attachments/assets/8bd9a8cd-ee56-4e72-975f-ecabbb8b57f6" />

<img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/edf33429-8eea-4857-a991-c2d7706fc787" />

3. Select the **target microcontroller** or board and click **Next**.
   



4. Name the project.
   <img width="589" height="666" alt="image" src="https://github.com/user-attachments/assets/398ff2fe-9739-459d-a278-f0a24580fe87" />


5. The corresponding `.ioc` file will be generated automatically.
  <img width="1561" height="833" alt="image" src="https://github.com/user-attachments/assets/fe9c060e-3581-41f8-a63b-7c74332cc278" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/acc4f1c4-5e33-431b-8a76-3b102016baa6" />
<img width="1486" height="848" alt="image" src="https://github.com/user-attachments/assets/6611051e-fdeb-4563-9b8f-36bc8649ee43" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  <img width="1088" height="723" alt="image" src="https://github.com/user-attachments/assets/b379470a-0eb5-47fd-9097-aa15f09f7ca7" />

 
8. Edit the generated main program as required.
   <img width="1138" height="631" alt="image" src="https://github.com/user-attachments/assets/5a3cd4b4-ae39-48bf-a4ac-e63cfba70895" />

9. Click **Project → Build All**.
<img width="860" height="379" alt="image" src="https://github.com/user-attachments/assets/4664e5a2-0ec9-4eeb-941e-873a30f36c2c" />

10. Link the **HEX file** using the post-build process.
    <img width="1053" height="465" alt="image" src="https://github.com/user-attachments/assets/478187a0-0ee6-4c50-9cac-c3b5ee18521b" />

11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/7fab887a-a72e-4162-b0a6-415fb7fbcbff" />
    <img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/d8cc0baf-d092-42e6-9a45-86ae2ea4b8b9" />

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
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

CASE 2: LED OFF

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




