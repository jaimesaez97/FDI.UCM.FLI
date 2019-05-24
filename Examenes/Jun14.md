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