# EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT

### Aim:
To Interface a push button and generate an interrupt , simulate it using an led and simuate it on  proteus 

### Components required:
STM32 CUBE IDE, Proteus 8 simulator .

### Theory:

ARM v7 Core supports multiple great features for handling exceptions and interrupts. Which includes the Nested Vectored Interrupt Controller (NVIC).

Micro-Coded Architecture So that interrupt stacking, entry, and exit are done automatically in hardware. Which offloads this work overhead from the CPU
### Processor Mode

The processor mode can change when exceptions occur. And it can be in one of the following modes:
Thread Mode: Which is entered on reset.
Handler Mode: Which is entered on all other exceptions.
<img src="https://github.com/vasanthkumarch/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/36288975/4f52f2d6-4cdb-4315-b2b2-b55dc1639c43" alt="Interrupt Generation Circuit" width="500" />
The STM32 ARM microcontroller interrupts are generated in the following manner:

The system runs the ISR and then goes back to the main program. The NVIC and EXTI are configured. The Interrupt Service Routine (ISR) also known as the interrupt service routine handler is defined to enable the external interrupts.

Let us learn about the important features which are needed to configure external interrupts in STM32 microcontrollers

Interrupt Lines (EXTI0-EXTI15)
The STM32 ARM microcontroller features 23 event sources which are divided into two sections. The first section corresponds t external pins on each port which are P0-P15. The second section corresponds to RTC, ethernet, USB interrupts. Therefore, in the first section, we have 16 lines corresponding to line0 till line15. All of these map to a pin number.
The diagram below shows how the GPIO pins are connected to the 16 interrupt lines:

<img src="https://github.com/vasanthkumarch/EXPERIMENT-06-INTERRUPT-GENERATION-USING-PUSHBUTTON-AND-SIMULATING-THE-OUTPUT-/assets/36288975/3e1ededb-144c-4103-a64e-9132b7e06e1b" alt="Interrupt Generation Circuit" width="500" />

One important thing to note here is that same number pins are connected to line with the same number. All of these then join to form a single line. Additionally, we can not use two pins one one line at the same time. For example out of PA1, PB1, PC1, PD1, PE1, PF1 and PG1 you can only use a single pin out of all these. This is because they are all connected to the same line EXTI1. However you can use PA1 and PA2 at the same time as they are connected with different lines.

Now each of these lines EXTI0-EXTI15 can be used to trigger an interrupt on different modes of the signal : rising edge, falling edge or rising_falling edge.


<h2>Procedure:</h2>

<p>1. Click on STM32 CUBE IDE, the following screen will appear:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png" width="500" />

<p>2. Click on FILE, click on new STM32 project:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png" width="500" />
<img src="https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png" width="500" />

<p>3. Select the target to be programmed as shown below and click on next:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189280-ed5dcf1d-dd8d-43ae-815d-491085f4863b.png" width="500" />

<p>4. Select the program name:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png" width="500" />

<p>5. Corresponding IOC file will be generated automatically:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189378-3abbdee2-0df6-470f-a3cd-79c74e3d3ad8.png" width="500" />

<p>6. Select the appropriate pins as GPIO, input or output, USART or required options and configure:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189403-f7179f1a-3eae-4637-826b-ab4ec35ba1e1.png" width="500" />
<img src="https://user-images.githubusercontent.com/36288975/226189425-2b2414ce-49b3-4b61-a260-c658cb2e4152.png" width="500" />

<p>7. Click on Ctrl+S, automatically C program will be generated:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189443-8b43451d-0b14-47e4-a20b-cc09c6ad8458.png" width="500" />
<img src="https://user-images.githubusercontent.com/36288975/226189450-85ffa969-2ffb-4788-81e5-72d60fdda0f1.png" width="500" />

<p>8. Edit the program as per the requirements:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png" width="500" />

<p>9. Select EXTI pin configuration and clock configuration:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png" width="500" />

<p>10. Once the project is built:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png" width="500" />

<p>11. Click on the Debug option:</p>
<img src="https://user-images.githubusercontent.com/36288975/226189625-37daa9a3-62e9-42b5-a5ce-2ac63345905b.png" width="500" />

<h2>Creating Proteus Project and Running the Simulation</h2>

<p>12. Create a new Proteus project and place STM32F40xx (i.e., the same MCU for which the project was created in STM32Cube IDE).</p>
<p>13. After creating the circuit as per requirement as shown below:</p>
<img src="https://user-images.githubusercontent.com/36288975/233856847-32bea88a-565f-4e01-9c7e-4f7ed546ddf6.png" width="500" />

<p>14. Double click on the MCU part to open settings. Next to the Program File option, give the full path to the Hex file generated using STM32Cube IDE. Then set the external crystal frequency to 8M (i.e., 8 MHz). Click OK to save the changes.</p>

<p>15. Click on Debug and simulate using the simulation option as shown below:</p>
<img src="https://user-images.githubusercontent.com/36288975/233856904-99eb708a-c907-4595-9025-c9dbd89b8879.png" width="500" />



  

## STM 32 CUBE PROGRAM :
```c
/* Name:Abdur Rahman Basil A H
Register Number:212223240002 */
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
	if((GPIO_Pin == GPIO_PIN_0)){
		HAL_GPIO_TogglePin(GPIOA,GPIO_PIN_5);
	}
}
```


<h2>Output Screenshots of Proteus:</h2>

<h3>Trigger 1:</h3>
<img src="https://github.com/user-attachments/assets/0fc3964c-b579-4947-9e0b-3947cc474560" width="500" />

<h3>Trigger 2:</h3>
<img src="https://github.com/user-attachments/assets/9aa00fa0-4224-4b84-ab29-dc2916aeaeee" width="500" />

<h2>Circuit Diagram (Export the Graphics to PDF and Add the Screenshot Here):</h2>
<img src="https://github.com/user-attachments/assets/aff4c609-b01d-41af-b01d-18ae870482e9" width="500" />


 
## Result :
Interfacing a push button and interrupt genrateion is simulated using proteus 
