# TALLER ( PRIMER PARCIAL)
### ARQUITECTURA DE COMPUTADORES
#### 2017
###### Porcentaje 30%


8. ¿Por que la instrucción **CALL** utilizar el registro %o7 ---> registro 15.?
     ###### R/ Es la dirección donde se almacena la instrucción call
9. convertir el programa en lenguaje de máquina a lenguaje ensamblador y luego a lenguaje de alto nivel el siguiente programa:

```10100000000100000010000000000101```
###### R/ |10|10000|000010|000000|1|0000000000101|
######    OR %g0, 5, %l0   lenguaje ensamblador
######    int a = 5;       lenguaje de alto nivel
```10100010000100000011111111111010```
```10010000000001000100000000010000```


10. Convierta el siguiente código a lenguaje ensamblador, máquina **SPARC V8** y hexadecimal.
a.
 ```c
 int main(){
 int a = 8;
 int b = -16800;
 int c = 33; 
 if((a+b)<=b*32){
 	c=a+(b*2);
	}
else{
	return b;
}
	return a+c;
}
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
```
c.
 ```c
int main(){
	int a = -21180;
}
```

11. Convierta el siguiente código a lenguaje ensamblador, máquina **SPARC V8** y hexadecimal.
 ```c
int test(int a, int b, int c){
	int z;
	z = a - b + c*4;
	return z + 2;
}

int main(){
	int p = 4, y = 2, c = -128;
	int x = test(p,y,c);
	return x + 45;
}
 ```
12. Implemente una función **Mul** en lenguaje de alto nivel, lenguaje ensamblador **SPARC V8** y lenguaje de máquina SPARC V8 que realice la multiplicación de dos enteros sin signo usando solo sumas.
13. Implemente la función **Pot** en lenguaje de alto nivel,lenguaje ensamblador **SPARC V8** y lenguaje de máquina SPARC V8 que realice la potencia de dos números enteros sin signo realizando llamados a la función desarrollada en el punto 9.
14. Implemente una función **Fact** en lenguaje de alto nivel, lenguaje ensamblador **SPARC V8** y lenguaje de máquina SPARC V8 que calcule el factorial de un número entero sin signo.
15. Implemente una función **Div** en lenguaje de alto nivel, lenguaje ensamblador **SPARC V8** y lenguaje de máquina SPARC V8 que calcule la division de un número entero sin signo.
