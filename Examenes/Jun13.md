# Fundamentos de los Lenguajes Informáticos
## Examen Junio 2013


### Ejercicio 1. [2 puntos]
L1 = { w € {a,b} | |w| impar y primer símbolo coincide con el central}

Podemos concluir que L no es regular si apelamos a la dependencia del contexto que supone: hay que guardar cuál es la letra central para cerciorar que es igual que la primera, y esto no se consigue con lenguajes regulares.

Vamos a desmotrar su no pertenencia a través del lema del bombeo:

(P.t. n >= 1 Ex. x : |x| >= n ^ x € L1 : P.t. u,v,w : x = uvw ^ 1 <= |v| <= |uv| <= n : Ex.i >= 0 : uv^iw € L2) -> L2 !€ REGs

Elegimos la cadena x = ba^nba^nb.
uv = ba^s (1 <= s <= n-1)

v  = a^j (1 <= s <= j <= n-1)

Suponiendo i = 0, uv^0w = uw = ba^(n-j)ba^nb € L2.


### Ejercicio 2. [3 puntos]

L2 = { a^nb^ma^(n+m) | n,m >= 0 }

Este lenguaje es dependiente del contexto, ya que solo hay que contar el número de as y bs que apilamos y luego desapilar el doble; es decir, desapilar una por cada a entrante.

AP M,, Lf(M) = L2:

(q0,a,Z0) = (q1,AZ0)
(q0,b,Z0) = (q2,AZ0)
(q1,a,A)  = (q1,AA)
(q1,b,A)  = (q2,AA)
(q2,b,A)  = (q2,AA)
(q2,a,A)  = (q3,A) // Aquí no borramos (primera) 
(q3,a,A)  = (q4,€) // Borramos aquí (segunda)
(q4,a,A)  = (q3,A) // Aquí no borramos (primera del siguiente par)
	Final State {q4}


### Ejercicio 3. [2 puntos]

Vamos a plantear una MT que multiplique por tres el número de la cinta representado en base 10.

Para ello hay que plantear la idea:
	- Primero recorreremos la cadena entera para empezar por la derecha.
	- Iremos leyendo caracteres y llevaremos estados en función del ACARREO:
		- En q1 no hay acarreo.
		- En q2 hay 1 de acarreo.
		- En q3 hay 2 de acarreo.

(q0,digit,digit) = (q1,->)
(q1,0,0) = (q1,<-)
(q1,1,3) = (q1,<-)
(q1,2,6) = (q1,<-)
(q1,3,9) = (q1,<-)
(q1,4,2) = (q2,<-)
(q1,5,5) = (q2,<-)
(q1,6,8) = (q2,<-)
(q1,7,1) = (q3,<-)
(q1,8,4) = (q3,<-)
(q1,9,7) = (q3,<-)

(q2,#,1) = (q1,<-)
(q2,0,1) = (q1,<-)
(q2,1,4) = (q1,<-)
(q2,2,7) = (q1,<-)
(q2,3,0) = (q2,<-)
(q2,4,3) = (q2,<-)
(q2,5,6) = (q2,<-)
(q2,6,9) = (q2,<-)
(q2,7,2) = (q3,<-)
(q2,8,5) = (q3,<-)
(q2,9,8) = (q3,<-)

(q3,#,2) = (q1,<-)
(q3,0,2) = (q1,<-)
(q3,1,5) = (q1,<-)
(q3,2,8) = (q1,<-)
(q3,3,1) = (q2,<-)
(q3,4,4) = (q2,<-)
(q3,5,7) = (q2,<-)
(q3,6,0) = (q3,<-)
(q3,7,3) = (q3,<-)
(q3,8,6) = (q3,<-)
(q3,9,9) = (q3,<-)

(q1,#,#) = (qF,->)
	Final State {qF}
