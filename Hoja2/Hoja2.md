# Ejercicios HOJA 2

## Ejercicio 1
### 1) Cadebas {a,b,c} con al menos 1 a y 1 b.
((a + b + c)* a(a + b + c)* + ((a + b + c)* b(a + b + c)* ))
### 2) Cadenas {0,1} cuyo 4º símbolo por la DCH es un 1.
(0 + 1)1(0+1)(0+1)(0+1)
### 3) Cadenas {0,1} con a lo sumo una pareja de unos consecutivos.
0*(e + 1)(e + 1)(0 + 01)*
### 4) Cadenas {0,1} cada pareja de ceros aparece antes que cualquier pareja de unos.
(0 + 01 + 0011)*

## Ejercicio 2 
### 1) (1 + e)(00*1)*0*
Lenguajes que no contienen más de 1 uno consecutivo.
### 2) (0*1*)*000(0+1)*
Lenguajes que contienen tres ceros.
### 3) (1 + 10)*
Lenguajes que no contienen 2 ceros consecutivos.
### 4) (1 + 01 + 001)*(e + 0 + 00)
Lenguajes que no contienen más de dos ceros consecutivos.
### 5) (0 + 1)* 011
Cadenas que acaban por 011.
### 6) (11 + 0)* (00 + 1)*
Cadenas que no contienen 1 cero solo después de un 0 suelto.

## Ejercicio 3
### 1) 01*
inicial(q0).

aceptacion(q1).

(q0,0) = q1

(q1,1) = q1

### 2) (0 + 1)01
inicial(q0).

aceptacin(q3).

(q0,0|1) = q1

(q1,0) = q2

(q2,1) = q3

### 3) 00(0+1)*
inicial(q0).

aceptacion(q2).

(q0,0) = q1

(q1,0) = q2

(q2,-) = q2

## Ejercicio 4
### 1) ER
(a + b)* a(a+b) 
### 2) AFN
inicial(q0).

aceptacion(q2).

(q0,-) = q0

(q0,a) = q1

(q1,-) = q2

### 3) AFD
inicial(q0).

aceptacion(q3).

(q0,a) = q2

(q0,b) = q1

(q1,a) = q0

(q2,-) = q3

## Ejercicio 5
### 1) (0 + 1)* 		0* + 1*
No son equivalentes.
0010 € L1
	!€ L2
### 2) 0(120)* 12		01(201)* 2
Sí son equivalentes.
### 3) (0* 1* )*     	(0* 1)*
Sí son equivalentes.
### 4) (01 + 0)* 0		0(10 + 0)*
Sí son equivalentes (L20 equivalencia).
### 5) (a + b)*   		a* (ba* )*
Sí son equivalentes (L20 equivalencia). 

### 6) b* a* + a* b*    a* + b*
No son equivalentes.
ab 	€ L1
   !€ L2
### 7) (cb* c + cb* b)  (cc)* + (cc)* (cb)(b+c)
Sí son equivalentes (L20).
## EJERCICIO 6
### 1) 111 no subcadena.
(0 + 10 + 110)*
### 2) w no tiene dos ceros consecutivos.
(e + 0)(1 + 01)*
### 3) |w|0 = |w|1 y ningún prefijo de w tiene dos ceros más que unos, ni dos unos más que ceros.
(01 + 10)*
### 4) |w|0 dibisible por 3
1*000*1*
### 5) Exactamente una aparicion de 111
(0 + 10 + 110)*111(0 + 10 + 110)*
### 6) |w| impar y no acaba en cero
(1 + 01)* (e + 0)
### 7) Toda b tiene una c detrás.
(a + c)*(b + e)(c + e)(a + c)*
### 8) |w|a <= 3
(b + c)*(e + a)(b + c)*(e + a)(b + c)*(e + a)(b + c)*

## Ejercicio 7
### 1)
(ba)*
### 2)
(ab(e + a))* 
### 3)
(aa(e + a))*

## Ejercicio 8
### 1) a((ab)∗cb)∗ + a(ababcb∗)∗a∗
Sí es ambigua: se puede obtener la cadena "a" tanto con el primer término como con el segundo.
### 2) aab∗(ab)∗ + ab∗ + a∗bba∗
Sí es ambigua: "abb" se puede conseguir con el segundo y con el tercer término.
### 3) aaba∗ + aaaba + aabba∗ + a
No es ambigua.
