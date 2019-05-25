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
