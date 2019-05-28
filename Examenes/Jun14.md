# Fundamentos de los Lenguajes Informáticos
## Examen Junio 2014


### Ejercicio 1. [2,5 puntos]

L1.1 = { a^nb^m | n ≥ m y m ≤ 2 }
L1.2 = { a^nb^m | n ≥ m y m ≥ 2 }

Ambos lenguajes son razonablemente parecidos, pero podemos darnos cuenta que el L1.2 es más complejo porque comprende muchísimas más palabras que L1.1. 

En L1.1. los casos en los que hay que controlar que el número de bs sea mayor al de as es muy acotado, ya que bs como mucho va a haber dos.

En L1.2. esto ya no es así ya que m puede ser cualquier valor entre 2 y +INF, por lo que el lenauje deja de ser regular.

a)
AP M,, L(M) = L1.1

(q0,a) = q1
(q0,b) = q5
(q1,a) = q2
(q1,b) = q3
(q2,a) = q2
(q2,b) = q4
(q3,a) = q5
(q3,b) = q5
(q4,a) = q5
(q4,b) = q3
(q5,-) = q5 /*Trap State*/

ER s : L(s) = L1.1

L(a + aa* b + aaa* bb)

b)
(P.t. n >= 1 Ex. x : x € L1.2 ^ |x| >= n ^ P.t. u,v,w : x = uvw ^ (1 <= |v| <= |uv| <= n) : Ex. i >= 0 : uv^iw € L1.2) ---->  L1.2 !€ REGs.

Supongamos x = a^nb^n,

uvw = a^nb^n

uv = a^s (1 <= s <= n)
v  = a^j (1 <= j <= s <= n)

Elegimos i=0, uv^iw = uv^0w = uw

uw = a^(n-j)b^n que !€ L1.2 -> L1.2 !€ REGs.

### Ejercicio 2.
L = { a^ib^jb^ka^l | i, j, k, l ≥ 0 y i = l y j = k }

A simple vista podríamos pensar que este lenguaje no es un LIC al necesitar dos pilas para guardar el número de caracteres, pero no es así.

Podemos ver que lo único que restringe b^jb^k j = k es que en el centro de la cadena haya un número par de bs, no es necesario guardarlo en la pila.

AP M,, Lf(M) = L2

(q0,a,Z0) = (q3,AZ0)
(q0,b,Z0) = (q1,Z0)
(q1,b,Z0) = (q2,Z0)
(q2,b,Z0) = (q1,Z0)
(q3,a,A)  = (q3,AA)
(q3,b,A)  = (q4,A)
(q4,b,A)  = (q5,A)
(q5,b,A)  = (q4,A)
(q5,a,A)  = (q6,€)
(q6,a,A)  = (q6,€)
	Final State {q0, q2, q6}


### Ejercicio 3. [2 puntos]

Se pide una Máquina de Turing que "divida entre 2":

q0315 => qF157 ∗ 1
q0014 => qF007 ∗ 0

Idea:
	- Recorrer los números de IZQUIERDA A DERECHA:
		- Si entra número PAR poner división exacta y seguir con el siguiente.
		- Si entra número IMPAR poner división exacta y pasar a estado de ACARREO.

// Transiciones de operación en NO ACARREO
(q0,0,0) = (q0,->)
(q0,1,0) = (q1,->)
(q0,2,1) = (q0,->)
(q0,3,1) = (q1,->)
(q0,4,2) = (q0,->)
(q0,5,2) = (q1,->)
(q0,6,3) = (q0,->)
(q0,7,3) = (q1,->)
(q0,8,4) = (q0,->)
(q0,9,4) = (q1,->)
// Transiciones de operación en ACARREO
(q1,0,5) = (q0,->)
(q1,1,5) = (q1,->)
(q1,2,6) = (q0,->)
(q1,3,6) = (q1,->)
(q1,4,7) = (q0,->)
(q1,5,7) = (q1,->)
(q1,6,8) = (q0,->)
(q1,7,8) = (q1,->)
(q1,8,9) = (q0,->)
(q1,9,9) = (q1,->)
// Transiciones de ESCRITURA RESTO PAR
(q0,#,*) = (q2,->)
(q2,_,0) = (q4,<-)
// Transiciones de ESCRITURA RESTO IMPAR
(q1,#,*) = (q3,->)
(q3,#,1) = (q4,<-)
// Transiciones de PRESENTACIÓN SALIDA
(q4,_,_) = (q4,<-)	// _ representa todo menos #
(q4,#,#) = (qF,->)