# Mikro Assembler BASIC Commands


## ASSEMBLE - assemble the source code

### Commands
* `ASSEMBLE`

### Description
Assembles the source code to memory. It runs three passes then provides memory addresses for the start and end of each area of machine code used, or stops and displays an error.


## AUTO - automatically provide line numbers

### Commands
* `AUTO`
* `AUTO start`
* `AUTO start,step`

### Description
Outputs a line number ready for code to be entered and automatically displays the next line number when you press return.

To stop the AUTO function hold shift and press return, or press return twice.

Default start number is 100 and default step is 10.


## DELETE - remove specified lines

### Commands
* `DELETE start-end`
* `DELETE start-`
* `DELETE -end`

### Description
Delete the specified range of lines from memory.


## DISASSEMBLE - display a disassembled area of memory

### Commands
* `DISASSEMBLE start-end`
* `DISASSEMBLE start-`


## FIND - display all uses of a label

### Commands
* `FIND label`
* `FIND label,start-end`
* `FIND label,start-`


## FORMAT - display the formatted source code

### Commands
* `FORMAT`

### Description
Display the source code formatted in to columns better suited for assembler code.


## NUMBER - display a number in different formats

### Commands
* `NUMBER $hexadecimal`
* `NUMBER decimal`
* `NUMBER @octal`
* `NUMBER %binary`

### Description
Takes a number and displays its value in hexadecimal, decimal, octal, and binary.


## TABLE - display a list of assembled labels

### Commands
* `TABLE`

### Description
Used after a successful assembly to display an alphabetically sorted list of labels with their 16-bit hexadecimal values.


## TIM - start the machine code monitor

### Commands
* `TIM`
