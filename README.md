# Code-Conversion-Using-8085

## Aim:

To write 8085 microprocessor programs for converting:
1.	Hexadecimal to ASCII
2.	ASCII to Hexadecimal

## Apparatus Required:
•	Laptop with an internet connection

## Program 1: Hexadecimal to ASCII Conversion

## Algorithm:

1.	Load the hexadecimal number from memory location 4200H.
2.	Mask the upper nibble and check if it is less than 10H.
3.	If it is less than 10H, add 30H to convert it to ASCII.
4.	If it is greater than 10H, add 37H to convert it to ASCII.
5.	Repeat the process for the lower nibble.
6.	Store the ASCII equivalent in memory location 4300H and 4301H.

## Program:
```
LDA 4200H
MOV B,A
ANI 0F0H
RRC
RRC
RRC
RRC
CPI 0AH
JC ADD30
ADI 37H
JMP STORE1
ADD30: ADI 30H
STORE1:STA 4300H
MOV A,B
ANI 0FH
CPI 0AH
JC ADD30L
ADI 37H
JMP STORE2
ADD30L: ADI 30H
STORE2: STA 4301H
HLT
```

## Output:

<img width="1915" height="1028" alt="image" src="https://github.com/user-attachments/assets/b1937897-dd6f-4411-bd12-41c78f483ee0" />
<img width="1915" height="1022" alt="image" src="https://github.com/user-attachments/assets/27925c21-3b5c-4879-a690-2dd4956352fa" />

## Program 2: ASCII to Hexadecimal Conversion

## Algorithm:

1.	Load the first ASCII digit from memory location 4200H.
2.	Convert it to hexadecimal by subtracting 30H (if it's a number) or 37H (if it's a letter A-F).
3.	Load the second ASCII digit from memory location 4201H and repeat the process.
4.	Combine the upper and lower nibbles to form a hexadecimal number.
5.	Store the result in memory location 4300H.

## Program:
```
LDA 4200H
CPI 3AH
JC SUB30
SUI 37H
JMP STOREH
SUB30: SUI 30H

STOREH: MOV C, A
LDA 4201H
CPI 3AH
JC SUB30L
SUI 37H
JMP STOREL
SUB30L: SUI 30H
STOREL: MOV B,A
MOV A,C
RLC 
RLC
RLC
RLC
ADD B
STA 4300H
HLT
```

## Output:
<img width="1871" height="1024" alt="image" src="https://github.com/user-attachments/assets/9e90f309-40a2-4855-841d-1ff1e38c8dd3" />
<img width="1919" height="1018" alt="image" src="https://github.com/user-attachments/assets/e00df295-ee65-464a-a144-1837e519fc4f" />

## Result:

The 8085 microprocessor successfully converts hexadecimal numbers to ASCII and vice versa, storing the results in memory.



