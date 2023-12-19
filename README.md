# CPE 487 Final Project: Hex Calculator 
## By Brandon Joel, Padraig Phelps, Carly Tronolone
### Board 7

### Introduction
The FPGA (Field Programmable Gate Array) will be programmed on the Nexys A7-100T board in order to complete simple hexadecimal calculations, such as addition, subtraction, multiplication, division, and modulus, on four-digit hexadecimal numbers. A 16-button keypad module will be connected to the Pmodport JA on the Nexys A7-100T board directly. 

--add image of keypad--
--some kind of high level block diagram showing how different parts of your program connect together and/or showing how what you have created might fit into a more complete system could be appropriate instead.--

### Bahaviors/Modified Codes
#### hexcalc.vhd
- Top level source module
- 

#### keypad.vhd

#### leddec16.vhd

#### hexcalc.vhd

#### hexcalc.xdc

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
5. Use keypad and switches (and buttons?)
   - 


### Conclusion


A description of the expected behavior of the project, attachments needed (speaker module, VGA connector, etc.), related images/diagrams, etc.
The more detailed the better – you all know how much I love a good finite state machine and Boolean logic, so those could be some good ideas if appropriate for your system. 
A summary of the steps to get the project to work in Vivado and on the Nexys board
Images and/or videos of the project in action interspersed throughout to provide context
“Modifications”
If building on an existing lab or expansive starter code of some kind, describe your “modifications” – the changes made to that starter code to improve the code, create entirely new functionalities, etc. Please share any starter code used as well.
If you truly created your code/project from scratch, describe that in brief here.
Conclude with a summary of the process itself – who was responsible for what components (preferably also shown by each person contributing to the github repository!), the timeline of work completed, any difficulties encountered and how they were solved, etc.
