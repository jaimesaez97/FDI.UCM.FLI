# Hoja 5 EJS

## Ejercicio 1
L = L(a(a+b)*b)

### 1.1 AFN -> AP M : L€(M) = Lf(M) = L
(q0,a) = {q1}
(q1,a) = {q1}
(q1,b) = {q1,q2}
Final State = q2

(q0,a,Z0) = {(q1,Z0)}
(q1,a,Z0) = {(q1,Z0)}
(q1,b,Z0) = {(q1,Z0), (q2,Z0)}
Final State = q2

### 1.2 AFD -> APD : Lf(M) = L
(q0,a) = q1
(q0,b) = q3
(q1,a) = q1
(q1,b) = q2
(q2,_) = q1
(q3,_) = q3 T.S.
Final State = q2

(q0,a,Z0) = (q1,Z0)
(q1,a,Z0) = (q1,Z0)
(q1,b,Z0) = (q2,Z0)
(q2,_,Z0) = (q1,Z0)
Final State = q2

## Ejercicio 2
L(aa*ba)
    
(q0,a,Z0) = (q0,AZ0)
(q0,a,A)  = (q0,A)
(q0,b,A)  = (q1,€)
(q1,a,Z0) = (q1,€)
Final State = q1
    L€(M) = Lf(M) = L

## Ejercicio 3
M = ({q,p},{0,1},{Z0,X},δ,q,Z0,{p})
[Transiciones Del Enunciado]

### 3.1 w = 01
[foto_movil_17.04/acreswasa]

### 3.2 w = 0011
[foto_movil_17.04/acreswasa]
 
### 3.3 w = 010
[foto_movil_17.04/acreswasa]

## Ejercicio 4
M = ({q1,q2,q3,q4},{a,b},{A,B},δ,q1,A,{q4})
[Transiciones_enunciado]

### 4.1. Lf(M) y L€(M)
Ambos lenguajes son {a^n b^n | n > 0}.

### 4.2. M'  : Lf(M') = Lf(M')\{a}

### 4.3. M'' : Lf(M'') = L€(M'') = Lf(M')

## Ejercicio 5
L = {x ∈ {a, b}∗ | |x|a = |x|b}

### 5.1. AP M: Lf(M) = L€(M) = L
(q0,a,Z0) = (q1,AZ0)
(q1,b,A)  = (q1,€)
(q1,a,B)  = (q1,€)
(q1,b,B)  = (q1,BB)
(q1,a,A)  = (q1,AA)
(q1,a,Z0) = (q1,AZ0)
(q1,b,Z0) = (q1,BZ0)
(q1,€,Z0) = (q0,€)
Final State q0

### 5.2. APD M' :  Lf(M') = L
(q0,a,Z0) = (q1,AZ0)
(q0,b,Z0) = (q1,BZ0)
(q1,a,A)  = (q1,AA)
(q1,b,B)  = (q1,BB)
(q1,a,B)  = (q2,€)
(q1,b,A)  = (q2,€)
(q2,a,Z0) = (q1,AZ0)
(q2,b,Z0) = (q1,BZ0)
Final State q2

## Ejercicio 6
L = {x ∈ {a, b}∗| |x|a > |x|b}
### 6.1. AP M : Lf(M) = L
(q0,a,Z0) = (q1,AZ0)
(q1,a,A)  = (q1,AA)
(q1,a,B)  = (q1,€)
(q1,b,A)  = (q1,€)
(q1,b,Z0) = (q2,BZ0)
(q2,b,B)  = (q2,BB)
(q2,b,Z0) = (q2,BZ0)
(q2,a,Z0) = (q2,AZ0)
(q2,a,A)  = (q2,AA)
(q2,a,B)  = (q2,€)
(q2,b,A)  = (q2,€)
(q2,€,A)  = (q1,A)
Final State = q1

### 6.2. Modifica M para L = Lf(M) = L€(M)

### 6.3. APD M' : Lf(M)

## Ejercicio 7
L = {x ∈ {(,)}∗| los paréntesis de x están equilibrados}
### 7.1. AP M de 1 estado : L€(M) = L
(q0,(,Z0) = (q0,()
(q0,(,()  = (q0,(()
(q0,),()  = (q0,€)
(q0,€,Z0) = (q0,€)
Final State q0

### 7.2. APD M' : Lf(M) = L
(q0,(,Z0) = (q1,()
(q1,),()  = (q1,€)
(q1,(,()  = (q1,(()
(q1,€,Z0) = (q2,€)
Final State q2

## Ejercicio 8
L = {x ∈ {a, b}∗| x = xR}
### AP M : Lf(M) = L€(M) = L
(q0,0,Z0) = (q0,0Z0)
(q0,1,Z0) = (q0,1Z0)
(q0,0,0)  = {(q0,00),(q1,€)}    // Aquí se introduce determinismo
(q0,1,1)  = {(q0,11),(q1,€)}
(q1,0,0)  = (q1,€)
(q1,1,1)  = (q1,€)
(q1,€,Z0) = (q1,€)
Final State q1

## Ejercicio 9

### 9.1. {0^n1^n | n € N}
(q0,0,Z0) = (q1,0Z0)
(q1,0,0)  = (q1,00)
(q1,1,0)  = (q2,e)
(q2,1,0)  = (q2,e)
Final State q2

### 9.2. {0^n1^m | n,m € N, n <= m}
(q0,0,Z0) = (q1,0Z0)
(q1,0,0)  = (q1,00)
(q1,1,0)  = (q2,e)
(q2,1,0)  = (q2,e)
(q2,1,Z0) = (q2,Z0)
Final State q2

### 9.3. {0^n1^m | n,m € N, n >= m
(q0,0,Z0) = (q1,0Z0)
(q1,0,0)  = (q1,00)
(q1,1,0)  = (q2,e)
(q2,1,0)  = (q2,e)
(q2,1,Z0) = (q2,Z0)
Final State {q1,q2}

### 9.4. {x € {0,1}* | |x|0 = 2*|x|1}

### 9.5. {c^n(ba)^m | n,m € N, n > m}

## Ejercicio 10

### 10.1. {w€ {a,b} | |w| impar y la primera letra coincide con la central}

### 10.2. {a(^m)b(^n) | m,n € N, n <= m <= 2n}
L = {a(^m)b(^n) | m,n € N, n <= m} U {a(^m)b(^n) | m,n € N, m <= 2n}

### 10.3. {a(^m)b(^n)c(^p)d(^q) | m,n,p,q € N, m + n = p + q}
(q0,a,Z0) = (q1,1Z0)
(q1,a,1)  = (q1,11)
(q1,b,1)  = (q2,11)
(q2,b,1)  = (q2,11)
(q2,c,1)  = (q3,e)
(q3,c,1)  = (q3,e)
(q3,d,1)  = (q4,e)
(q4,d,1)  = (q4,e)
(q4,d,Z0) = (q4,e)
Final State q4
    Lf(M) = L€(M) = L
    
### 10.4. {a(^i)b(^j)c(^k) | i,j,k € N, i != j}
Vemos que L = {a(^i)b(^j)c(^k)| i,j,k € N, i > j} U(disjunta) {a(^i)b(^j)c(^k)| i,j,k € N, i < j}
El camino de i > j es {q0,q1,q2}.
El camino de i < j es {q0,q3,q4}.

(q0,a,Z0) = (q1,NZ0)
(q0,b,Z0) = (q3,NZ0)
(q1,a,_)  = (q1,A_)
(q1,b,A)  = (q2,e)
(q1,b,N)  = (q0,e)
(q2,b,A)  = (q2,e)
(q2,b,N)  = (q0,e)
(q2,a,_)  = (q2,A_)
(q3,b,_)  = (q3,B_)
(q3,a,B)  = (q4,e)
(q3,a,N)  = (q0,e)
(q4,a,B)  = (q4,e)
(q4,a,N)  = (q0,e)
(q4,b,_)  = (q4,B_)
    Final State {q1,q2,q3,q4}
    N is used to indicate i = j
    
### 10.5. {a(^i)b(^j)c(^k) | i,j,k € N, i != j o j != k}
Vemos que L = {a(^i)b(^j)c(^k)| i,j,k € N, i != j} U {a(^i)b(^j)c(^k) | i,j,k € N, j != k}

### 10.6. {a(^n)b(^m)c(^n+m) | n,m € N}
Símbolos de pila:
    A : apilando as y bs
(q0,a,Z0) = (q1,AZ0)
(q0,b,Z0) = (q2,AZ0)
(q1,a,A)  = (q1,AA)
(q1,b,A)  = (q2,AA)
(q2,b,A)  = (q2,AA)
(q2,c,A)  = (q4,e)
(q3,c,A)  = (q4,A)  /* En este paso no desapilo: leo dos c's y desapilo 1 (q2) */
(q3,c,Z0) = (q4,Z0)
(q4,c,Z0) = (q3,e)  /* Si aceptamos por pila vacía, aquí |x|c = 2*(|x|a + |x|b) */
(q4,c,A)  = (q3,e)
    Final State {q0,q3}
    
### 10.7. {a(^i)b(^j)c(^k) | i,j,k € N, i = 2j o j = 2k}
L = {a(^i)b(^j)c(^k) | i,j,k € N, i = 2j} U {a(^i)b(^j)c(^k) | i,j,k € N, j = 2k}