## L1 = { a^m.b^n ∣0 ≤ n ≤ m ≤ 2n }

### 1.0. DEFINICIÓN
Cadenas de aes seguidas de bes (incluyendo la vacía) con un número de `a`s entre el número de `b`s y el doble.

Ideas:
- |w|a <= 2*|w|b

- |w|b <= |w|a

### 1.1. AP:
- Al llegar a Q3, se sabe el número de `a` apilados = `n`.
- El número de `b` debe ser:
    - Como mucho igual a n.
    - Como poco la mitad que n.

Probamos a partirlo:
    - L  = { a^m.b^n ∣ 0 ≤ n ≤ m }
    - L' = { a^m.b^n ∣ 0 ≤ m ≤ 2n }

L:

(q0,a,Z0) = (q1,AZ0)

(q1,a,A)  = (q1,AA)

(q1,b,A)  = (q1,e)

(q2,b,A)  = (q2,e)

L':

(q0,a,Z0) = (q1,AZ0)

(q1,a,A)  = (q2,A)

(q1,b,A)  = (q3,e)

(q2,a,A)  = (q1,AA)

(q2,b,A)  = (q3,e)

(q3,b,A)  = (q3,e)

    Final State q3
    
==> Creo que aquí se necesita NO DETERMINISMO : ¿cómo sabes a cuál de los dos lenguajes pertenece para apilar más o menos as?

### 1.2. GIC:

#### 1.2.1. Definición formal

S -> aSb | aaSb | \epsilon

#### 1.2.2. Explicación diseño

La proyección S representa al lenguaje de cadenas de as seguidas por cadenas de bs, incluyendo a la cadena vacía, en las que el número de bs está ligado al número de as: como mucho las mismas y como poco la mitad, y todos los valores comprendidos entre ellos.
No es difícil darse cuenta de ello ya que solo hay tres opciones:
    - Que sea la cadena vacía.
    - Que haya una a y una b en los extremos de la cadena.
    - Que haya dos as al principio y una b al final.

#### 1.2.3. Explicación ambigüedad

La gramática propuesta no es ambigua porque solo tiene dos términos distintos y la proyección del vacío con alguno de ellos no resulta el otro término. Es decir, la combinación de (a\epsilonb)* no da lugar a (aaSb) y viceversa.

Si hacemos el árbol de derivación para cualquier cadena podemos asegurar que es único.

# L2 = { x∈{0,1}∗ ∣|x|0 = 2⋅|x|1 }
### 2.0. DEFINICIÓN:
L2 representa al lenguaje que reconoce las cadenas de ceros y unos con exactamente el doble de ceros que de unos.

### 2.1. AP:
- AQUÍ ESTÁ EL NO DETERMINISMO

Idea:
- Saber siempre qué ha pasado en ele stado anterior.
01 : desapilo ese cero

00 : apilo un cero

10 : apilo uno y lo desapilo con el cero

11 : apilo dos unos
    
### 2.2. GIC:

#### 2.2.1. Definición formal
S -> 0T0  | 0U1   | 1U0  | 1V1 | e | 

T -> 1S   | 0TT0  | S1          (recuperar 1 1)

U -> 1UU0 | 0UU1  | 0S          (recuperar 1 0)

V -> 1VV1 | 10000 | 01000 | 00100 | 00010 | 00001        <- AMBIGUEDAD (S puede vacio => 0000e == 000e0)

#### 2.2.2. Explicación diseño

La proyección V representa aquel estado en el cual se deben recuperar cuatro 0s; es decir, se ha escrito una cantidad de unos tal como para que se deban escribir cuatro 0s para compensar. Eso se puede hacer de varias formas:
    - Recuperando 4 ceros y entremedias volver a la proyección S porque la cadena continua.
        - Este ejemplo sería por ejemplo la cadena `w = 111 00 010 000000 010 0000 111`.
    - Se puede seguir acumulando 1s e indicando los ceros que se deben recuperar (1VV1)

La proyección T representa aquel estado en el que se debe compensar un 1; es decir, se ha escrito una cantidad de ceros tal como para que se deba escribir un 1 para que haya igualdad. Aquí hay dos posibilidades:
    - 1S y continuar
    - Se puede seguir acumulando 0s e indicar los unos a recuperar (0TT0).
    
La proyección U representa aquel estado en el que se deben compensar 1 0; es decir, se ha escrito una cantidad de unos tal como para que se deban escribir un 0 para compensar. Se puede hacer de cuatro formas:
    - Escribir un 0 y continuar (0S).
    - Cadena que empieza por 0 y acaba por 1, e indicando que se deben recuperar dos 1s (0UU1).
    - Igual que ejemplo anterior pero empezando por 1 y acabando por 0 (1UU0).
 
 La proyección S es la que representa al lenguaje. Hay cinco opciones:
    - Que sea la cadena vacía.
    - Que empiece y acabe por cero, teniendo entre medias una subcadena con 1 uno más que la mitad de 0s.
    - Que empiece por uno y acabe por cero, teniendo entre medias una subcadena con un 0 más que el doble de 1s.
    - Que empiece por cero y acabe por uno, teniendo entre medias una subcadena con un 0 más que el doble de 1s.
    - Que empiece y acabe por uno, teniendo en miedio una subcadena con cuatro ceros más que el doble de 1s.

#### 2.2.3. Explicación ambigüedad
La gramática propuesta es ambigua porque al ser el vacío una proyección de S siempre se puede hacer, por ejemplo 1S o S1 (proyección T).


# L3 = { x∈{a,b,c}∗ ∣ ∃n,m: n > m ≥ 0 : x = cn(ba)m}
Si lo despejamos y aclaramos:
    L3 = { c^n(ba)^m ∣ 0 ≤ m < n}
Idea:
    - Puede haber tantas `c` como se quiera
    - El número de apariciones de subcadena (ba) es como máximo uno menos que el de c
### 3.0. DEFINICIÓN:
L3 representa el lenguaje que reconoce las cadenas que empiezan por un número de ces mayor o igual a un número de repeticiones de la subcadena ba que le sucede. También incluye a la cadena vacía.

### 3.1. AP:
Suponemos un APD M ,, Lf(M) = L3 (reconoce por estado final).
->(q0,c,Z0) = (q1,Z0)     

(q1,c,Z0) = (q2,CZ0)    Q1 : reconoce solo la primera c de la cadena Y NO LA APILA

(q2,c,C)  = (q2,CC)     Q2 : reconoce solo LA SEGUNDA c de la cadena Y LA APILA

(q2,b,C)  = (q3,C)       

(q3,a,C)  = (q4,e)      Q3 : reconoce una B (después de las Cs) y no desapila nada

(q4,b,C)  = (q3,C)      Q4 : reconoce una A después de la B y DESAPILA LA C

    Final State {q1,q2,q4}

Como se puede ver es determinista ya que no existe ninguna transición en la que se permita determinismo (que haya que elegir entre dos posibles estados a los que lleva la transición).

### 3.2. GIC:
#### 3.2.1. Definición formal

S -> cSB | cB

B -> ba  | e

#### 3.2.2. Explicación diseño

La proyección B representa las posibles veces que se puede escribir la subcadena ba. Vemos que no se retroalimenta, por lo que solo se podrán escribir tantas (ba) como Bs escriba anteriormente la proyección S. También puede ser vacío porque el lenguaje también reconoce aquellas cadenas w que tienen >= 0 y < |w|c.

La proyección S representa el lenguaje entero:
    - cSB : se pueden escribir tantas cs como se quieran, "guardando" al final cuántas (ba) como máximo podemos escribir.
    - cB  : para terminar la proyección (como no tiene vacío no acaba).

#### 3.2.3. Explicación ambigüedad

Creo que la gramática no es ambigua ya que las proyecciones son muy limitadas y no hay ninguna de ellas que se repita:
    - La B se dedica a escribir tantas subcadenas (ba) como se hayan almacenado anteriormente.
    - La S se dedica a escribir tantas Cs como se quiera, y guardar el número como Bs que se escribirán posteriormente.  