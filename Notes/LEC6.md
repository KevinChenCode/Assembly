Practice
========

Write assembly language tcode that mimics the situtation in in the second block

```C
int* myptr;
int myval, yourval;

myval = 6;
myptr = &yourval;
*myptr = myval;
```

```Assembly
movi r8, 6
movia r12, yourval
stw r8, 0(r12)
```

yourval is a memory location!



Let's find the max int of list of 10

```assembly
InputList: .word 1, 9, -3, 0x4, 5, 6, -7, 9, 1, 0

-start:	
		movi 	r12,	9
		movia 	r11,	InputList
		ldw 	r16,	0(r11)

-LoopI:	
		addi	r11, 	r11,	4				#addi : goes to next address
		subi	r12,	r12,	1				#subi : decriments index
		beq		r12,	r0,	Endsrc				#beq : if both are equal(r0 is always 0)
		ldw		r13,	0(r11)					#get Next
		bgt		r13,	r16,	replace
		br 		LoopI

-Replace:
		mov r16, 	r13 						#replace max value
		br 	LoopI

-Endsrc:
		br 	Endsrc
``` 


#Branches

Used to change program flow
	
	`bxx	ra,	rb,	Dest`

where xx is:
	eq:		==
	gw:		!=
	lt:		<		
	gt:		>
	ge:		>=
	le:		<=
	r :		always

#Sections

directive defining groups of assembly that is loaded in the same area of memory

