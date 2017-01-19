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
