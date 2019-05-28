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
G = ({S}, {a,b}, S, 'producciones de abajo')

S -> ab | aabb | aaaSbbb
		
### 3. [2 puntos]

L4 = { w1cw2 | w1,w2 € {a,b}* con w1 != w2 }

Máquina de Turing que DECIDA.

Idea:
	- Recorrer la cadena de derecha a izquierda y ver si el primer símbolo que se lee coincide con el primero después de leer una c.

Casos Límite:
	- w1 subcadena de w2 (comprobado en q8)
	- w2 subcadena de w1 (comprobado en q2,q5 si llega blanco)
	- #c# (comprobado en q6)
	
(q0,a,0) = (q1,->)
(q0,#,#) = (q6,->)
(q0,c,c) = (q8,->)	/* q8: Comprueba caso en que w1 sea subcadena de w2 */
(q1,a,a) = (q1,->)	
(q1,b,b) = (q1,->)
(q1,c,c) = (q2,->)	/* Muevo cursor a la derecha de la C */
(q2,*,*) = (q2,->)	/* Me salto las letras que coinciden y he tapado */
(q2,a,*) = (q3,->)	/* Símbolos coincidentes: marco y a vuelvo a empezar */
(q2,b,b) = (qF,N)
(q2,#,#) = (qF,N)	/* Si me encuentro aquí un blanco es el caso en que w2 es subcadena de w1 (f.e. ababcaba)  */
(q3,a,a) = (q3,<-)	/* q3 se encarga de volver a la primera posición a la derecha del último 0 marcado */
(q3,b,b) = (q3,<-)
(q3,c,c) = (q3,<-)
(q3,*,*) = (q3,<-)
(q3,0,0) = (q0,->)	/*Vuelvo a la izquierda*/
(q4,a,a) = (q4,->)
(q4,b,b) = (q4,->)
(q4,c,c) = (q5,->)
(q5,*,*) = (q5,->)
(q5,a,a) = (qF,N)
(q5,b,*) = (q3,<-)
(q5,#,#) = (qF,N)	/* Si me encuentro aquí un blanco es el caso en que w2 es subcadena de w1 (f.e. bababcbaba)  */
(q6,c,c) = (q7,->)	/*q6,q7 sirven para reconocer #c# (caso extremo)*/
(q7,#,#) = (qF,N)
(q8,*,*) = (q8,->)	/* Leo toda la subcadena de w2 que coincide con w1 */
(q8,a,a) = (qF,N)	/* Si me encuentro algún símbolo, reconozco */
(q8,b,b) = (qF,N)
	Final State {qF}
