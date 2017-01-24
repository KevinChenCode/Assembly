LECTURE 7
=========

How many bytes of memory does the following take?

If it starts at `0x1000`, what is the _address_ of `Iarray`

```Assembly
	Somestring: .ascii	"Boo!"			//4
	Barray: .byte		6, 3, -1, -7	//4
	Harray: .hword		9, 3, 7, 77		//8
	Iarray: .word		46, 29			//8
	movi	r6, 577						//4
	movia	r7, Iarray					//8
```

A: 0x1010, ie going up 16 bytes

##alignment
Words and instructions must be on "word boundaries" ie the address must divide by 4.

Half words must be at addresses divisable by 2.

use `.align 1` for half-words, `.align 2` for words

These skip momory and go to next aligned address

C:

```c
	int A = 0
	sptr = Somestring;
	while(*sptr)
		A++;
```

Assembly:

```Assembly
	mov		r8,		r0
	movia	r9,		Somestring
	
	Whilelabel:
		ldbu	r10,	0(r9)
		bgt		r9,		r0,		IsChar
		br	donewhile
		
	IsChar:
		addi	r8,		r8,		1
		addi	r9,		r9,		1
		br		Whilelabel
		
	donewhile:
		mov		r8,		r0
		movia	r9,		somestring
```

