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
