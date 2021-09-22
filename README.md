# Roark for HP-75C/D Computer
Roarks's Formula for Stress and Strain for Hewlett Packard HP 75C/D Computer
http://materiales.azc.uam.mx/gjl/Clases/MA10_I/Roark%27s%20formulas%20for%20stress%20and%20strain.pdf

## Purpose

This program computes the Shear, Moment, Slope, and deflection for Elastic Straight Beams as defined in Table 8.1 of Roarks's Formula for Stress and Strain.
The following cases are implemented:

* Concentrated intermediate load: Case 1a to 1f are implemented
* Partial distributed load: Case 2a to 2f are implemented

## Usage
The program asks for the inputs. The variable names are the same as defined in the Roark's. See demo below:

![](demo.gif)

## Outputs
The program computes:
- The reaction forces at beam supports
- The bending moment at beam supports
- The maximal bending moment (along the beam, can be less than on the support)
- The maximal deflection
- The deflection along the beam for a given range
- The moment along the beam for a given range
- The shear force along the beam for a given range

## Requirements
This program uses the Math Rom. The module shall be properly installed on your calculator.
If you follow the instruction below for installation, you will also need the Math Rom installed in EMU75.
See EMU71 help for how to install the Rom into the emulator.

## Installation
There are several methods to copy the program to the HP-75C/D Calculator.
The description below is derived from http://www.namirshammas.com/HP71B/EMU71.htm and https://groups.io/g/hp75/topic/28780206?p=Created,,,20,2,0,0::,,,0,0,0,28780206

First, get EMU75 here: http://www.jeffcalc.hp41.eu/emu75/
Read the documentation here: http://www.jeffcalc.hp41.eu/emu75/files/emu75eng.pdf

1. Copy the code, renaming it to emu_in.dat, to Emu75's home directory.
2. Enter this program in Emu75 (or copy it from the repositery, see readdat file)
```bas
10 DIM A$[120]
20 DELAY .1
30 INPUT 'filename? ';F$
35 EDIT F$,TEXT
40 ASSIGN # 1 TO F$
50 ENTER ':I1' ; A$
60 DISP A$
70 IF A$[1,5]="*EOF*" THEN GOTO 100
80 PRINT # 1,VAL(A$[1,3]) ; A$[5]
90 GOTO 50
100 ASSIGN # 1 TO *
110 DISP "Import is complete"
120 END
```
3. Run the program in EMU75. The program prompts for a name. It will be the name of the ROARK program in EMU71.
4. Close the file by executing from the keyboard:
```bas
        clear ":i1"
```
5. The text file is now in the emulated HP-75c/d file system, as a proper HP-75C/D TEXT file, with the name you chose. You can now transform it to a BASIC program by executing from the keyboard (replace ROARK with the name you chose before):
```bas
         TRANSFORM "ROARK" INTO BASIC
```
6. You can now copy the file to HDRIVE1 by executing from the keyboard (replace ROARK with the name you chose):
```bas
         COPY "ROARK" TO ":M1"
```
7. The file HDRIVE1.dat is now able to be used to transfer directly its content with the PILBOX. Go to your ILPER folder and replace the HDRIVE1.dat file from ILPER with the one from EMU75 (backup the old one before if needed). Connect you HP-75C/D to the PILBOX, run ILPER, and execute the following command on your (real) HP-75C/D:
```bas
         COPY "ROARK:M1" to "ROARK"
```
8. You can also copy the file from EMU75 to a regular windows text file with the following program:
```bas
05 PWIDTH 94
10 ENDLINE CHR$(13)&CHR$(10)
20 PRINTER IS ":I1"
30 INPUT "FILENAME? ";F$
40 PLIST F$
50 PRINTER IS *
```
You'll find a PC text file named "emu_out.dat" in Emu71's home directory.
         
## Thanks

Many thanks to Jean-Francois Garnier, Christoph Giesselink, Namir Shammas, Robert Prosperi and Valentin Albillo.

