Push-Button-Controlled Buzzer and Speaker Using AT89C51 Microcontroller
1. Aim

To design and implement a push-button-controlled buzzer and speaker using the AT89C51 microcontroller. The system detects the push-button input and activates the buzzer and speaker through a BC547 NPN transistor. The audible indicators remain ON while the button is pressed and turn OFF when the button is released.

2. Apparatus Required
S.No.	Component	Specification	Quantity
1	Microcontroller	AT89C51	1
2	Push Button	Normally Open	2
3	Buzzer	5V DC	1
4	Speaker	Low-power speaker	1
5	NPN Transistor	BC547	1
6	Base Resistor	330 Ω	1
7	Pull-down Resistor	10 kΩ	1
8	Reset Resistor	10 kΩ	1
9	Capacitor	0.1 µF	1
10	Crystal Oscillator	11.0592 MHz	1
11	Power Supply	Regulated +5V DC	1
12	Connecting Wires	—	As required
13	Computer	Keil µVision IDE	1
14	Digital Multimeter	Voltage measurement	1
3. Software Required
Keil µVision IDE
Embedded C compiler
Proteus Design Suite
8051 Microcontroller Programmer
4. Theory

The AT89C51 is an 8-bit microcontroller belonging to the 8051 family. It is widely used in embedded systems for controlling electronic devices and performing simple automation tasks.

The microcontroller contains an 8-bit CPU, 4 KB of on-chip Flash memory, 128 bytes of RAM, 32 programmable I/O pins, two 16-bit timers/counters, a serial communication port, and interrupt control circuitry.

In this project, the AT89C51 is used to control two audible output devices: a buzzer and a speaker. A push button acts as the input device, allowing the user to control the operation of the sound-producing devices.

The push button is connected to Port 1, pin P1.2 of the microcontroller. A 10 kΩ pull-down resistor ensures that the input remains at a stable LOW logic level when the button is not pressed.

When the button is pressed, a HIGH logic signal is applied to P1.2. The microcontroller detects this input and generates a HIGH output at P3.2.

The output signal is applied to the base of a BC547 NPN transistor through a 330 Ω resistor. The transistor operates as an electronic switch and controls the current supplied to the buzzer and speaker.

When the transistor switches ON, current flows through the audible devices and produces sound. When the button is released, the transistor switches OFF, stopping the sound.

Thus, the project demonstrates digital input interfacing, transistor switching, and output-device control using an 8051-family microcontroller.

5. Description of Individual Components
5.1 AT89C51 Microcontroller

The AT89C51 is an 8-bit microcontroller manufactured as part of the 8051-compatible family.

Important features:

8-bit CPU.
4 KB Flash program memory.
128 bytes internal RAM.
32 programmable input/output pins.
Two 16-bit timers/counters.
Full-duplex serial port.
Five interrupt sources.
Operating voltage typically around 5V.

In this project:

P1.2 is used to receive the push-button input.
P3.2 is used to control the transistor.
VCC and GND provide power to the microcontroller.
5.2 Push Button

A push button is a mechanical switching device used to establish or interrupt an electrical connection.

A normally open (NO) push button remains open when released and closes when pressed.

In this circuit:

Released condition: P1.2 = LOW.
Pressed condition: P1.2 = HIGH.
5.3 Buzzer

A buzzer is an electronic sound-producing device that converts electrical energy into sound energy.

A 5V active buzzer contains an internal oscillator and produces sound when DC power is applied.

It is used in:

Alarm systems.
Warning systems.
Doorbells.
Electronic notification circuits.
5.4 Speaker

A speaker converts an electrical audio signal into sound waves through the movement of its diaphragm.

A passive speaker requires an alternating electrical signal to produce continuous audible sound. Therefore, the simple ON/OFF transistor circuit is suitable for switching a compatible buzzer, but a passive speaker needs a suitable audio-frequency driver to produce a sustained tone.

5.5 BC547 Transistor

The BC547 is a general-purpose NPN bipolar junction transistor.

It has three terminals:

Base (B)
Collector (C)
Emitter (E)

The transistor works as an electronic switch in this project.

When a sufficient base current is supplied, the transistor enters saturation and allows current to flow from collector to emitter.

5.6 Resistors

Resistors are used to limit current and establish proper voltage levels.

330 Ω resistor: Limits the transistor base current.
10 kΩ resistor: Keeps the push-button input LOW when the button is released.
10 kΩ reset resistor: Forms part of the reset circuit.
5.7 Capacitor

A 0.1 µF capacitor is used as part of the reset circuit or supply decoupling arrangement, depending on the circuit design.

It helps suppress short-duration voltage disturbances when correctly placed.

6. Circuit Connections
AT89C51 Pin	Connection
P1.2 (Pin 3)	Push-button input
P3.2 (Pin 12)	BC547 base through 330 Ω
VCC (Pin 40)	+5V
GND (Pin 20)	Ground
RST (Pin 9)	Reset circuit
XTAL1 (Pin 19)	Crystal oscillator
XTAL2 (Pin 18)	Crystal oscillator
Input Section

One terminal of the push button is connected to +5V, and the other terminal is connected to P1.2.

A 10 kΩ resistor is connected between P1.2 and ground to maintain a LOW input when the button is released.

Output Section

P3.2 is connected to the BC547 base through a 330 Ω resistor.

The emitter is connected to ground, and the collector is connected to the negative side of the compatible buzzer load.

The positive side of the buzzer is connected to +5V.

Important: A passive speaker should use a separate suitable audio driver. Do not connect a low-impedance speaker directly in parallel with a buzzer and assume the BC547 can safely drive both. Check the load current and transistor ratings.

7. Working Principle

The circuit works on the principle of digital switching and transistor operation.

Initially, the push button remains in the released state. The pull-down resistor maintains P1.2 at LOW logic level.

The microcontroller continuously reads the input status.

When the push button is pressed, +5V is applied to P1.2, producing a HIGH logic signal.

The microcontroller identifies the HIGH signal and makes P3.2 HIGH.

This HIGH signal provides base current to the BC547 transistor through the 330 Ω resistor.

The transistor switches ON and allows current to flow through the buzzer circuit. The buzzer generates an audible warning signal.

When the button is released, P1.2 returns to LOW. The microcontroller makes P3.2 LOW, switching OFF the transistor and buzzer.

The entire process repeats continuously.

8. Algorithm
Start the system.
Initialize the microcontroller.
Configure P1.2 as input.
Configure P3.2 as output.
Set the output LOW.
Read the push-button status.
Check whether the button is pressed.
If pressed, introduce a 20 ms debounce delay.
Verify the input again.
If the input remains HIGH, switch ON the output.
If the input is LOW, switch OFF the output.
Repeat the process continuously.
9. Design Calculations
9.1 Power Supply Calculation

The AT89C51 operates using a regulated 5V DC power supply.

Given:

Supply voltage:

VCC = 5V

Assuming the microcontroller current consumption is approximately 20 mA for an illustrative calculation:

Power consumption:

P = V × I

P = 5 × 0.02

P = 0.1 W

Therefore, the estimated microcontroller power consumption is:

P = 100 mW

Actual consumption depends on clock frequency, operating conditions, and connected loads.

9.2 Pull-Down Resistor Calculation

The pull-down resistor is connected between the input pin P1.2 and ground.

Given:

Supply voltage = 5V
Pull-down resistance = 10 kΩ

When the button is pressed, the pull-down current is:

I = V/R

I = 5/10000

I = 0.0005 A

I = 0.5 mA

Therefore, the current through the pull-down resistor during the pressed condition is approximately:

I = 0.5 mA

9.3 Transistor Base Resistor Calculation

The base resistor limits the current flowing into the BC547 transistor.

Given:

Supply voltage = 5V
Base-emitter voltage = 0.7V
Base resistor = 330 Ω

Assuming the output pin reaches approximately 5V for this nominal calculation:

Base current:

Ib = (Vout - Vbe)/Rb

Ib = (5 - 0.7)/330

Ib = 4.3/330

Ib = 0.013 A

Ib = 13.03 mA

Therefore, the nominal calculated base current is approximately:

Ib = 13.03 mA

The actual base current depends on the AT89C51 output voltage under load. A 330 Ω resistor may demand more current than is appropriate for a particular port pin. The base resistor should be selected using the microcontroller's guaranteed output-current specifications and the transistor's required collector current. A larger resistor or a dedicated driver stage may be necessary.

9.4 Transistor Collector Current

The collector current depends on the buzzer load.

Assume an example 5V buzzer consumes 30 mA.

Then:

Ic = 30 mA

For reliable switching, the transistor should be operated in saturation with sufficient base drive.

The approximate forced current gain is:

Forced beta = Ic/Ib

Using a conservative illustrative base current of 3 mA:

Forced beta = 30/3

Forced beta = 10

This is a common design target for saturated switching, but the actual BC547 datasheet and load conditions must be checked.

9.5 Buzzer Power Calculation

Assume:

Operating voltage = 5V
Buzzer current = 30 mA

Power:

P = V × I

P = 5 × 0.03

P = 0.15 W

Therefore:

Buzzer power = 150 mW

This is an example calculation. Replace 30 mA with the actual current rating of the selected buzzer.

9.6 Debouncing Delay Calculation

Mechanical push buttons may produce multiple rapid transitions when pressed or released.

A delay of approximately 20 milliseconds is introduced to reduce false triggering.

Given:

Debouncing delay = 20 ms

In seconds:

20/1000 = 0.02 seconds

Therefore:

Debouncing delay = 0.02 seconds

The actual software delay depends on the crystal frequency and compiler-generated machine instructions.

9.7 Total Power Calculation

Assume the following illustrative loads:

AT89C51 current = 20 mA
Buzzer current = 30 mA

Total current:

Itotal = 20 + 30

Itotal = 50 mA

Total power:

Ptotal = 5 × 0.05

Ptotal = 0.25 W

Therefore:

Estimated total power = 250 mW

This estimate excludes other circuit losses and the speaker driver. Actual power should be calculated using measured currents.

10. Embedded C Program
c
#include <reg51.h>

sbit BUTTON = P1^2;
sbit BUZZER = P3^2;

void delay_ms(unsigned int ms)
{
    unsigned int i, j;

    for(i = 0; i < ms; i++)
    {
        for(j = 0; j < 112; j++)
        {
            /* Approximate delay */
        }
    }
}

void main(void)
{
    BUTTON = 1;
    BUZZER = 0;

    while(1)
    {
        if(BUTTON == 1)
        {
            delay_ms(20);

            if(BUTTON == 1)
            {
                BUZZER = 1;
            }
        }
        else
        {
            BUZZER = 0;
        }
    }
}

11. Program Explanation
reg51.h provides the 8051 register definitions.
BUTTON represents the input pin P1.2.
BUZZER represents the output pin P3.2.
delay_ms() creates an approximate delay.
BUTTON = 1 releases the port pin for input operation.
BUZZER = 0 switches OFF the output initially.
while(1) executes continuously.
if(BUTTON == 1) checks whether the push button is pressed.
delay_ms(20) provides debounce time.
BUZZER = 1 activates the transistor driver.
BUZZER = 0 deactivates the transistor driver.
12. Experimental Procedure
Connect the AT89C51 microcontroller to the regulated 5V supply.
Connect the crystal oscillator circuit to XTAL1 and XTAL2.
Connect the reset circuit to the RST pin.
Connect the push button to P1.2.
Connect the pull-down resistor between P1.2 and ground.
Connect P3.2 to the BC547 base through the selected resistor.
Connect the buzzer driver circuit.
Compile the Embedded C program using Keil µVision.
Generate the HEX file.
Load the HEX file into the AT89C51 microcontroller or Proteus simulation.
Switch ON the power supply.
Press the push button and observe the buzzer operation.
Release the button and verify that the buzzer switches OFF.
Record the voltage readings using a digital multimeter.
13. Experimental Readings

The following values are illustrative expected readings. Actual hardware readings must be recorded during the experiment.

S.No.	Button Condition	P1.2 Voltage	P1.2 Logic	P3.2 Voltage	Buzzer
1	Released	0V	LOW	0V	OFF
2	Pressed	5V	HIGH	HIGH	ON
3	Released	0V	LOW	0V	OFF
4	Pressed	5V	HIGH	HIGH	ON
5	Pressed continuously	5V	HIGH	HIGH	ON
6	Released	0V	LOW	0V	OFF
14. Result Analysis

The experimental operation demonstrates that the AT89C51 can detect digital input signals and control external devices using its output pins.

When the input signal at P1.2 changes from LOW to HIGH, the microcontroller generates a HIGH output at P3.2.

The BC547 transistor acts as a switch and activates the buzzer load.

When the input changes from HIGH to LOW, the transistor switches OFF and the buzzer stops producing sound.

Thus, the system successfully demonstrates push-button interfacing and transistor-based load switching.

15. Advantages
Simple and low-cost design.
Easy to implement and understand.
Requires fewer external components.
Provides immediate audible indication.
Demonstrates microcontroller input/output interfacing.
Can be expanded for multiple alert conditions.
16. Applications
Security alarm systems.
Emergency warning systems.
Doorbell circuits.
Industrial fault indication.
Vehicle warning systems.
Patient assistance systems.
Home automation systems.
Electronic notification systems.
17. Limitations
The circuit provides basic ON/OFF control.
Different sound frequencies are not generated by the given program.
Mechanical switches may introduce bouncing.
A passive speaker requires an audio-frequency driver.
The output current is limited by the transistor and microcontroller specifications.
18. Future Enhancements
Add multiple push buttons for different warning signals.
Generate different tones using timer interrupts.
Add LED indicators.
Implement adjustable buzzer duration.
Add an LCD display to show system status.
Develop a password-based security alarm system.
Add a suitable audio amplifier for the speaker.
19. Conclusion / Result

The push-button-controlled buzzer and speaker system was designed using the AT89C51 microcontroller and Embedded C programming.

The microcontroller successfully detects the push-button input and controls the output through a BC547 transistor driver.

When the push button is pressed, the buzzer is activated. When the push button is released, the buzzer is switched OFF.

The project demonstrates the basic concepts of digital input interfacing, transistor switching, and embedded system control.

Therefore, the design and implementation of a push-button-controlled audible alert system using the AT89C51 microcontroller were successfully studied and demonstrated.

20. References
AT89C51 Microcontroller Datasheet – Microchip Technology.
BC547 NPN Transistor Datasheet.
8051 Microcontroller Architecture and Interfacing.
Keil µVision Embedded C Compiler Documentation.
Electronic Devices and Circuit Theory – Robert L. Boylestad.
