 SNES to NEO-GEO
===============

This is an Arduino project which allows you to interface a SNES or Super Famicom controller
(or a clone) to a NEO GEO style DB15 connector.

With some additions it's based on Robin Edwards code found at 

https://github.com/robinhedwards/SNES-to-NeoGeo and 
https://github.com/burks10/Arduino-SNES-Controller

I created that code to be able to connect some 8bitdo awesome wireless controllers to my 
NEO GEO MVS1B which I was consolizing. Also the goal was not only to connect wireless controllers
to arcade board but also implement turbo fire buttons, DIP switches wireless control and some 
more interesting things.

Some short notes and pictures you can see below.

To consolize my MVS I was referring to this site
http://www.jamma-nation-x.com/jammax/cmvs.html

To connect Arduino and DB15 joystick ports I was reffering to that thread on neo-geo.com
http://www.neo-geo.com/forums/showthread.php?236280-Info-Consolized-MV1B-Controller-points-on-the-bottom-of-the-board 

![Image](mv1b_controller_pinout.jpg?raw=true)

During consolizing I decided to keep the original case as a whole thing because I hate to cut any
holes on the original consoles. So I was using pieces of black plastic to be able to fit all the 
power and RGB sockets along with SNES, DB15 joystick sockets and screen. Two Arduino's were used where 
the one board is main and has screen and DIP switches connected. 

During power up you can see SNK Logo on the screen


![Image](SNKLogo.jpg?raw=true)



and after couple of seconds it starts showing status of DIP Switches and Turbo Fire status



![Image](DIPState.jpg?raw=true)

DIP switches and Turbo Fire can be swithced on/off with joystick buttons combination listed below.

SNES gamepad button combinations
```
SELECT + START - Pause mode (DIP_SWITCH 8) - Disabled after UNIBIOS installation
SELECT + A + X - Test mode (DIP_SWITCH 1)
SELECT + B + Y - Freeplay mode (DIP_SWITCH 7)
L_SHIFT and START - I made them equal because if you use 8Bitdo and holding start more than 5sec 
contoller being powered down, so I dublicated START to L_SHIFT. It allows to reset console if  
You play famous Banana 161 in 1 chineese game cartridge by holding L_SHIFT about 5~10 seconds
SELECT + any of A, B, X OR Y - Autofire mode - switch on/off them in autofire mode
```
DIP Switches connections
```
DIP Pin  ->  Arduino
--------     -------
TEST_MODE       13
FREE_PLAY       A3
PIN_PAUSE       12
```



![Image](DIPSwitches.jpg?raw=true)

DIPSwitches connection

This shows a completed project on a cheap Arduino Pro Mini (5v) clone wired up to a SNES female
socket and female DB15 for easy connections. Also Arduino is connected to the board as per 
diagram listed above.

SNES female controller and DB15 sockets, SSD1306　Screen and Arduino Mini are available on eBay of AliExpress for a couple of bucks.

SNES Controller -> Arduino
--------------------------

```
  -----------------\
  | 1 2 3 4 | 5 6 7 |
  -----------------/
  
  Pin 1: +5V
  Pin 2: Clock -> Arduino A0
  Pin 3: Latch -> Arduino A1
  Pin 4: Serial -> Arduino A2
  Pin 7: GND
```

Arduino -> DB15
---------------

```
    1(=GND)        8(=5V)
  \-------------------/
   \ o o o o o o o o / [Viewed from front]
    \ o o o o o o o /
     --------------- 
      9          15

 DB15 Pin  ->  Arduino
 --------      -------
 1 (GND)       GND
 8 (+5V)       +5V
 3 (Sel)       D2
 11 (Start)    D3
 15 (Up)       D4
 7 (Down)      D5
 14 (Left)     D6
 6 (Right)     D7
 13 (A)        D8
 5 (B)         D9
 12 (C)        D10
 4 (D)         D11
```



![Image](Front.jpg?raw=true)

Front panel

![Image](Back.jpg?raw=true)

Back panel
