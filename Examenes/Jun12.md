# Fundamentos de los Lenguajes Informáticos
## Junio 2012

### Ejercicio 1


### Ejercicio 2
L2 = { x € {a,b}* | |x|a = |x|b + 1 }

AP M ,, Lf(M) = L2

(q0,a,Z0) = (q1,Z0)
(q0,b,Z0) = (q3,Z0)
(q1,a,[]) = (q1,[]a)
(q1,b,A)  = (q2,€)
(q1,b,Z0) = (q0,Z0)
(q2,b,A)  = (q2,€)
(q2,a,Z0) = (q1,AZ0)
(q2,b,Z0) = (q0,Z0)
(q3,a,Z0) = (q0,Z0)
(q3,b,[]) = (q3,[]b)
(q3,a,B)  = (q4,€)
(q4,a,Z0) = (q0,Z0)
(q4,a,B)  = (q4,€)
(q4,b,B)  = (q4,BB)
	FInal State {q1,q2}

¿GIC?

### Ejercicio 3.

Sumar dos veces mismo número (x2).

1111 -> 11111111

La idea es la siguiente:
	- Recorro el dígito entero y coloco una marca al final.
	- Por cada símbolo antes de la marca lo borro y coloco dos después.

El proceso sería algo así:

...BBBB1111BBBB... => ...1111M... => ...111M11... => ...11M1111... => 1M111111... => ...M11111111... => ...11111111... 

(q0,1,1) = (q0,->)
(q0,#,M) = (q1,<-)
(q1,1,1) = (q1,<-)
(q1,#,#) = (q2,->)
(q2,1,#) = (q3,->)
(q2,M,#) = (q2,N)	// Esta transa limpia la M que queda al final
(q3,#,#) = (q3,->)
(q3,1,1) = (q3,->)
(q3,M,M) = (q3,->)
(q4,1,1) = (q4,->)
(q4,#,1) = (q5,->)
(q5,#,1) = (q6,<-)
(q6,1,1) = (q5,<-)
(q6,M,M) = (q6,<-)
(q6,#,#) = (q2,->)
