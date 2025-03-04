# Roark's Formula for HP-75C/D Computer
Roarks's Formula for Stress and Strain for Hewlett Packard HP 75C/D Computer


## Purpose

This program computes the shear, moment, slope, and deflection for Elastic Straight Beams as defined in Table 8.1 of Roarks's Formula for Stress and Strain.
The following cases are implemented:

* Concentrated intermediate load: Case 1a to 1f are implemented
* Partial distributed load: Case 2a to 2f are implemented

## Features

- **User Inputs**: Prompts for beam length (L), load positions (a), modulus of elasticity (E), moment of inertia (I), applied loads (W), and step size for calculations (Step).
- **Case Selection**: Allows selection from various loading cases (e.g., concentrated load at free end, uniform load over entire length) using a case identifier (e.g., "1A", "2B").
- **Calculations**: Computes reactions at supports, maximal moments, shear forces, and deflections along the beam.
- **Output**: Displays results in a structured format, including reactions at supports and maximal values of moments and deflections.

## Usage Instructions

1. **Start the Program**: Load and run the program on the HP-75.
2. **Input Parameters**: When prompted, enter the following:
   - **Case**: Enter the case identifier (e.g., "1A", "2B") corresponding to the loading scenario.
   - **L (Length)**: Total length of the beam.
   - **a (Position)**: Position of the applied load or start of the distributed load.
   - **E (Modulus of Elasticity)**: Young's modulus of the beam material.
   - **I (Moment of Inertia)**: Moment of inertia of the beam's cross-sectional area.
   - **W (Load)**: Magnitude of the applied load (for certain cases).
   - **wa (Start Load Intensity)**: Intensity of the distributed load at the start position (for certain cases).
   - **wl (End Load Intensity)**: Intensity of the distributed load at the end position (for certain cases).
   - **Step**: Interval for calculating and displaying results along the beam length.
3. **View Results**: The program will display:
   - Reactions at supports (RA, RB).
   - Moments at supports (MA, MB).
   - Maximal values of moments and deflections along the beam.
   - Tabulated deflection, moment, and shear force values at specified intervals along the beam.

 See demo below:

![](demo.gif)

## Notes

- Ensure that the case identifier corresponds to the desired loading scenario as per Roark's Formulas.
- Input values should be in consistent units to maintain accuracy.
- The program uses numerical methods to find roots and evaluate functions, ensuring precise calculations for various beam configurations.

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
See EMU75 help for how to install the Rom into the emulator.

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
7. The file HDRIVE1.dat is now able to be used to transfer directly its content with the PILBOX. Go to your ILPER folder and replace the HDRIVE1.dat file from ILPER with the one from EMU75 (backup the old one before if needed). Connect you HP-75C/D to the PILBOX, run ILPER, and execute the following commands on your (real) HP-75C/D:
```bas
         ASSIGN IO ":P1,:M1,:M2,:I1"
         COPY "ROARK:M2" to "ROARK"
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
9. Close the file by executing from the keyboard:
```bas
CLEAR ":I1"
```

You'll find a PC text file named "emu_out.dat" in Emu75's home directory.
         
## Thanks

Many thanks to Jean-Francois Garnier, Christoph Giesselink, Namir Shammas, Robert Prosperi and Valentin Albillo.

## References

- Roark, R.J., Young, W.C., Budynas, R.G., & Sadegh, A.M. (2020). *Roark's Formulas for Stress and Strain* (9th ed.). McGraw-Hill Education.
http://materiales.azc.uam.mx/gjl/Clases/MA10_I/Roark%27s%20formulas%20for%20stress%20and%20strain.pdf
- HP-75 Reference Manual https://literature.hpcalc.org/items/1073
- HP-75 Owener Manual. https://literature.hpcalc.org/items/1072
