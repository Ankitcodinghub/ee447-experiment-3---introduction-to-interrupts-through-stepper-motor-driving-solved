# ee447-experiment-3---introduction-to-interrupts-through-stepper-motor-driving-solved
**TO GET THIS SOLUTION VISIT:** [EE447 Experiment 3 – Introduction to Interrupts through Stepper Motor Driving Solved](https://www.ankitcodinghub.com/product/ee447-solved-3/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;112892&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;EE447 Experiment 3 - Introduction to Interrupts through Stepper Motor Driving Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
Objectives

The concept of interrupts and their trigger-response structure

Differences between polling-driven and interrupt-driven I/O

How to write interrupt service routines (ISR) for the TM4C

How to generate delays using the System Timer system

How to drive a stepper motor

1 Background Information

1.1 Interrupts

This register model for the TM4C123GH6PM contains the Program Status Register (PSR). Eight of the bits in the PSR (bits 7:0) indicate which interrupt, if any, is currently being handled.

1.1.1 Interrupt Service Routine

An interrupt service routine (ISR) is similar to a subroutine. It is called by the system when an interrupt occurs. Recall from the lectures that there are two main interrupt service approaches which are polling and vectored interrupts. TM4C123GH6PM supports vectored interrupts. In that scheme, each interrupt source has an address dedicated to it and that address contains the address of the ISR. The design of the MCU is in such a way that when an interrupt occurs, the PC fetches the corresponding address of the ISR from the vector map which is the memory block dedicated to the interrupt sources in order to hold the addresses of the ISRs. A complete interrupt vector map for TM4C123GH6PM is listed in the file Startup.s available on ODTUClass course page. This map tells you where the interrupt vector the appropriate interrupt service routine is located for all possible TM4C123GH6PM interrupts.

In general, the main program runs, possibly in an infinite loop, to perform some user defined useful tasks. However, you sometimes need to perform additional tasks that actually depend on internal or external requests. A request can be considered as an interrupt to the main program. When an interrupt occurs, the system runs the ISR. In that manner, an ISR is similar to a subroutine but it responds to a request, i.e. it is called by the system, whereas a subroutine is called because of an instruction in the program.

1.1.2 Coding with Interrupts Using C

There are two main tasks to properly make use of the interrupts. The first task is to write a function and the second task is to configure and initialize the interrupt source that you want to use. The latter is to be explained in the following subsection 1.1.3 specific to System Timer interrupt. Recall that ISR is actually a subroutine/function which is called by the system when the related interrupt occurs. Thus, writing an ISR is actually writing a subroutine/function which is something you know from Experiment 1. There is no difference, all you do is write a usual function in C with the correct name and the compiler will link your subroutine with the related interrupt so that your function becomes an ISR.

Remember that a 4-Byte memory space is dedicated to each interrupt source. In that space, the address of the corresponding ISR should be placed. Thus, all you need is to place the address where your function starts in the reserved memory space of the interrupt you are using. When using C this is very simple. When you examine the vector map defined in the start-up code, Startup.s, you will realize that the reserved memory spaces for the interrupt vectors are filled via an assembly directive that uses labels and resolves the address value that a label corresponds: ;******************************************************************************

;

; The vector table .

;

;******************************************************************************

EXPORT

Vectors Vectors

DCD StackMem + Stack ; Top of Stack

DCD Reset Handler ; Reset Handler

. . .

DCD SysTick Handler ; SysTick Handler

. . .

Therefore, as long as the name of your function matches the label of the corresponding interrupt source and it returns and takes nothing (that is void), your function is the ISR. For example, if you want to use Sys tick interrupt the name on the interrupt vector is ”SysTick Handler”. Hence, you will have a function like the one below.

void SysTick Handler ( void )

{

. . . //Your Interrupt function

} here

When you further examine the start up code, Startup.s, you will see code sections devoted to the default interrupt service subroutines:

. . .

;******************************************************************************

;

; This is the code that gets called when the processor f i r s t starts execution ; following a reset event .

;

;******************************************************************************

EXPORT Reset Handler

Reset Handler

. . .

IMPORTmain

B main

. . .

SysTick Handler PROC

EXPORT SysTick Handler [WEAK]

B .

ENDP

. . .

Notice that the first ISR is the reset handler. Reset is an unmaskable interrupt and its ISR is called when the system reset occurs. You can see that your main program is called by this ISR with the specific label main. That is why you have been labeling your main program with the label main when using assembly. The default ISR sections of the interrupt sources follow the reset handler.

Now, what is left is the initialization and the configuration of the interrupt source you are planning to use. In the following section 1.1.3, the System Timer is to be explained, since it is interrupt source you will be using in the scope of this lab.

1.1.3 System Timer (SysTick)

There are three important control registers for the SysTick in the TM4C123GH6PM: STCTRL,

The Status and Control register (STCTRL) given by Figure 7 is used to enable the SysTick system (interrupt vector address 0x0000.003C). Bit 0 of this register is the System Timer Enable (ENABLE) bit. This bit when set to 1 enables the SysTick system, and when set to 0, disables the SysTick system. Bit 1 is the Interrupt Enable bit (INTEN) which enables interrupts for the SysTick system. When this bit is set to 1 interrupts are enabled and an ISR will be called when the timer reaches 0. Bit 2 is the Clock Source bit (CLK_SRC). The internal oscillator of the TM4C123GH6PM is not the only clock available to use. With additional setup, other more accurate oscillators can be used. However, for now we will simply use the Precision Internal OSCillator (PIOSC) divided by 4. The PIOSC runs at 16 MHz on the TM4C123GH6PM, so PIOSC/4 is 4 MHz. Hence the clock period is 250ns, which enables us creating delays in the order of seconds.

Figure 1: Status and Control register (STCTRL) at 0xE000.E010.

The SysTick Reload Value register (STRELOAD) given by Figure 8 selects the time-out period of the SysTick system. RELOAD[23:0] is where the 24-bit starting value for the counter will be stored. The SysTick system will count down from this value to 0, subtracting 1 every clock cycle.

Figure 2: SysTick Reload Value register (STRELOAD) at 0xE000.E014.

The SysTick Current Value register is a 24-bit register containing the current value of the count down from the RELOAD value.

The SYSPRI register configures the priority level, 0 to 7 of the SysTick exception handler by placing this level into the TICK field (bits 31:29). The lower the value of this field, the higher its priority. Recall from

Figure 3: SysTick Current Value register (STCURRENT) at 0xE000.E018

the lectures that a priority level of 1 or greater is required to enable SysTick interrupts. This register is byte addressable.

Figure 4: SYSPRI3 register at 0xE000.ED20

void init f volatile unc ( int void ){

*SYS BASE = ( volatile int *) 0xE000E000 ;

volatile int *SYS LOAD = ( volatile int *) 0xE000E014 ;

volatile int *SYS VAL = ( volatile int *) 0xE000E018 ;

volatile int *SYS CTRL = ( volatile int *) 0xE000E010 ;

volatile int *SYS IRP = ( volatile int *) 0xE000ED20;

volatile int *SYSCTL RCGCGPIO = ( volatile int *) 0x400FE608 ;

volatile int *GPIOF DIR = ( volatile int *) 0x40025400 ;

volatile int *GPIOF DEN = ( volatile int *) 0x4002551C ;

*SYSCTL RCGCGPIO |= 0x20 ; // turn on bus clock for GPIOF

*GPIOF DIR |= 0x08 ; // set GREEN pin as a digital output pin

*GPIOF DEN |= 0x08 ; // Enable PF3 pin as a digital pin

*(SYS LOAD) = 15999999; // Configure load value

*(SYS VAL) = 15999999; // Clear the timer register by writing to it

*(SYS IRP) = 0x40000000 ; // Configure interrupt priority for sys tick

*(SYS CTRL) = 0x07 ; //source system bus , interrupt enabled and clock is

}

volatile int *GPIOF DATA = ( volatile int *) 0x40025020 ; // Notice that PF3 is write enabled

//This is the function to be called by the ISR void SysTick Handler ( void )

GPIOF DATA ˆ= 8; // toggle PF3 pin

} started

#include ”TM4C123GH6PM.h” void init func ( void ){

SYSCTL=&gt;RCGCGPIO |= 0x20 ; // turn on bus clock for GPIOF

GPIOF=&gt;DIR |= 0x08 ; // set GREEN pin as a digital output pin

GPIOF=&gt;DEN |= 0x08 ; // Enable PF3 pin as a digital pin

SysTick=&gt;LOAD = 15999999; // one second delay relaod value

SysTick=&gt;CTRL = 7 ; // enable counter , interrupt and select system bus SysTick=&gt;VAL = 0; // i n i t i a l i z e current value register

}

//This is the function to be called by the ISR void SysTick Handler ( void )

{

GPIOF=&gt;DATA ˆ= 8; // toggle PF3 pin

} clock

1.2 Stepper Motors

The stepper motor is an electromagnetic device that converts digital pulses into mechanical shaft rotation. Advantages of step motors are low cost, high reliability, high torque at low speeds and a simple, rugged construction that operates in almost any environment. The main disadvantages in using a stepper motor are the resonance effects often exhibited at low speeds and decreasing torque with increasing speed. These motors are commonly used in measurement and control applications. Sample applications include ink jet printers, CNC machines, volumetric pumps, etc.

The inner structure of the stepper motors are beyond the scope of this experiment. For this experiment we will consider stepper motors as black boxes, which convert digital pulses into mechanical shaft rotation. The protocol for this conversion is standard and very simple.

The stepper motor, like most other motor types has coils in its structure, which converts electrical current to magnetic force to rotate the motor shaft. Very simple schematic of a stepper motor with its control circuitry is given in Figure 5.

By energizing the coils respectively in each step, the stepper motor is rotated in one direction with fixed angles, which is prescribed in stepper motor’s specifications. Every stepper motor has a fixed stepping angle. While reversing the current in an alternating fashion (windings energized consecutively), the

Figure 5: In this circuit, a micro-controller controls the rotation of a motor known as a step motor by sequentially activating one transistor at a time (thus, energizing one motor coil at a time). With each step in the sequence, the motor rotates a fixed number of degrees.

motor makes this fixed angle of rotation. Essentially a digital input pattern with only one high bit from the driver is equivalent to one step. This mode of operation is called the Full Step Mode for step motors.

Step No. Out0 Out1 Out2 Out3

Full Step 1 1 0 0 0

Full Step 2 0 1 0 0

Full Step 3 0 0 1 0

Full Step 4 0 0 0 1

Applying these values to the controller outputs in the ascending order according to step index will make our motor make four steps of fixed angle rotation. Note that the table is cyclic in the sense that Full Step 1 follows Full Step 4. Reversing the direction of the order to descending (the order which the output is applied) will make the motor to rotate in the reverse direction.

1.2.1 Motor Driving

The ULN200xA devices are high-voltage, high-current Darlington transistor arrays. The ULN2003A is one of the most common motor driver ICs that houses an array of 7 Darlington transistor pairs, each capable of driving loads up to 500mA and 50V. Typical usage of the ULN2003A is in driver circuits for relays, lamp and LED displays, stepper motors, logic buffers and line drivers.

1.2.2 Motor Drive Control

Figure 6: ULN2003A PCB connections

2 Preliminary Work

Assume you have started your own company and you want to develop an ink jet printer. You made a research and you understood there are different components needed. One of the required tasks for an ink jet printer is to relocate the ink jet throughout the page width. After your preliminary research, you realized that, this task is commonly done by stepper motors. Before you advance in the development of the rest of the printer, you should understand how to drive a stepper motor using a TM4C123GH6PM processor. Hence, you have decided to implement a system that controls the speed and direction of a stepper motor via external push buttons. You will implement your system step by step as follows:

1. (10%) Write a C function that which sends a GPIO port the necessary signals to demonstrate the Full Step Mode in both directions (clockwise or counterclockwise).

2. (10%) Now, you will design a system that has two inputs from push buttons and provides a step to the stepper motor upon input. One button is to provide a step for clockwise rotation and the other is for counterclockwise rotation. You will use 4 buttons of the 4×4 Keypad Module introduced in Experiment-2. Draw the necessary connections between TM4C123G, ULN2003A’s board, 4×4 Keypad Module and stepper motor.

4. (5%) At this stage, you will design a system that has 4 inputs from push buttons to control a stepper motor. One button is for speeding up, one is for slowing down, the other two are for directions. You will use 4 buttons of the 4×4 Keypad Module introduced in Experiment-2. Draw the necessary connections between TM4C123G, ULN2003A’s board, 4×4 Keypad Module and stepper motor.

5. (65%) According to your hardware design in part-4, write a C program that, in an infinite loop, drives a stepper motor speed and direction of which can be controlled by external push buttons.

For this item, please explain how you attack the problem and draw a flowchart of your algorithm.

3 Parts List

1 x TM4C123G Board

1 x Stepper Motor

1 x ULN2003A 1 x 4×4 Keypad Module

References

[1] TI, “Tiva tm4c123gh6pm microcontroller data sheet.” http://www.ti.com/lit/ds/spms376e/ spms376e.pdf.

A Coding with Interrupts Using Assembly (OLD)

There are two main tasks to properly make use of the interrupts. The first task is to write an ISR and the second task is to configure and initialize the interrupt source that you want to use. The latter is to be explained in the following appendix B specific to System Timer interrupt. Recall that ISR is actually a subroutine which is called by the system when the related interrupt occurs. Thus, writing an ISR is actually writing a subroutine which is something you know from Experiment-1. There is no difference, all you do is labeling your subroutine by using PROC and ENDP directive doublet and ending your subroutine code with BX LR instruction, since the handling mode specific content of the LR tells the system to exit from the handler mode by fetching the return address from the saved context when the interrupt occurs. The issue is to link your subroutine with the related interrupt so that your subroutine becomes an ISR.

Remember that a 4-Byte memory space is dedicated to each interrupt source. In that space, the address of the corresponding ISR should be placed. Thus, all you need is to place the address where your subroutine starts in the reserved memory space of the interrupt you are using. There are several ways to do that. When you examine the vector map defined in the start up code, Startup.s, you will realize that the reserved memory spaces for the interrupt vectors are filled via assembly directive that uses labels and resolves the address value that a label corresponds:

;******************************************************************************

;

; The vector table .

;

;******************************************************************************

EXPORT

Vectors Vectors

DCD StackMem + Stack ; Top of Stack

DCD Reset Handler ; Reset Handler

. . .

DCD SysTick Handler ; SysTick Handler

. . .

Therefore, as long as the label of your subroutine matches with the label of the corresponding interrupt source, your subroutine is the ISR. When you further examine the start up code, Startup.s, you will see code sections devoted to the interrupt service subroutines:

. . .

;******************************************************************************

;

; This is the code that gets called when the processor f i r s t starts execution ; following a reset event .

;

;******************************************************************************

EXPORT Reset Handler

Reset Handler

. . .

IMPORTmain

B main

. . .

SysTick Handler PROC

EXPORT SysTick Handler [WEAK]

B .

ENDP

. . .

;******************************************************************************

;

; The vector table .

;

;******************************************************************************

IMPORT SysTick Handler ; the label is to be imported EXPORT Vectors

Vectors

DCD StackMem + Stack ; Top of Stack DCD Reset Handler ; Reset Handler

. . .

DCD SysTick Handler ; SysTick Handler

. . .

. . .

. . .

; The SysTick Handler section should be disabled

; to prevent redefinition of the same label

; SysTick Handler PROC

; EXPORT SysTick Handler [WEAK]

; B .

; ENDP

; . . .

The other approach is calling your subroutine from the ISR implemented in the start up code, Startup.s. Again you should use EXPORT directive to make your subroutine achievable and you should use IMPORT/EXTERN directive to refer your subroutine from the start up code. For instance, if you are planning to use System Timer interrupt, your generic start up code for the second approach after modification should be something like: ;******************************************************************************

;

; The vector table .

;

;******************************************************************************

; NO CHANGE AT THIS SECTION EXPORT Vectors

Vectors

DCD StackMem + Stack ; Top of Stack

DCD Reset Handler ; Reset Handler

. . .

DCD SysTick Handler ; SysTick Handler

. . .

; My SysTick Handler subroutine should be implemented and EXPORTed

IMPORT My ST ISR ; import the starting address of ISR

SysTick Handler PROC

EXPORT SysTick Handler [WEAK]

B My ST ISR

ENDP

. . .

B System Timer (SysTick) Using Assembly (OLD)

The Status and Control register (STCTRL) given by Figure 7 is used to enable the SysTick system (interrupt vector address 0x0000.003C). Bit 0 of this register is the System Timer Enable (ENABLE) bit. This bit when set to 1 enables the SysTick system, and when set to 0, disables the SysTick system. Bit 1 is the Interrupt Enable bit (INTEN) which enables interrupts for the SysTick system. When this bit is set to 1 interrupts are enabled and an ISR will be called when the timer reaches 0. Bit 2 is the Clock Source bit (CLK_SRC). The internal oscillator of the TM4C123GH6PM is not the only clock available to use. With additional setup, other more accurate oscillators can be used. However, for now we will simply use the Precision Internal OSCillator (PIOSC) divided by 4. The PIOSC runs at 16 MHz on the TM4C123GH6PM, so PIOSC/4 is 4 MHz. Hence the clock period is 250ns, which enables us creating delays in the order of seconds.

The SysTick Reload Value register (STRELOAD) given by Figure 8 selects the time-out period of the SysTick system. RELOAD[23:0] is where the 24-bit starting value for the counter will be stored. The SysTick system will count down from this value to 0, subtracting 1 every clock cycle.

The SysTick Current Value register is a 24-bit register containing the current value of the count down

Figure 7: Status and Control register (STCTRL) at 0xE000.E010.

Figure 8: SysTick Reload Value register (STRELOAD) at 0xE000.E014.

from the RELOAD value.

Figure 9: SysTick Current Value register (STCURRENT) at 0xE000.E018

The SYSPRI register configures the priority level, 0 to 7 of the SysTick exception handler by placing this level into the TICK field (bits 31:29). The lower the value of this field, the higher its priority. Recall from the lectures that a priority level of 1 or greater is required to enable SysTick interrupts. This register is byte addressable.

Figure 10: SYSPRI3 register at 0xE000.ED20

from the main program to configure and initialize the timer interrupt. The start up code, Startup.s, is assumed to be modified as explained in the previous section 1.1.2 to link the user defined ISR.

;*********************************************************

; Your SystemTimer . s source f i l e to implement

; initialization and ISR

;*********************************************************

; Definition of the labes standing for

; the address of the registers NVIC ST CTRL EQU 0xE000E010

NVIC ST RELOAD EQU 0xE000E014

NVIC ST CURRENT EQU 0xE000E018

SHP SYSPRI3 EQU 0xE000ED20

; end of the register label definitions

; 0x7D0 = 2000 =&gt; 2000*250ns = 500mus RELOAD VALUE EQU 0x000007D0

;********************************************************* ; Initialization area

;*********************************************************

;LABEL DIRECTIVE VALUE COMMENT

AREA THUMB init isr , CODE, READONLY, ALIGN=2

EXPORT InitSysTick

InitSysTick PROC

; f i r s t disable system timer and the related interrupt

; then configure it to use isternal oscillator PIOSC/4

LDR R1, =NVIC ST CTRL

MOV R0, #0

STR R0, [R1]

; now set the time out period

LDR R1, =NVIC ST RELOAD

LDR R0, =RELOAD VALUE

STR R0, [R1]

; time out period is set

; now set the current timer value to the time out value

LDR R1, =NVIC ST CURRENT

STR R0, [R1]

; current timer = time out period

; now set the priority level

LDR R1, =SHP SYSPRI3 MOV R0, #0x40000000

STR R0, [R1]

; priority is set to 2

; now enable system timer and the related interrupt

LDR R1, =NVIC ST CTRL

MOV R0, #0x03

STR R0, [R1]

; set up for system time is now complete

BX LR

ENDP

;********************************************************* ; SysTick ISR area

;*********************************************************

;LABEL DIRECTIVE VALUE COMMENT

EXPORT My ST ISR

My ST ISR

PROC

. . . ; your routine

BX ENDP LR ; return

;********************************************************* ; Your main . s source f i l e

;*********************************************************

;LABEL DIRECTIVE VALUE COMMENT

AREA THUMB main , CODE, READONLY

EXTERN InitSysTick ; Reference external subroutine

EXPORT main

main PROC

. . . ; your other initiali zaitons

BL InitSysTick ; i n i t i a l i z e system timer

CPSIE I ; enable interrupts

. . .

ENDP ; rest of your code
