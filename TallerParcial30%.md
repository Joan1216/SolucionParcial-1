# TALLER ( PRIMER PARCIAL)
### ARQUITECTURA DE COMPUTADORES
#### 2017
###### Porcentaje 30%


8. ¿Por que la instrucción **CALL** utilizar el registro %o7 ---> registro 15.?
```
R/ Porque en el registro %o7 se almacena la dirección actual de la instrucción call
```
9. convertir el programa en lenguaje de máquina a lenguaje ensamblador y luego a lenguaje de alto nivel el siguiente programa:

```
10100000000100000010000000000101
10100010000100000011111111111010
10010000000001000100000000010000

 LENGUAJE DE MÁQUINA
 |op=10|rd=10000|op3=000010|rs1=00000|i=1|imm13=0000000000101|
 |op=10|rd=10001|op3=000000|rs1=00000|i=1|imm13=1111111111010|
 |op=10|rd=01000|op3=000000|rs1=10001|i=0|unsed(zero)=00000000|rs2=10000|

 LENGUAJE ENSAMBLADOR
 OR %g0, 5, %l0 
 OR %g0, -6,%l1  
 ADD %l1, %l2, %o0

 LENGUAJE DE ALTO NIVEL
 int main(){
 int a = 5;  
 int b = -6;
 return a + b;}
 ```


10. Convierta el siguiente código a lenguaje ensamblador, máquina **SPARC V8** y hexadecimal.
a. 
 ```c
 int main(){
        %L0
 int a = 8;
       %L1>>%L6
 int b = -16800;
      %L2
int c = 33; 
 if((a+b)<=b*32){
 	c=a+(b*2);
	}
else{
	return b;
}
	return a+c;
}

LENGUAJE ENSAMBLADOR

MAIN:

MOV 8 %L0             0x00000
SETHI ,%L0            0x00004
OR %L0 ,  , %L6       0x00008
MOV 33 %L2            0x0000C 
ADD %L0 , %L6 , %L3   0x00010
SLL %L6 , 5 , %L4     0x00014
CMP %L3 , %L4         0x00018
BG A SINO             0x0001C
SLL %L6 , 1 , %L5     0x00020
ADD %L0 , %L5 , %L2   0x00024
BA A SALIDA           0x00028
SINO                  0x0002C
  MOV %L6 , %O0       0x00030
SALIDA                0x00034
  ADD %L0 , %L2 , %O1 0x00038
  
LENGUAJE DE MÁQUINA  

/10/10000/000010/00000/1/0000000001000/     0x00000
/00/10001/100/1111111111111111101111/       0x00004
/10/11000/000010/10001/1/0001001100000/     0x00008
/10/10010/000010/00000/1/0000000100001/     0x0000C
/10/10011/000000/10000/0/00000000/10001/    0x00010
/10/10100/100101/10001/1/00000000/00101/  0x00014
CMP                                         0x00018
/00/1/1010/010/0000000000000000000100/      0x0001C
/10/10101/100101/10001/1/0000000000001/     0x00020
/10/10010/000000/10000/0/00000000/10101/    0x00024
/00/1/1000/010/0000000000000000000010/      0x00028
SINO
  /10/01000/000010/00000/0/00000000/10001/  0x0002C
SALIDA
  /10/01001/000000/10000/0/00000000/10010/  0x00030
  
HEXADECIMAL

0XA0102008
0X233FFFEF
0XB0146260
0XA4102021
0XA6040011
0XA92C6005
0X
0X34800004
0XAB2C6001
0XA4040015
0X30800002
0XA0100011
0XA2040012



 ```
b.
 ```c
int main(){
	int a = 8;
	int b = -10;
	if(a!=b){
		return c/8;
}
else{
	return b;
}
}

LENGUAJE ENSAMBLADOR

MAIN:

MOV 8 , %L0           0x00000
MOV -10 , %L2         0x00004
MOV # , %L1           0x00008
CMP %L0 , %L2         0x0000C
BNE A SALIDA1         0x00010
SRL %L1 , 3 , %O1     0x00014
SALIDA                0x00018
  ADD %L2 , 0 , %O0   0x0001C
  
LENGUAJE DE MÁQUINA

/10/10000/000010/00000/1/0000000001000/   0x00000
/10/10010/000010/00000/1/0000000000110/   0x00004
/10/10001/000010/00000/1/0000000000000/   0x00008
CMP                                       0x0000C
/00/1/1001/010/0000000000000000000010/    0x00010
/10/01001/100110/10001/1/00000000/00011/  0x0001C
SALIDA
  /10/01000/000000/10010/1/0000000000000/ 0x00020
  
HEXADECIMAL

0XA0102008
0XA4102006
0XA2102000
0X
0X32800002
0X93346003
0X9004A000

```
c.
 ```c
int main(){
	int a = -21180;
}

LENGUAJE ENSAMBLADOR

MAIN:

SETHI  , %L0         0x00000
OR %L0 , 324 , %L1   0x00004

LENGUAJE DE MÁQUINA

/00/10000/100/1111111111111111101011/  0x00000
/10/10001/000010/10000/1/0000101000100/  0x00004

HEXADECIMAL

0X213FFFEB     
0XA2142144
```

11. Convierta el siguiente código a lenguaje ensamblador, máquina **SPARC V8** y hexadecimal.
 ```c
int test(int a, int b, int c){
       %o1
	int z;
	z = a - b + c*4;
	return z + 2;
} 

int main(){
         %i0     %i1     %i2
	int p = 4, y = 2, c = -128;
	 %l0
	int x = test(p,y,c);
	return x + 45;
}
LENGUAJE ENSAMBLADOR

Test
MOV 0 %o1            0X0000
SLL %i2, 2, %l0      0x0004
SUB %i0, %i1, %l1    0x0008
ADD %l1, %l0, %o1    0x000C
JMPL %o7, 8, %g0     0x00010
ADD %o1, 2, %o1      0x00014

MAIN:

MOV 4 %i0            0x00018
MOV 2 %i1            0x0001C
CALL Test            0x00020
MOV -128 %i2         0x00024
ADD %l0, 45, %o0     0x00028

LENGUAJE DE MÁQUINA

10010010000100000010000000000000  0X0000
10100001001011100110000000000010  0X0004
10100010001001100000000000011001  0x0008
10010010000001000100000000010000  0x000C
10000001110000111110000000001000  0x00010
10010010000000100110000000000010  0x00014
10110000000100000010000000000100  0x00018
10110010000100000010000000000010  0x0001C
01111111111111111111111111110111  0x00020
10110100000100000011111110000001  0x00024
10010000000001000010000000101101  0x00028

Hexadecimal

0X92102000
0XA12E6002
0XA2260019
0X92044010
0X81C3E008
0X92026002
0XB0102004
0XB2102002
0X7FFFFFF7
0XB4103F81
0X9004202D
```
12. Implemente una función **Mul** en lenguaje de alto nivel, lenguaje ensamblador **SPARC V8** y lenguaje de máquina SPARC V8 que realice la multiplicación de dos enteros sin signo usando solo sumas.
 ```c
           %i1    %i2
 int mult(int a, int b){
     %l1  %l0
 int c=0, i=0;
 for(i=1;i<=b;i++)
 {
 c=c+a;
 }
 return c;
 }
 LENGUAJE ENSAMBLADOR
 
 MULT
 MOV 0 %i0           0x0000
 MOV 0 %L0           0X0004
 FOR
 CMP %l0, %i2        0x0008
 BG a SALIDA         0x000C
 ADD %i0, %i1, %i0   0x00010
 BA FOR              0x00014
 INC %l0             0x00018
 SALIDA
 ADD %i0, %g0, %o0   0x0001C
 
 LENGUAJE DE MÁQUINA
 
 10100010000100000010000000000000    0x0000
 10100000000100000010000000000000    0x0004
 
 00110100101111111111111111111100    0x000C
 10100010000001100000000000010000    0x00010
 00010000101111111111111111111100    0x00014
 10100000000001000010000000000001    0x00018
 10010000000001000100000000000000    0x0001C
 
 Hexadecimal
 
 0XA2102000
 0XA0102000
 0X
 0X34BFFFFC
 0XA2060010
 0X10BFFFFC
 0XA0042001
 0X90044000
 
 ```

13. Implemente la función **Pot** en lenguaje de alto nivel,lenguaje ensamblador **SPARC V8** y lenguaje de máquina SPARC V8 que realice la potencia de dos números enteros sin signo realizando llamados a la función desarrollada en el punto 9.
14. Implemente una función **Fact** en lenguaje de alto nivel, lenguaje ensamblador **SPARC V8** y lenguaje de máquina SPARC V8 que calcule el factorial de un número entero sin signo.
```c
 int Fact(int a){
   int i,c=1;
   for(i=1 ; i<=a ; i++)
     {
      c=i*c;
      }
      return c;   
  }
 LENGUAJE ENSAMBLADOR
 Fact

 MOV 1 %l0              0x0000
 MOV 1 %l1              0x0004
   FOR
 CMP %l0, %i0           0x0008
 BG a salida            0x000C
 SLL %l0, %1, %l1       0x00010
 BA FOR                 0x00014
 INC %l0                0x00018
   salida
 ADD %l1, %g0, %o0     0x0001c
 
   LENGUAJE DE MÁQUINA
  
  10100000000100000010000000000001
  10100010000100000010000000000001
  
  00110100100000000000000000000100
  10100001001011000000000000010001
  00010000101111111111111111111100
  10100000000001000010000000000001
  10000000000010001000000000000000
   
 Hexadecimal
 
 0XA0102001
 0XA2102001
 
 0X34800004
 0XA12C0011
 0X10BFFFFC
 0XA0042001
 0X90044000
  ```
15. Implemente una función **Div** en lenguaje de alto nivel, lenguaje ensamblador **SPARC V8** y lenguaje de máquina SPARC V8 que calcule la division de un número entero sin signo.
