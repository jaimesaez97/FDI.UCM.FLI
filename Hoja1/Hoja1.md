# Hoja 1 de Ejercicios.
## Ejercicio 1
### 1) |w| impar
inicial(q0).

aceptacion(q1).

q0 -> q1 : a,b

q1 -> q0 : a,b
### 2) w acaba en 12
inicial(q0).

aceptacion(q2).

q0 -> q1 : 1

q0 -> q0 : 2

q1 -> q2 : 2

q1 -> q1 : 1

q2 -> q1 : 1

q2 -> q0 : 2
### 3) 1212 no subcadena.
inicial(q0).

aceptacion(q0,q1,q2,q3).

q0 -> q0 : 2

q0 -> q1 : 1

q1 -> q1 : 1

q1 -> q2 : 2

q2 -> q0 : 2

q2 -> q3 : 1

q3 -> q1 : 1

q3 -> q4 : 2

q4 -> q4 : 1,2
### 4) 1212 subcadena w
inicial(q0).

aceptacion(q4).

q0 -> q0 : 2

q0 -> q1 : 1

q1 -> q1 : 1

q1 -> q2 : 2

q2 -> q0 : 2

q2 -> q3 : 1

q3 -> q1 : 1

q3 -> q4 : 2

q4 -> q4 : 1,2
	(Nos podemos dar cuenta que las transiciones son igual que en ejemplo 2.3 (nos piden lo contrario)).
### 5) |w|0 par y |w|1 par 
inicial(q0).

aceptacion(q0,q1,q2).

q0 -> q1 : 0

q0 -> q2 : 1

q1 -> q0 : 0

q1 -> q3 : 1

q2 -> q0 : 1

q2 -> q3 : 0

q3 -> q2 : 0

q3 -> q1 : 1

### 6) cada 1 en w está precedido y seguido por 2.
inicial(q0).

aceptacion(q0).

q0 -> q1 : 2

q2 -> q2 : 2

q2 -> q3 : 1

q3 -> q0 : 2

q3 -> q1 : 1

q1 -> q1 : 1,2	(TRAP_STATE)

### 7) 11 ni 22 subcadenas
inicial(q0).

aceptacion(q0,q1,q2).

q0 -> q1 : 1

q0 -> q2 : 2

q1 -> q3 : 1

q1 -> q2 : 2

q2 -> q1 : 1

q2 -> q3 : 2

q3 -> q3 : 1,2  (TRAP_STATE)

### 8) ni 12 ni 21 subcadenas
inicial(q0).

aceptacion(q0,q1,q2).

q0 -> q1 : 2

q0 -> q2 : 1

q1 -> q1 : 2

q1 -> q3 : 1

q2 -> q2 : 1

q2 -> q3 : 2

q3 -> q3 : 1,2	(TRAP_STATE)

### 9) |w| mod 5 != 0
inicial(q0).

aceptacion(q1,q2,q3,q4).

q0 -> q1 : a,b

q1 -> q2 : a,b

q2 -> q3 : a,b

q3 -> q4 : a,b

q4 -> q0 : a,b

## Ejercicio 2
inicial(A).

aceptacion(A,B).

A -> B : 0

A -> A : 1

B -> C : 0

B -> A : 1

C -> C : 0,1

Podemos observar que C es un estado trampa, y solo llega a C con una cadena 00.
Concluimos que este lenguaje reconoce todas las cadenas que no contienen dos ceros consecutivos.

## Ejercicio 3
### a)
Reconoce a todas las cadenas que no contienen un 0 después del primer 1.
### b)
(10)*
Reconoce todas las cadenas que no contienen un 0 antes que un 1 ni dos caracteres iguales consecutivos.
### c)
Reconoce a todas las cadenas que acaban en 1.
### d)
(0(01)*1)*
Reconoce a todas las cadenas que no contienen tres ceros consecutivos y el mismo número de ceros consecutivos ANTES que de unos consecutivos.
### e)
(01 + 10)*
Reconoce a todas las cadenas que no contienen dos ceros ni dos unos consecutivos.

## Ejercicio 4
### 1) 4º símb. por la DCH es 1.
inicial(q0).

aceptacion(q4).

q0 -> q0 : 0,1

q0 -> q1 : 1

q1 -> q2 : 0,1

q2 -> q3 : 0,1

q3 -> q4 : 0,1
### 2) w = z1azaz2 siendo z,z1,z2 € {a,b}* y |z| = 4i para algun i >= 0
inicial(q0).

aceptacion(q5).

q0 -> q0 : a,b

q0 -> q1 : a

q1 -> q2 : a,b

q2 -> q3 : a,b

q3 -> q4 : a,b

q4 -> q1 : a,b

q1 -> q2 : a

q5 -> q5 : a,b
### 3) |w| >= 5 y |sufix(w)| = 5 y empieza por a
inicial(q0).

aceptacion(q5).

q0 -> q0 : a,b

q0 -> q1 : a

q1 -> q2 : a,b

q2 -> q3 : a,b

q3 -> q4 : a,b

q4 -> q5 : a,b
### 4) {ab}* {ba} *
inicial(q0).

aceptacion(q0,q2).

q0 -> q1 : a

q0 -> q2 : b

q1 -> q3 : b

q2 -> q3 : a

q3 -> a3 : a

a3 -> q2 : b
### 5) prefijo ba o bba
inicial(q0).

aceptacion(q3).

q0 -> q1 : b

q1 -> q2 : b

q1 -> q3 : a

q2 -> q3 : a

q3 -> q3 : a,b


## Ejercicio 5

PEREZOTE

## Ejercicio 6
### a)
inicial(q0).

aceptacion(q2,q5,q6).

estados:

q0 : {q0}

q1 : {q2}

q2 : {q1,q2}

q3 : {q3}

q4 : {q4}

q5 : {q1,q3}

q6 : {q1,q0}

q0 -> q1 : 1

q0 -> q2 : 0

q1 -> q1 : 0,1	(TRAP_STATE)

q2 -> q3 : 0

q2 -> q5 : 1

q3 -> q0 : 1

q3 -> q4 : 0

q4 -> q1 : 0

q4 -> q0 : 1

q5 -> q4 : 0

q5 -> q6 : 1

### b)

inicial(q0).

aceptacion(q3,q4,q7,q8,q9).

estados:

q0: {q0}

q1: {q1}

q2: {q2}

q3: {q0,q3}

q4: {q0,q4}

q5: {q1,q2}

q6: {q0,q1}

q7: {q1,q3}

q8: {q0,q2}

q9: {q3}

(q0,a) = q1

(q0,b) = q2

(q1,a) = q3

(q1,b) = TRAP_STATE

(q2,a) = TRAP_STATE

(q2,b) = q4

(q3,a) = q5

(q3,b) = q2

(q4,a) = q1

(q4,b) = q6

(q5,a) = q9

(q5,b) = TRAP_STATE

(q6,a) = q7

(q6,b) = q2

(q7,a) = q8

(q7,b) = TRAP_STATE

(q8,a) = q1

(q8,b) = q8

## Ejercicio 7
inicial(q0).

aceptacion().

estados:

q0 : {p}

q1 : {q}

q2 : {r}

q3 : {s}

q4 : {q,r}

q5 : {r,s}

q6 : {q,s}

q7 : {p,q,r}

q8 : {r,q,s}

(q0,0) = q6

(q0,1) = q1

(q1,0) = q2

(q1,1) = q4

(q2,0) = q3

(q2,1) = q0

(q3,0) = VACIO

(q3,1) = q0

(q4,0) = q5

(q4,1) = q7

(q5,0) = q3

(q5,1) = q0

(q6,0) = q2

(q6,1) = q4

(q7,0) = q8

(q7,1) = q7

(q8,0) = q5

(q8,1) = q7

## Ejercicio 8
### 1) a*b*c*
inicial(q0).

aceptacion(q2).

(q0,a) = q0

(q0,e) = q1

(q1,b) = q0

(q1,e) = q2

(q2,c) = q2

### 2) (01)* + (010)*
inicial(q0).

aceptacion(q2,q3).

(q0,0) = q0

(q1,1) = q2

(q2,0) = q3

(q3,0) = q1

(q3,1) = q2
### 3) Una de las cuatro últimas posiciones es 1.
iniical(q0).

aceptacion(q6).

(q0,-) = q0

(q0,0) = q2

(q0,1) = q1

(q1,-) = q3

(q2,0) = q4

(q2,1) = q3

(q3,-) = q4

(q4,1) = q5

(q5,-) = q6

### 4) {ab}*{ba}*

### 5) prefijo ba o bba
inicial(q0).

aceptacion(q3).

(q0,b) = q1.

(q1,a) = q3.

(q1,b) = q2.

(q2,a) = q3.

(q3,-) = q3.

## Ejercicio 9

### e-AFN -> AFN
inicial(p).

aceptacion(r).

(p,a) = {p}
(p,b) = {q,p}
(p,c) = {r,q}

(q,a) = {q,p}
(q,b) = {r,q}
(q,c) = {r}

(r,a) = {q,r}
(r,b) = {r}
(r,c) = {r}

### AFN -> AFD
inicial(q0).

aceptacion(q2,).

estados:
q0 : {p}.

q1 : {p,q}

q2 : {q,r}

q3 : {r}

q4 : {p,q,r}


(q0,a) = q0

(q0,b) = q1

(q0,c) = q2

(q1,a) = q1

(q1,b) = q4

(q1,c) = q4

(q2,a) = q4

(q2,b) = q2

(q2,c) = q3

(q3,a) = 

------------------
# NO ACABADO
------------------