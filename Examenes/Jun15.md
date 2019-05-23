# Fundamentos Lenguajes Informáticos
## Examen Junio 2015


### 1. [2,5 puntos]

L1 = { xyx^r | x,y € {a,b}* | |x| = 1}
L2 = { xyx^r | x,y € {a,b}* | |y| = 1}

El lenguaje L1 reconoce todas las cadenas que empiezan y acaban por el mismo símbolo, puesto que la inversa de una cadena de longitud 1 es esa misma cadena. Por lo tanto, este lenguaje a todas las cadenas que empiezan y acaban por el mismo símbolo.
Este lenguaje es claramente regular.

El lenguaje L2 reconoce todas las cadenas que empiezan por una subcadena x, les sigue un símbolo cualquiera y acaban por la inversa de x. Este lenguaje es claramente dependiente del contexto.

a)
ER(L1) = ((a (a + b + c)* a) + (b (a + b + c)* b) )
AP M : L(M) = L1
(q0,a) = q1
(q0,b) = q2
(q1,a) = q3
(q1,b) = q1
(q2,a) = q2
(q2,b) = q4
(q3,a) = q3
(q3,b) = q1
(q4,a) = q2
(q4,b) = q4
	Final State: q3, q4

b)
Sea x € L2 ^ |x| >= n
P.t. u,v,w : x = uvw ^ 1 <= |uv| <= |v| <= n

->

Ex. i >= 0 : uv^iw !€ L2

Elegimos i = 0  => uv^0w = uw !€ L2 ya que 
		0^(n-j)10^n NO ES PALÍNDROMO (1 <= j)
		
### 2. [2 puntos]

L3 = {a^n b^n | n >= 0} ∩ {w € {a,b}* | |w| no es múltiplo de 6}

Este lenguaje reconoce a las cadenas que tienen un número NO MÚLTIPLO de 6 de 'a's y consecutivamente el mismo número de 'b's.
Este lenguaje es Independiente del Contexto porque el lenguaje {a^nb^n | n >= 0} es indpendiente del contexto por definición y aplicarle la restricción de que n % 6 != 0 no rompe esto.

Al ser un LIC, vamos a construir un AP que lo reconozca y una GIC que lo genere.

APD M,, Lf(M) = L€(M) = L3 (reconoce por estado final y por cola vacía)
Hay que construir un APD que se base en el del lenguaje {a^nb^n} pero que no reconozca si n % 6 == 0.

(q0,a,Z0) = (q1,AZ0)
(q1,a,A)  = (q2,AA)
(q1,b,A)  = (q7,€)
(q2,a,A)  = (q3,AA)
(q2,b,A)  = (q7,€)
(q3,a,A)  = (q4,AA)
(q3,b,A)  = (q4,€)
(q4,a,A)  = (q5,AA)
(q4,b,A)  = (q7,€)
(q5,a,A)  = (q6,AA)
(q5,b,A)  = (q7,€)
(q6,a,A)  = (q1,AA)		/*En este estado n % 6 == 0 -> NO SE PUEDE EMPEZAR A DESAPILAR*/
(q7,b,A)  = (q7,€)		/*Leemos todas las B y vacíamos pila*/
(q7,€,Z0) = (q8,€)		/*Vacío pila para reconocer*/
	Final State q8

GIC:
		PEDIR
		
### 3. [2 puntos]

L4 = { w1cw2 | w1,w2 € {a,b}* con w1 != w2 }

Máquina de Turing que DECIDA.

Hemos pensado en desarrollar una MT que 