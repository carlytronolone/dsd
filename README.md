# CPE 487 Final Project: Hex Calculator 
## By Brandon Joel, Padraig Phelps, Carly Tronolone
### Board 7

### Introduction
The FPGA (Field Programmable Gate Array) will be programmed on the Nexys A7-100T board in order to complete simple hexadecimal calculations, such as addition, subtraction, multiplication, division, and modulus, on four-digit hexadecimal numbers. A 16-button keypad module will be connected to the Pmodport JA on the Nexys A7-100T board directly. 

![image](https://github.com/carlytronolone/dsd/assets/117042826/7c84b0de-891c-49fb-85e0-f2bc7346fb34)

The goal of this project is to expand upon the overall functionality of the hexadecimal calculator from Lab 4. As the functionality of the original calculator only involved addition and subtraction, the group wants to add functionality for multiplication, division, and modulo operations.

To make up for the lack of buttons on the Nexys A7-100T board, the plan is to use a switch to change operation modes. The original addition button will also have multiplication mapped to it, and the subtraction button will have division mapped to it. The switch will be used to toggle between modes to be able to perform addition and subtraction or multiplication and division. The only button not used on the original calculator will have modulo mapped to it.

![final project](https://github.com/carlytronolone/dsd/assets/117042826/dd588bed-664c-4d33-99a5-3f9ef6e6a3cf)

The figure above describes the various states of the calculator and how it should move through operations. After inputting the first number for the operation, pressing the addition button will set ‘plus_minus’ to ‘1,’ whereas pressing the subtraction button will set it to ‘0.’ If the switch is on before pressing either the addition or subtraction buttons, it will set ‘mode_check’ to ‘1,’ where it is ‘0’ by default. Pressing the modulo button instead will set ‘modulo’ to ‘1,’ where it is ‘0’ by default. After inputting the second number for the operation, pressing the equals button will perform the operation depending on the previously set values. It will first check if ‘modulo’ is set to ‘1’ and will perform the modulo operation if it is. If it is not, it will then check for ‘plus_minus’ and ‘mode_check.’ It will then perform the addition, subtraction, multiplication, or division depending on the values set. Pressing the clear button will reset the display back to 0 and prepare the calculator for the first number of a new operation.

### Behaviors/Modified Codes
We used the codes from Lab 4 as a base code. [https://github.com/byett/dsd/tree/CPE487-Fall2023/Nexys-A7/Lab-4]

#### hexcalc.vhd
- Includes new subtraction, multiplication, division, and modulo operations
- Added a new modulo button
- Added a switch to toggle between addition/subtraction and multiplication/division
- Expanded the exisiting FSM to record more data and cases

#### keypad.vhd
- No changes to original code
  
#### leddec16.vhd
- No changes to original code

#### hexcalc.xdc
- Added buttons for modulo operation
- Added switch to switch between addition/subtraction and multiplication/division

### Steps
1. Create a new RTL project _hexcalc_ in Vivado Quick Start
   - Create three new source files of type VHDL called _keypad_, _leddec16_, and _hexcalc_
   - Create a new constraint file of the type XDC called _hexcalc_
   - Choose _Nexys A7-100T board_ for the prpkect
   - Click _Finish_
   - Click design sources and copy the VHDL code from _keypad.vhd_, _leddec16.vdh_, and _hexcalc.vhd_
   - Click _constraints_ and copy the code from _hexcalc.xdc_
2. Run synthesis
3. Run implementation and open implemented design
4. Generate bitstream, open hardware manager, and program device
   - Click _Generate Bitstream_
   - Click _Open Hardware Manager_
       - Click _Open Target_
       - Click _Auto Connect_
   - Click _Program Device_
       - Click _xc7a100t_0_ to download _hexcalc.bit_ to the Nexys A7-100T board
5. Use keypad and switches and buttons
   - _BTNC_ clears the display
   - _BTNU_ is addition/multiplication operations
   - _BTNL_ is equal
   - _BTNR_ is modulo operation
   - _BTND_ is subraction/division operations
   - If switch J15 is down/off, addition or subtraction can be performed
   - If switch J15 is up/on, multiplication or division can be performed

### Challenges
- Synthesis errors for coding multiplication and division operations
   - Because multiplication and division operations are integer operations in VHDL, some manipulation was required to get the right syntax in order to perform the operations. We have the operation be performed as a temporary integer signal, then the integer result is converted back into an STD_LOGIC_VECTOR
- Overflows within multiplication operation
   - To avoid overflows within the multiplication operation, we wanted to input a temporary function. Theoretically, this function would have the result be ‘0’ if the multiplication resulted in a value over FFFF. Unfortunately, we ran into accuracy issues and removed this overflow prevention.
- Board and keypad issues
   - When testing our code, the display board was not showing any value other than ‘9’, even when trying to input values via the keypad. Initially, we thought the issue was with our code logic but upon further inspection and code testing, we concluded that something was wrong with either the Nexys A7 board or the keypad. To fix this, we went and got a new board and keypad, which worked. 

### Conclusion
Our hex calculator serves as an everyday calculator, capable of completing addition, subtraction, multiplication, division, and modulo operations. The expansion of Lab 4 allowed us to critically think and troubleshoot through creating these new calculator operations, and also encounter some challenges, such as synthesis errors and overflow concerns. Despite the challenges faced, the process allows for careful data handling and multiple operations. Overall, the team was able to broaden the calculator’s abilities and deepen our understanding of VHDL implementation and hardware integration.

### Roles and Responsibilities
Brandon Joel - Code/Modifications
Padraig Phelps - Code/Modifications
Carly Tronolone - GitHub, system diagram
