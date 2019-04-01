# Hoja 4: Gramáticas Independientes del Contexto

## Ejercicio 1
### $\sigma = {a,b}
### L = { w € $\sigma | |w|a % 2 == 0}
abbbbbbbba
S -> bS | aA | $\epsilon 
A -> a | Ba
B -> bB | $\epsilon
    CORREGIR
## Ejercicio 2
### 0*1(0+1)*
S -> A1B
A -> 0A | $\epsilon
B -> 0B | 1B | $\epsilon
a) 00101

    S => A1B => 0A1B => 00A1B => 00$\epsilon1B => 0010B 0 => 00101B => 00101$\epsilon
    S=> A1B => A10B => A101B => A101$\epsilon => 0A101 => 00A101 => 00$\epsilon101 => 00101

b) 1001

    S => A1B => $\epsilon1B => 10B => 100B => 1001B => 1001$\epsilon => 1001
    S => A1B => A10B => A100B => A1001B => A1001$\epsilon => $\epsilon1001 => 1001
    
c) 00011
    
    S => A1B => 0A1B => 00A1B => 000A1B => 000$\epsilon1B => 00011B => 00011$\epsilon => 00011
    S => A1B => A11B => A11$\epsilon => 0A11 => 00A11 => 000A11 => 000$\epsilon11 => 00011

## Ejercicio 3
## S -> aSb | aSa | $\epsilon | bSb | bSa
El lenguaje descrito por S describe a cualquier cadena del alfabeto $\sigma = {0,1}* que tenga un número de caracteres par.
abababab
abbaba

## Ejercicio 4
### L = {x € {(,)}* | x tiene paréntesis equilibrados}
S -> (S) S | $\epsilon

## Ejercicio 5
### S -> aS | aSbS | $\epsilon
### w = aabab
### 1) Dos árboles derivación
               aabab
        /     /     \    \
       a     S       b    S
            / \         /  \  \   \
           a   S       a   S  b   S
               |           |      |
          $\epsilon   $\epsilon $\epsilon
          
               aabab
           /          \
          a            S
                  /   /   \   \
                 a    S    b   S
                      |    /  /  \  \
                $\epsilon a  S    b  S
                             |       |
                    $\epsilon $\epsilon 
                               
            
### 2) Dos derivaciones a la izquierda
    
    S => aSbS => aaSbS => aa$\epsilonbS => aabaSbS => aababS => aabab
    S => aS => aaSbS => aabaSbS => aababS => aabab
### 3) Dos derivaciones a la derecha

    S => aSbS => aSbaSbS => aSbaSb => aSbab => aaSbab => aabab
    S => aS => aaSbS => aabS => aabaSbS => aabaSb => aabab

## Ejercicio 6
### S -> aB | bA
### A -> a | aS | bAA
### B -> b | bS | aBB
### 1) w = aababb
Árbol de derivación:
            
                aababb
         /        \
        a          B
            /   |   \
           a    B    B
                |  /  |  \
                b a   B   B      
                      |   |
                      b   b
Derivación por la izquierda.
    
    S => aB => aaBB => aabB => aabaBB => aababB => aababb
    
Derivación por la derecha.

    S => aB => aaBB => aaBB => aaBaBB => aaBaBb => aaBabb => aababb
### 2) ¿Es G ambigua?
Sí, ya que la misma cadena tiene dos árboles de derivación posibles.

### 3) Razona L(G) = {w € {a,b}+ | |W|a = |W|b}

## Ejercicio 7
### S -> ABS | AB
### A -> aA | a
### B -> bA
Entendamos la gramática.
A describe al lenguaje L(aa*).
B describe al lenguaje L(baa*)
S describe al lenguaje L((aa*baa*)(aa*baa*)*).
    => L(a+ba+).
### a) aabaab
No pertenece al lenguaje ya que no hay ninguna manera posible de que la última letra de la cadena sea b.

### b) aaaaba
Sí pertenece al lenguaje.
    
    S => AB => aAB => aaAB => aaaAB => aaaaB => aaaabA => aaaaba
    
### c) aabbaa
No pertenece al lenguaje ya que no hay ninguna manera posible de generar una cadena con Bs consecutivas.

### d) abaaba
Sí pertenece al lenguaje.

    S => ABS => ABAB => aBAB => abAAB => abaAB => abaaB => abaabA => abaaba

## Ejercicio 8
### 1) {\alpha \in {a,b,0,\epsilon,+,.,*,(,)}* | \alpha es una E.R sobre {a,b}}

### 2) {x#xR# | x \in {0,1}+}*

## Ejercicio 9
### 1) {a^nb^m| m,n \geq 0 }


               