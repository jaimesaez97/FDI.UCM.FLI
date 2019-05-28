# Fundamentos de los Lenguajes Informáticos
## Examen Junio 2018

### 1. [2,5 puntos]

L1.1 = {1^j0^k € {0,1}* | j >= 0 ^ k = (j mod 3)}
L1.2 = {1^j0^k € {0,1}* | j >= 0 ^ k = (j div 3)}

L1.1 reconoce a las cadenas de un número natural de 1s seguido de un número natural de 0s que es el resto de dividir el número de 1s entre tres.
Ej: 10, 1100, 111, 1110, 111100, 1111000...

En este lenguaje hay tres opciones: 
	- Cadena con 1 0.
	- Cadena con 2 0s.
	- Cadena sin 0s.
Es un lenguaje regular porque no depende de todo el número de unos, sino de una acotación del resto de número de 1s al dividirlo entre tres.

L1.2 reconoce a las cadenas de un número natural de 1s seguido de un número natural de 0s que es exactamente el número de 1s dividido entre 3.
EJ: 1, 11, 1110, 11110, 111110, 11111100...

Este lenguaje es claramente dependiente del contexto porque dependiendo del número de unos que escribamos habrá que escribir un número de 0s, sin acotación.

a)
APD M,, L(M) = L1.1
(q0,0) = q1
(q0,1) = q5
(q1,0) = q2
(q1,1) = q3
(q2,0) = q4
(q2,1) = q0
(q3,0) = q5
(q3,1) = q5
(q4,0) = q3
(q4,1) = q5
(q5,_) = q5	/*TrapState*/
	Final State q0, q3

ER(L1.1) = ((111)*(€ + 10 + 1100))

b)
Sea x € L1.2 ^ |x| >= n

x = 1^n0^(n/3)

P.t. u,v,w : x = uvw ^ 1 <= |v| <= |uv| <= n
	uv = 0^s 1 <= s <= n
	v  = 0^j 1 <= j <= s <= n

->

Ex. i >= 0 : x = uv^iw !€ L1.2

i = 0 => uv^0w = uw
	1^(n-j)0^(n/3) !€ L1.2
	
Habíamos elegido n/3 truncado porque de esta forma si n = 3 y quito j = 1, la cadena debería quedarse sin 0s y no es loq ue ocurre:
	x = 1110 	(n = 3, n/3 = 1)
	x = 110		(n = 2, n/3 != 1)
	
### 2. [2,5 puntos]

L2 = { a^nb^mc^p | m > n + p, siendo n,m,p > 0 }

Creo que este lenguaje es LIC porque se me ocurre un autómata de pila que vaya leyendo símbolos y no reconozca si m <= n + p.

AP M,, Lf(M) = L2

La idea para este autómata es la siguiente:
	- Apilar un número de As en la pila.
	- En cuanto entra la primera B cambio al estado de desapilar y quito todas las As.
		- Cuando salgo de este estado n = m y en la pila está Z0.
	- La primera B QUE SOBRA (m > n) no la guardo en la pila.
	- Sigo apilando Bs hasta que me aparezca una C.
	- En el último estado sigo apilando Cs MIENTRAS ME QUEDEN Bs EN LA PILA.
	
(q0,a,Z0) = (q1,AZ0)
(q0,b,Z0) = (q3,Z0) /*No apilo 1ª b sobrante*/
(q1,a,A)  = (q1,AA)
(q1,b,A)  = (q2,€)	
(q2,b,A)  = (q2,€)
(q2,b,Z0) = (q3,Z0)	/*No apilo 1ª b sobrante*/
(q3,b,B)  = (q3,Z0)
(q3,b,Z0) = (q3,BZ0)
(q3,c,B)  = (q4,€)
(q4,c,B)  = (q4,€)
	Final State q4
	
GIC
	S -> ABbC
	A -> aABb | €
	B -> bB | €
	C -> bBCc | €
	
### 3. [1,5 puntos]

Pide señalar *qué significa decidir un lenguaje* y construir una MT que *decida* L sobre el alfabeto {a,b}*.

L = { wa^(|w|a) | w € {a,b}* }

Decidir un lenguaje es una máquina de Turing que siempre para; es decir, para las cadenas que reconoce el lenguaje para en estado de aceptación y para las que no para en otro estado.

La primera idea que he pensado para este lenguaje es empezar por la izquierda:
	- Por cada A que me encuentre la borro y compruebo:
		- Si borro el primer símbolo que me encuentro, ¿a la izquierda hay un blanco? (Cadena de longitud 1)
			- He terminado.
		- ¿No? 
			- Voy al final derecho de la cadena, borro el primer símbolo y vuelvo a empezar.
