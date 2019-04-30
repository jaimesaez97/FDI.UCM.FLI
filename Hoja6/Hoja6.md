# Ejercicio 1
L1 = {a^n b^2n c^m | n,m >= 0}

Voy a demostrar que L1 € LICs construyendo una GIC que lo genere:

S -> AC
A -> aAbb | \epsilon
C -> cC   | \epsilon

L2 = {a^n b^m c^2m | n,m >= 0}
Ahora se demuestra que L2 € LICs construyendo otra GIC que lo genere:

S -> AB
A -> aA | \epsilon
B -> bBcc | \epsilon

L1 ^ L2 = L = {a^n b^m c^m | m >= 0}
Demostramos que L no pertenece a LIC (intersección no cerrada para LICs).
L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y

Escogemos z = (a^n)(b^n)(c^n).
Hacemos Distinción de Casos:
1. Que solo haya un símbolo en vx (|vwx| <= n)
    - Hay tres posibilidades:
        - vx = a^j (1 <= j <= n)
        - vx = b^j (1 <= j <= n)
        - vx = c^j (1 <= j <= n)
    - Para este caso elegimos la iteración i = 0:
        - u(v^0)w(x^0)y = uwy !€ L1 ya que:
            - a^n-j b^n c^n € L (1 <= j)
            - a^n b^n-j c^n € L (1 <= j)
            - a^n b^n c^n-j € L (1 <= j)
                - Concluimos que para este caso **L !€ LICs**
2. Que haya dos símbolos en vx (tiene que caer entre a,b o entre b,c ya que |vwx| <= n)
    - Notación:
        - |vx|a = Sa
        - |vx|b = Sb
        - |vx|c = Sc
    - Aquí hay dos casos:
        - Sc = 0 y 1 <= Sa,Sb <= n
        - Sa = 0 y 1 <= Sb,Sc <= n
    - Aquí también elegimos la iteración i = 0:
        - u(v^0)w(x^0)y = uwy !€ L1 ya que:
            - a^n-Sa b^n-Sb c^n !€ L (1 <= Sa,Sb)
            - a^n b^n-Sb c^n-Sc !€ L (1 <= Sb,Sc)

Ya hemos concluido:
- L1 € LICs
- L2 € LICs
- L1^L2 !€ LICs --> Intersección no cerrado para LICs

# Ejercicio 2
## Demostrar LR = {w^R | w € L} € LICs si L € LICs.

¿Cómo se demuestra?

# Ejercicio 3
## Demostrar L € LICs -> L € REGs
No, no existe ningún lenguaje regular que no sea independiente del contexto, puesto que los REGs son un subconjunto de los LICs.

# Ejercicio 4
## 1. {a^i b^i c^j | 1 <= j <= 2i}
L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y
- Elegimos z = a^n b^n c^2n
Haciendo Distinción de Casos:
1. Que solo haya un símbolo (|vx| <= n)
    - Tres posibilidades:
        - vx = a^j (1 <= j <= n)
        - vx = b^j (1 <= j <= n)
        - vx = c^j (1 <= j <= n <= 2n ya que 1 <= n)
    - Eligiendo la iteración i = 2:
        - z = uvvwxxy !€ L ya que:
            - a^2n b^n c^n !€ L
            - a^n b^2n c^n !€ L
            - a^n b^n c^2n+j !€ L (2n + j >= n (1 <= j))
2. Que haya dos símbolos:
    - Notación:
        - |vx|a = Sa
        - |vx|b = Sb
        - |vx|c = Sc
    - Aquí hay dos posibilidades:
        - Sa = 0, 1 <= Sb,Sc <= n
        - Sc = 0, 1 <= Sa,Sb <= n
    - Eligiendo la iteración i = 2:
        - z = uvvwxxy !€ L ya que:
            - a^n b^n+Sb c^2n+Sc !€ L
                - Sb,Sc >= 1
            - a^n+Sa b^n+Sb c^2n !€ L
                - Sa,Sb >= 1 -> |c| > 2n

Ya podemos concluir que L !€ LICs.

## 2. {a^i | i es primo}

L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y
- Elegimos z = a^na

## 3. {www | w € {a,b}* }

L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y

- Elegimos z = (a^n)(a^n)(a^n)
Haciendo Distinción de Casos:
1. Que solo haya un símbolo:
    - Hay seis posibilidades:  
        - vx = a^j (1 <= j <= n)
        - vx = b
        - vx = a^j (1 <= j <= n)
        - vx = b
        - vx = a^j (1 <= j <= n)
        - vx = b
    - Si escogemos la iteración i = 0:
        - z = uvw !€ L ya que:
            - (a^n-j)b(a^n)b(a^n)b !€ L
            - (a^n)(a^n)b(a^n)b    !€ L
            - (a^n)b(a^n-j)b(a^n)b !€ L
            - (a^n)b(a^n)(a^n)b    !€ L
            - (a^n)b(a^n)b(a^n-j)b !€ L
            - (a^n)b(a^n)(a^n)     !€ L
2. Que haya dos símbolos:
    - Notación:
        - |vx|a = Sa
        - |vx|b = Sb
    - Hay una posibilidad:
        - 1 <= Sa < n, Sb = 1
    - Eligiendo iteración i = 0:
        - z = uvw !€ L ya que:
            - (a^n-Sa)(a^n)b(a^n)b !€ L
            - (a^n)b(a^n-Sa)(a^n)b !€ L
            - (a^n)b(a^n)b(a^n-Sa) !€ L

Ya hemos demostrado que L !€ LICs.

## 4. {x € {a,b,c}* | |x|a = |x|b = |x|c }
Para demostrar este lenguaje se puede usar la demostración usada en el ejercicio 1 (L1^L2).

## 4. {a^i b^j | j = i^2 }
Vamos a demostrar que L !€ LICs.

L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y

- Elegimos z = a^n b^(n^2).
Haciendo Distinción de Casos sobre vx:
1. Que solo contenga un símbolo
    - Hay dos posibilidades:
        - vx = a^j (1 <= j <= n)
        - vx = b^j (1 <= j <= n)
    - Eligiendo iteración i = 0:
        - Tenemos que z = uwy !€ L ya que:
            - a^(n-j) b^n^n   !€ L (1 <= j)
            - a^n b^((n^n)-j) !€ L (1 <= j)
2. Que contenga dos símbolos:
    - Notación:
        - |vx|a = Sa
        - |vx|b = Sb
    - Hay dos posiblidades:
        - Sa = 0, 1 <= Sb <= n
        - Sb = 0, 1 <= Sa <= n
    - Eligiendo la iteración i = 0:
        - z = uvw !€ L ya que:
            - a^(n-Sa) b^(n^n) !€ L
            - a^n b^((n^n)-Sb) !€ L

Ya hemos demostrado que L !€ LICs.

## 6. {a^i b^j a^k  | j = max(i,k)}

L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y
       
- Elegimos z = a^n b^n a^n.
Haciendo Distinción de Casos sobre vx:
1. Que solo contenga un símbolo
    - Hay tres posibilidades:
        - vx = a^j (1 <= j <= n)
        - vx = b^j (1 <= j <= n)
        - vx = a^j (1 <= j <= n)
    - Eligiendo la iteración i = 2:
        - z = uvvwxxy !€ L ya que:
            - a^(n+j) b^n a^n !€ L 
            - a^n b^(n+j) a^n !€ L
            - a^n b^n a^(n+j) !€ L

Ya hemos concluido que L !€ LICs.

## 7. {a^i b^j c^k | i < j < l}

L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y
- Eligiendo la cadena z = a bb c^n+2
Haciendo distinción de casos sobre vx:
1. Que solo haya un símbolo
    - Hay tres posibilidades:
        - vx = a^j (1 <= j <= n)
        - vx = b^j (1 <= j <= n)
        - vx = c^j (1 <= j <= n)
    - Eligiendo la iteración i = 0:
        - z = uvvwxxy !€ L ya que:
            - a^(1-j) b c^n+2 !€ L (1 <= j)
            - a b^(1+j) c^n+2 !€ L (1 <= j)
            - a b c^n+
            
    ¿CÓMO SE HACE ESTE?

## 8. {a^n b^n c^i | i <= n }

L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y

- Elegimos la cadena z = a^n b^n c
Haciendo Distinción de Casos sobre vx:
1. Que solo haya un símbolo:
    - Hay tres posibilidades:
        - vx = a^j (1 <= j <= n)
        - vx = b^j (1 <= j <= n)
        - vx = c
    - Eligiendo la iteración i = 2:
        - z = uvvwxxy !€ L ya que:
            - a^n+j b^n c !€ L
            - a^n b^n+j c !€ L
            - a^n b^n c^2 !€ L (cuando n=1)
2. Que haya dos símbolos:
    - Notación:
        - |vx|a = Sa
        - |vx|b = Sb
        - |vx|c = Sc
    - Hay dos posibilidades:
        - Sa = 0, 1 <= Sb,Sc <= n
        - Sc = 0, 1 <= Sa,Sb <= n
    - Eligiendo la iteración i = 2:
        - z = uvvwxxy !€ L ya que:
            - a^n+Sa b^n+Sb c !€ L (cuando Sa != Sb <-- NO VALE)
            - a^n b^n+Sb c+Sb !€ L 
    
    TERMINAR

## 9. {0^i 1^j | j = i^2}
Para este ejemplo nos vale el razonamiento del apartado 4.2 (este mismo ejercicio).

## 10. {a^n b^m c^k | n >= m >= k >= 0}

L.I. para demostrar !€ LICs:
    - P.t. n >= 1 : Ex.z: z € L ^ |z| >= n :
        - P.t. u,v,w,x,y € \sigma* :
            - z = uvwxy ^
            - 1 <= |vx| <= |vwx| <= n 
                - --> Ex.i : i >= 0 : 
                    - u(v^i)w(x^i)y

- Elegimos la cadena z = a^n b^n c^n
Haciendo Distinción de Casos sobre vx:
1. Que solo haya un símbolo
    - Hay tres posibilidades:
        - vx = a^j (1 <= j <= n)
        - vx = b^j (1 <= j <= n)
        - vx = c^j (1 <= j <= n) 
    - Eligiendo la iteración i = 0:
        - z = uvvwxxy !€ L ya que:
            - a^(n-j) b^n c^n !€ L
            - a^n b^(n-j) c^n !€ L
            - a^n b^
            
    TERMINAR
