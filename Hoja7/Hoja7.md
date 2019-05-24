# Fundamentos de los Lenguajes Informáticos
## Hoja 7

### Ejercicio 1.

L = { w € {a,b,c}* | |w| es par }

Idea: ir 'tapando' los extremos hasta que no qude ningún caracter.
Si queda 1, no es par.

MAL

### Ejercicio 2.

E = {a,b}
Buscar 2 aes consecutivas y parar en estado de aceptación.

(q0,b) = (q0,b,->)
(q0,a) = (q1,a,->)
(q1,a) = (q2,a,->)
(q1,b) = (q0,b,->)
	Final State q2
	
### Ejercicio 3.
M = ({q0,q1,q2,qf},{0,1},{0,1,#},δ,q0,€,{qf})

1.
δ(q0, 0) = (q1, 1, →), δ(q1, 1) = (q0, 0, →), δ(q1, #) = (qf , #, →).

Esta MT representa la operación NOT sobre una cadena binaria.
011100001 -> 100011110

2. 
δ(q0, 0) = (q0, #, →), δ(q0, 1) = (q1, #, →), δ(q1, 1) = (q1, #, →), δ(q1, #) = (qf , #, →).

Esta MT elimina todos los 0s de una cadena hasta que encuentra el primer 1 y luego borra todos los 1s, captando si la cadena queda vacía.

### Ejercicio 4.

n -> n+1

Idea: 
	- Ir hasta el final derecho de la cadena.
	- Recorrer hasta encontrar primer 0, que lo cambiamos a 1 y vamos a la derecha.
	- Recorrer (dcha) cambiando todos los 1s por 0s.
	
δ(q0, _) = (q0, _, →)
δ(q0, #) = (q1, #, <-)
δ(q1, 1) = (q1, 1, <-).
δ(q1, 0) = (q2, 1, ->)
δ(q2, 1) = (q2, 0, ->)
δ(q2, #) = (q3, #, <-)
δ(q3, _) = (q3, _, <-)
δ(q3, #) = (q0, #, ->) 

### Ejercicio 5.