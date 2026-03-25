# Práctica 1: Seminario de Scheme

## Realización de la práctica ##

1. Instala en tu ordenador el DrRacket, tal y como se comenta al
   comienzo del [seminario de
   Scheme](../../seminarios/seminario1-scheme/seminario1-scheme.md)
   y crea un fichero `practica1.rkt`. Incluye en el fichero todo el código que
   escribas esta semana. Usa comentarios (líneas que comienzan con `;`) para separar secciones y
   realizar anotaciones. 

   Este fichero te servirá guardar tu práctica. Para realizar la entrega deberás
   copiar las soluciones de cada ejercicio en el cuestionario que habilitaremos en Moodle.

2. Lee el seminario de Scheme hasta el apartado 2.4. (_Tipos de datos
   simples_) incluido. Puedes ver el **vídeo 1** en la página con los
   vídeos del seminario (en la semana 1 en Moodle).
   
    A la vez que lees el texto o ves el vídeo debes probar en el
    intérprete de Racket todos los ejemplos que aparecen. Pruébalos de
    forma interactiva en el panel de interpretación del DrRacket y
    guarda las definiciones en el panel de edición del fichero `practica1.rkt`.

3. Haz el siguiente ejercicio.

    **Ejercicio 1**. Lanza DrRacket y escribe cada una de las siguientes instrucciones
    en el intérprete, intentado adivinar el resultado que va
    devolver. Están ordenadas por dificultad de arriba abajo y de
    izquierda a derecha. ¡¡Piensa en los resultados!!. Intenta
    entender cómo interpreta Scheme lo que escribes.


    |Instrucción      | Instrucción                                    |
    |---------------- | -----------------------------------------------|
    |`3`              | `(+ (- 4 (* 3 (/ 4 2) 4)) 3)`                  |
    |`(+ 1 2 )`       | `(* (+ (+ 2 3) 4) (* (* 3 3) 2))`              |
    |`(+ 1 2 3 4)`    | `(* (+ 2 3 4 5) 3 (- 5 2 1))`                  |
    |`(+)`            | `(+ (- (+ (- (+ 2 3) 5) 1) 2) 3)`              |
    |`(sqrt 25)`      | `(- (sqrt (* 5 ( + 3 2))) (+ 1 1 1 1))`        |
    |`(* (+ 2 3) 5)`  | `(> (* 3 (+ 2 (+ 3 1)) (+ 1 1)) (+ (* 2 2) 3))`|
    |`+`              | `(= (* 3 2) (+ 1 (+ 2 2) 1))`                  |
    |`#\+`            | `(not (> (+ 3 2) 5))`                          |
    |`"+"`            | `(and (even? 2) (odd? (+ 3 2)))`               |
    |`"hola"`         | `(remainder (+ 6 2) (+ 1 1))`                  |


4. Lee el apartado 2.5. (_Tipos de datos compuestos_) del seminario de
   Scheme, en el que se explica cómo se trabaja con cadenas, parejas y
   listas en Racket. Puedes ver el **vídeo 2** en la página con los
   vídeos del seminario en Moodle.
   
    Prueba en el intérprete de Racket todos los ejemplos que aparecen
    en el seminario.

5. Haz los siguientes ejercicios. 

    **Ejercicio 2** sobre parejas. Predice lo que hace Scheme cuando
    escribas las siguientes expresiones. Están ordenadas por
    dificultad de arriba abajo y de izquierda a derecha. Después,
    pruébalas y comprueba si tu predicción era correcta. Si no lo era,
    intenta comprender por qué.

    | Instrucción                           | Instrucción                       |
    |---------------------------------------|-----------------------------------|
    | `(cons 1 2)`                          | `(car (car (cons (cons 1 2) 3)))` |
    | `(car (cons 1 2))`                    | `(car (cons (cons 3 4) 2))`       |
    | `(cdr (cons 1 2))`                    | `(cdr (cons (cons 3 4) 2))`       |
    | `(cons (* 2 3) (/ 4 2))`              | `(cdr (cons 1 (cons 2 3)))`       |
    | `(cons (+ 2 1) (if (> 2 3) "2" "3"))` | `(cdr (car (cons (cons 1 2) 3)))` |


    **Ejercicio 3** sobre listas. Predice lo que hace Scheme cuando escribas las
    siguientes expresiones. Después, pruébalas y comprueba si tu
    predicción era correcta. Si no lo era, intenta comprender por qué.

    | Instrucción                                    | Instrucción                              |
    |------------------------------------------------|------------------------------------------|
    | `(list 1 2 3 4)`                               | `(cons 3 '(1 2 3))`                      |
    | `(rest (list 1 2 3 4))`                         | `(rest (cons #t (cons "Hola" (list 1))))` |
    | `(first '(1 2 3 4))`                             | `(first (list (list 1 2) 1 2 3 4))`        |
    | `(first (list #t 1 "Hola"))`                     | `(first (rest '((1 2) 1 2)))`               |
    | `(first (rest (list 1 2 3 4)))`                   | `(cons '(1 2 3) '(4 5 6))`               |
    | `(rest (rest '(1 2 3 4)))`                       | `(first (rest (list 1 2 3 4)))`             |
    | `(first (rest (rest (list 1 2 3 4))))`             | `(rest (rest (list 1 2 3 4)))`             |
    | `(list (* 2 2) (+ 1 2) (/ 4 2))`               | `(first (rest (rest (rest '(1 2 3 4)))))`     |
    | `(list (+ 2 3) (- 3 4) (string-ref "hola" 3))` |                                          |


    **Ejercicio 4** sobre listas. Intenta hacer los siguientes apartados
    sin utilizar el intérprete de Scheme. Después comprueba si has acertado.

    a) Dada la siguiente lista, indica la expresión correcta para que
    Scheme devuelva 3:

    ```racket
    (list 1 2 3 4 5)
    ```

    b) Dada la siguiente lista, indica la expresión correcta para que
    Scheme devuelva (5).

    ```racket
    (list 1 2 3 4 5)
    ```

    c) Dada la siguiente lista, indica la expresión correcta para que
    Scheme devuelva 5.

    ```racket
    (list 1 2 3 4 5)
    ```

    d) Dada la siguiente expresión, ¿qué devuelve Scheme?

    ```racket
    (first (rest (rest (list 1 (list 2 3) (list 4 5) 6))))
    ```

    e) Dada la siguiente expresión, ¿qué devuelve Scheme?

    ```racket
    (rest (rest '(1 (2 3) 4 5)))
    ```

6. Lee el apartado 3 (_Estructuras de
   control_) del seminario de Scheme. Puedes ver el
   **vídeo 3** hasta el minuto 7:00 en la página con los vídeos del
   seminario en Moodle.

7. Haz el siguiente ejercicio.

    **Ejercicio 5**. Predice lo que devolverá Scheme cuando escribas
    las siguientes expresiones. Están ordenadas por dificultad de
    arriba abajo y de izquierda a derecha. Después, pruébalas y
    comprueba si tu predicción era correcta. Si no lo era, intenta
    comprender por qué.

    | Instrucción                                    | Instrucción                                                               |
    |------------------------------------------------|---------------------------------------------------------------------------|
    | `(equal? "hola" "hola")`                       | `(+ (char->integer(integer->char 1200)) (char->integer #\A))`             |
    | `(string-ref "pepe" 1)`                        | `(string-length (make-string 7 #\E))`                                     |
    | `(substring "buenos dias" 1 4)`                | `(define a 3)` <br/> `(define b (+ a 1))`                                 |
    | `(= "hola" "hola")`                            | `(+ a b (* a b))`                                                         |
    | `(string-ref (substring "buenos dias" 2 5) 1)` | `(= a b)`                                                                 |
    | `(define pi 3.14159)`                          | `(if (and (> a b) (< b (* a b))) b a)`                                    |
    | `pi`                                           | `(cond ((= a 4) 6)`<br/>`((= b 4) (+ 6 7 a))`<br/>`(else 25))`            |
    | `"pi"`                                         | `(+ 2 (if (> b a) b a))`                                                  |
    | `(+ pi (+ pi pi))`                             | `(* (cond ((> a b) a)` <br/>`((< a b) b)`<br/>`(else -1))`<br/>`(+ a 1))` |
    | `(+ (* pi pi) (- 2 pi pi pi pi))`              | `((if (< a b) + -) a b)`                                                  |

8. Lee el resto del seminario, desde el apartado 4 hasta el
   final. Puedes ver el **vídeo 3** desde el minuto 7:00 hasta el
   final en la página con los vídeos del seminario en Moodle.

    - Prueba las funciones `ecuacion` y `convertir-temperatura` y
      reflexiona sobre cómo se implementan.
      
    - Prueba las pruebas unitarias de la función `ecuacion`. Cambia la
      definición de la función para introducir un error y provocar un
      fallo en las pruebas unitarias. Arregla la definición de la
      función para que vuelva a funcionar.

9. Haz el siguiente ejercicio.

    **Ejercicio 6**
    
    a) Define una función que calcule la distancia entre
    dos puntos, definidos por parejas de números enteros. Añade los
    siguientes tests para comprobar que funciona correctamente:
    
    
    | Entrada               | Salida   |
    |-----------------------|----------|
    | `p1:(0, 0) p2:(0, 10)`  | `10`     |
    | `p1:(0, 0) p2:(10, 0)`  | `10`     |
    | `p1:(0, 0) p2:(10, 10)` | `14.142135623730951`     |


    b) Usando la función `distancia` definida anteriormente,
    implementa la función `isosceles?` que recibe las tres
    coordenadas de los vértices de un triángulo y debe devolver si la
    figura es un triángulo isósceles.  Para ello, debes comprobar que
    los tres lados no son iguales (sería equilátero) y que sucede
    alguna de las tres siguientes condiciones: o bien el primer
    lado es igual que el segundo, o el primer lado es igual que el
    tercero, o el segundo lado es igual que el tercero.
    
    Fíjate en que las funciones booleanas `and`, `or` y
    `not` devuelven ya un valor booleano y que en programación
    funcional se usa la composición de funciones.
    
    Debes implementar la función usando una única expresión en la que
    no uses `if`, sino una composición de expresiones booleanas.
    
    !!! Hint "Pista"
        Recuerda del seminario que la función `=` puede tener más de dos
        argumentos. 

    Añade los tests correspondientes a los siguientes ejemplos:

    ```racket
    ; Ejemplos de triángulos isósceles:
    
    ; p1: (0, 0) p2: (3, 3) p3: (6, 0)
    ; p1: (2, 2) p2: (4, 0) p3: (0, 0)

    ; No isósceles:

    ; p1: (0, 0) p2: (0, 0) p3: (0, 0) (igual la distancia entre los tres puntos)
    ; p1: (0, 0) p2: (1, 1) p3: (3, 2) (ningún lado igual)
    
    (isosceles? '(0 . 0) '(3 . 0) '(6 . 0)) ; ⇒ #t
    (isosceles? '(2 . 2) '(4 . 0) '(0 . 0)) ; ⇒ #t
    (isosceles? '(0 . 0) '(0 . 0) '(0 . 0)) ; ⇒ #f
    (isosceles? '(0 . 0) '(1 . 1) '(3 . 2)) ; ⇒ #f
    ```


## Entrega de la práctica

Copia los ejercicios de la práctica en el cuestionario
_Entrega práctica 1_. Tienes de plazo hasta el próximo domingo a las 21:00h. Una vez finalizado el plazo de entrega podrás revisar el cuestionario y
visualizar la solución. En este caso el único ejercicio con solución es el
ejercicio 6. 

Una vez esté disponible la solución debes compararla con la
tuya. Puedes consultar cualquier duda con tu profesor de prácticas en
la clase de prácticas de la semana que viene.

# Práctica 2: Programación funcional en Scheme


## Ejercicios

Abre el DrRacket y crea el fichero `practica2.rkt` en el que deberás
escribir todos los ejemplos y soluciones de los ejercicios que
hagas. Escribe en comentarios tu nombre y apellidos. Usa también
comentarios para separar secciones y realizar anotaciones.  Incluye en
el fichero todo el código, ejemplos y resolución de ejercicios, que
hagas esta semana.

También debes añadir casos de prueba al código de todas las funciones
que implementes, tal y como vimos al final del seminario de
Scheme. Puedes usar algunos de los ejemplos de los enunciados, pero
debes también construir algunos casos nuevos, con ejemplos creados por
ti.
   
!!! Note "Siempre debes incluir casos de prueba"
    Los casos de prueba son un componente importante del código, ya
    que permiten guardar en el propio código una demostración de que
    éste funciona correctamente, así como unos ejemplos de cómo llamar
    a las funciones definidas.
   
### Ejercicio 1

a) Implementa la función `(binario-a-decimal b3 b2 b1 b0)` que reciba
4 bits que representan un número en binario y devuelva el número
decimal equivalente.

```racket
(binario-a-decimal 1 1 1 1) ; ⇒ 15
(binario-a-decimal 0 1 1 0) ; ⇒ 6
(binario-a-decimal 0 0 1 0) ; ⇒ 2
```

**Nota**: recuerda que para realizar esta conversión, se utiliza la siguiente fórmula:

```text
n = b3 * 2ˆ3 + b2 * 2ˆ2 + b1 * 2ˆ1 + b0 * 2ˆ0
```

Para la implementación de la expresión debes utilizar la función `expt`.


b) Implementa la función `(binario-a-hexadecimal b3 b2 b1 b0)` que
reciba 4 bits de un número representado en binario y devuelva el
carácter correspondiente a su representación en hexadecimal.

```racket
(binario-a-hexadecimal 1 1 1 1) ; ⇒ #\F
(binario-a-hexadecimal 0 1 1 0) ; ⇒ #\6
(binario-a-hexadecimal 1 0 1 0) ; ⇒ #\A
```

**Nota**: para realizar esta conversión, como paso intermedio debes
pasar primero el número binario a su representación decimal
(utilizando la función definida en el apartado anterior) y después a
su correspondiente hexadecimal. 

Recuerda que la representación hexadecimal de los números decimales
del 0 al 9 es el carácter correspondiente a ese número, y que el
número decimal 10 se representa con el carácter A, el 11 con el B, y
así sucesivamente hasta el 15 que es el F en hexadecimal.

Para la implementación de esta función auxiliar que pasa de decimal a
hexadecimal debes usar las funciones `integer->char` y
`char->integer`. En la función `char->integer` los caracteres
consecutivos están asociados con números consecutivos. Por ejemplo, el
entero correspondiente al carácter `#\A` es uno menos que el
correspondiente al carácter `#\B`. Los caracteres de números y los de
letras no son consecutivos.


### Ejercicio 2

El cifrado César es una técnica cifrado por sustitución en la que cada letra del
texto se codifica por la correspondiente desplazada un cierto número de
lugares. Por ejemplo, si usamos un desplazamiento de 5, el carácter `#\c` se
codificaría por el carácter `#\h` (el carácter 5 posiciones después de la `#\c`
en el alfabeto).

Vamos a cifrar y descifrar letras minúsculas y mayúsculas del alfabeto inglés
(26 caracteres: desde `#\a ó #\A)` hasta `#\z ó #\Z`). Vamos a trabajar con un
desplazamiento variable, positivo o negativo, dependiendo en que sentido rotemos
el alfabeto.

Define las funciones `(cifra-caracter char desplazamiento)` y `(descifra-caracter char
desplazamiento)` que implementen el cifrado anterior.

Para la implementación de las funciones anteriores debes definir y usar las
siguientes funciones auxiliares:

- `(encuentra-indice char)`
- `(encuentra-caracter indice)`
- `(entre-az? char)`
- `(rota-indice indice desplazamiento)`

La función `(rota-indice indice desplazamiento)` recibe el índice del carácter
original y calcula el índice del carácter cifrado.

**Consejo**: puedes usar la función `modulo` [ver documentación](https://docs.racket-lang.org/reference/generic-numbers.html#(def._((quote._~23~25kernel)._modulo))).

Analiza los siguientes ejemplos para entender mejor el funcionamiento de las
funciones auxiliares y las funciones principales:

```racket
(encuentra-indice #\a) ; ⇒ 0
(encuentra-indice #\b) ; ⇒ 1
(encuentra-indice #\m) ; ⇒ 12
(encuentra-indice #\z) ; ⇒ 25

(encuentra-caracter 0) ; ⇒ #\a
(encuentra-caracter 1) ; ⇒ #\b
(encuentra-caracter 12) ; ⇒ #\m
(encuentra-caracter 25) ; ⇒ #\z

(entre-az? #\a) ; ⇒ #t
(entre-az? #\m) ; ⇒ #t
(entre-az? #\z) ; ⇒ #t
(entre-az? #\`) ; ⇒ #f
(entre-az? #\{) ; ⇒ #f

(rota-indice 4 12) ; ⇒ 16)
(rota-indice 4 24) ; ⇒ 2)
(rota-indice 4 -5) ; ⇒ 25)

(cifra-caracter #\c 5) ; ⇒ #\h)
(cifra-caracter #\z -1) ; ⇒ #\y)
(cifra-caracter #\j 40) ; ⇒ #\x)
(cifra-caracter #\D 3) ; ⇒ #\G)
(cifra-caracter #\ñ 3) ; ⇒ #\ñ)

(descifra-caracter #\d 3) ; ⇒ #\a)
(descifra-caracter #\y -1) ; ⇒ #\z)
(descifra-caracter #\x 40) ; ⇒ #\j)
(descifra-caracter #\G 3) ; ⇒ #\D)
(descifra-caracter #\tab 3) ; ⇒ #\tab)
```


### Ejercicio 3

Implementa la función `(menor-de-tres n1 n2 n3)` que reciba tres
números como argumento y devuelva el menor de los tres, intentando que
el número de condiciones sea mínima.

No debes utilizar la función `min`. 

Implementa dos versiones de la función: 

- versión 1: usando la forma especial `if` 
- versión 2 (llámala `menor-de-tres-v2`): sin usar la forma especial
  `if`, sino definiendo una función auxiliar `(menor x y)` que
  devuelva el menor de dos números (en esta sí que deberías usar `if`)
  y construyendo la función `menor-de-tres-v2` como una composición de
  llamadas a esta función  auxiliar. 

```racket
(menor-de-tres 2 8 1) ;; ⇒ 1
(menor-de-tres-v2 3 0 3) ;; ⇒ 0
```

### Ejercicio 4

a) Supongamos las definiciones

```racket
(define (f x)
    (cons x 2))

(define (g x y)
    (cons x y))
```

Realiza la evaluación paso a paso de la siguiente expresión 

```racket
(g (f (+ 2 1)) (+ 1 1))
```

mediante el **modelo de sustitución**, utilizando tanto el **orden
aplicativo** y como el **orden normal**.

Escribe la solución entre comentarios en el propio fichero `.rkt` de
la práctica.

b) Supongamos las definiciones

```racket
(define (func-1 x)
    (/ x 0))
    
(define (func-2 x y)
    (if (= x 0)
        0
        y))
```

Igual que en el apartado anterior, realiza la evaluación paso a paso
de la siguiente expresión

```racket
(func-2 0 (func-1 10))
```

mediante el **modelo de sustitución**, utilizando tanto el **orden
aplicativo** y como el **orden normal**. Y escribe la solución entre
comentarios en el propio fichero `.rkt` de la práctica.


### Ejercicio 5

Implementa la función `(cadenas-mayores lista1 lista2)` que recibe 2
listas con 3 cadenas y devuelve otra lista con las 3 cadenas de mayor
longitud, comparando las cadenas de cada posición de la
lista. En el caso en que las cadenas tengan la misma longitud, se
devuelve la cadena de la primera lista.

!!! Note "Pista"
    Puedes utilizar las funciones `second` y `third` que devuelven el
    segundo y el tercer elemento de una lista.
    
```racket
(cadenas-mayores '("hola" "que" "tal") '("meme" "y" "adios")) ; ⇒ ("hola" "que" "adios")
(cadenas-mayores '("esto" "es" "lpp") '("hoy" "hay" "clase")) ; ⇒ ("esto" "hay" "clase")
```


### Ejercicio 6

a) Supongamos que queremos programar un juego de cartas que usa la baraja
francesa. Lo primero que debemos hacer es definir una forma de
representar las cartas y funciones que trabajen con esa
representación. En este ejercicio vamos a implementar esas funciones.

Representaremos una carta por un símbolo con dos letras: la primera
indicará su número o figura y la segunda el palo de la carta,
representado con el símbolo UTF correspondiente.

!!! Nota "Símbolos UTF de los palos de la baraja francesa"
    Puedes copiar los siguientes símbolos UTF y pegarlos en el código
    fuente de la práctica: ♠, ♣, ♥ y ♦ (picas, tréboles, corazones y
    diamantes).

Por ejemplo:

```racket
(define tres-de-picas '3♠)
(define as-de-corazones 'A♥)
(define jota-de-diamantes 'J♦)
```

Debemos definir la función `carta` que devuelve una pareja con el
valor correspondiente a su orden en la baraja francesa (un número) y
el nombre del palo de la carta (como símbolo, no como cadena).

```racket
(carta tres-de-picas) ; ⇒ (3 . Picas)
(carta as-de-corazones) ; ⇒ (1 . Corazones)
(carta 'K♣) ; ⇒ (12 . Tréboles)
```

Los valores de las cartas de la baraja francesa son:

```text
A (As) ⇒ 1
J (Jota) ⇒ 10
Q (Reina) ⇒ 11
K (Rey) ⇒ 12
```

Para realizar el ejercicio debes definir en primer lugar las funciones
`(obten-palo char)` y `(obten-valor char)` que devuelven el palo y el
valor, dado un carácter. Y debes implementar la función `carta` usando
estas dos funciones.

```racket
(obten-palo #\♠) ; ⇒ Picas
(obten-palo #\♥) ; ⇒ Corazones
(obten-valor #\3) ; ⇒ 3
(obten-valor #\J) ; ⇒ 10
```

!!! Note "Pista"
    Puedes utilizar las funciones `(symbol->string simbolo)` que convierte un
    símbolo en una cadena y `(string-ref cadena pos)` que devuelve el
    carácter de una cadena situado en una determinada posición.

b) Implementa la función `(jugada-mano carta1 carta2 carta3)` que recibe 3 cartas de la
baraja francesa y devuelve una cadena indicando si la jugada de tres
cartas contiene una **pareja** (dos cartas con el mismo valor), un **trío**
(las tres cartas tienen el mismo valor) o **nada** (las tres cartas
son distintas) y también el valor de la pareja o del trío.

Para obtener los valores de las cartas debes implementar la función
`(valor-carta carta)`.

Ejemplos:

```racket
(jugada-mano '3♥ '3♣ '3♥) ; ⇒ "trío de 3"
(jugada-mano 'K♦ '7♠ 'K♥) ; ⇒ "pareja de 12"
(jugada-mano '5♣ '4♣ '6♣) ; ⇒ "nada"
```

!!! Note "Números a cadenas"
    Puedes obtener una cadena correspondiente a un número usando la función
    `number->string`. Esta función solo la debes usar en este ejercicio.

