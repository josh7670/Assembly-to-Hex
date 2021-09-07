# Risc-V Assembly-to-Hex Converter
The Risc-V Assembly-to-Hex Converter is essentially an assembler that reads a text file containing Risc_V assembly language, converts the instructions into hexadecimal text, and then writes them to a new text file. Note that this assembler only works for the RV32I ISA, and is meant to be used for running bare metal programs (i.e. without an operating system). 

## Using the Assembler
1. The assembler reads from a text file, so make sure the file you want to read from is in the same directory as the assembler. 
2. Make sure the name of the file you are opening for reading matches the file you want to read.
3. When you have finished writing the assembly text file, simply run the python program. If no errors are found in your assembly code, it will write hexadecimal text out to a file titled "mem.txt". 
4. To find if an instruction exists, simply search for it in the python file.

## Additional Info
* The assembler does not use ".text" or ".data"  directives. It assumes the text segment starts at instruction 0 in the program count. 
* You must manually load the starting address of your stack pointer in your assembly code. 
* Labels must be on their own line. They cannot share the same line as an instruction.
* Branch statements use labels, but not immediate values. 
* The assembler only recognizes the ABI name for each register (with the exception of "x0", which is used in place of "zero").
                [Risc_V Reg Names](https://en.wikichip.org/wiki/risc-v/registers)
* Due to hardware limitations of the RV32I ISA, branch statements can only reach 511 instructions in the positive direction and 512 instruction in the negative direction.
* The call instruction is also limited to this range, so calling a function more than 511 instructions away requires the use of lui (or auipc) and jalr instructions. 
* For more info on Risc-V go to [Risc-V Specs](https://riscv.org/technical/specifications/) and view "Volume 1" under "ISA Specification"

## Example Program
I have provided a sample program "pong.txt". It requires drivers for a VGA_80x60, 7-segment display, and keyboard in order to run on your Risc-V computer. Use "W" and "D" to control the left paddle movement, and use "O" and "K" to control the right paddle movement. Hit "Enter" to begin a new game. The score is displayed on the 7-segment display. 

