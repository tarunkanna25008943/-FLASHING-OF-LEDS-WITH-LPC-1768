# FLASHING-OF-LEDS-WITH-LPC-1768

# AIM: 
   To interface and toggle the led with ARM LPC 1768 microprocessor           
           
# COMPONENTS REQUIRED:
##  HARDWARE:
ARM LPC1768
LED
## SOFTWARE:
KEIL MICRO VISION 4.0 IDE

# PROCEDURE:


⮚	Open the Keil software and select the New uvision project from Project Menu as shown below.
⮚	Browse to your project folder and provide the project name and click on save.
⮚	Once the project is saved a new pop up “Select Device for Target” opens, Select the controller (NXP: LPC1768) from NXP (founded by philips) and click on OK.
⮚	Select the controller (NXP: LPC1768) and click on OK.
⮚	As LPC1768 needs the startup code, click on Yes option to include the LPC17xx Startup file.
⮚	Create a new file by file → new to write the program.
⮚	Type the code.
⮚	After typing the code save the file as main.c eg. (abc.c).
⮚	Right click target and Add the suitable files to source group1 and header for the project.
⮚	Add the main.c along with system_LPC17xx.c.
⮚	Build the project and fix the compiler errors/warnings if any.
⮚	Code is compiled with no errors. The .bin file is still not generated.
⮚	Right Click on Target Options to select the option for generating .bin file.
⮚	Set IROM1 start address as 0x2000. Bootloader will be stored from 0x0000- 0x2000 so application should start from 0x2000
⮚	Write	the	command	to	generate	the .bin file	from
.axf file
Command: fromelf --bin projectname.axf --output filename.bin
⮚	in c/c++ → include paths → desktop (00-libfiles).
⮚	.Bin file is generated after a rebuild.
⮚	Check the project folder for the generated .Bin file.

# ADD FILES:
Target1:
Source group1:
Startuplpc17xx.s, main.c (t), delay.c (t), systemlpc17xx.c (t), gpio.c (t)
Header:
Delay.h, stdutils.h, gpioi.h
# PIN DIAGRAM:
<img width="767" height="416" alt="image" src="https://github.com/user-attachments/assets/1afc7473-7913-488b-a649-7b4a6a9db4cc" />

# CIRCUIT DIAGRAM:
<img width="1156" height="482" alt="image" src="https://github.com/user-attachments/assets/ec4274e3-938a-4ac1-b3ee-9c642c5a71ae" />

# PROGRAM:
```
#include <LPC17xx.h>

void delay_ms(unsigned int ms)
{
    unsigned int i, j;

    for(i = 0; i < ms; i++)
    {
        for(j = 0; j < 5000; j++);
    }
}

int main(void)
{
    // Configure P0.22 as GPIO
    LPC_GPIO0->FIODIR |= (1 << 22);

    while(1)
    {
        // LED ON
        LPC_GPIO0->FIOSET = (1 << 22);

        delay_ms(500);

        // LED OFF
        LPC_GPIO0->FIOCLR = (1 << 22);

        delay_ms(500);
    }
}
```
# Output:
<img width="899" height="1599" alt="WhatsApp Image 2026-09-23 at 13 03 25" src="https://github.com/user-attachments/assets/b66e5088-7358-405e-b86c-39d119e90208" />

# Result:
Hence, LED blinking was implemented using GPIO control with LPC1768
