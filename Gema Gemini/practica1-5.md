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


# Práctica 3: Recursión, parejas y diagramas box-and-pointer

## Antes de la clase de prácticas ##

- Antes de empezar esta práctica es importante que revises la solución
  de la práctica 2. Puedes preguntar las dudas al profesor de prácticas.

- Los siguientes ejercicios están basados en los conceptos de teoría:

    - 2.7 _Recursión_
    - 2.8 _Recursión y listas_ 
    - 3 _Tipos de datos compuestos en Scheme_ 
    - 4 _Listas en Scheme_


## Ejercicios

Abre el DrRacket y crea el fichero `practica3.rkt` en el que deberás
escribir todos los ejemplos y soluciones de los ejercicios que
hagas.

### Función auxiliar para dibujar diagramas caja y puntero ###

Descarga el [fichero `lpp.rkt`](https://raw.githubusercontent.com/domingogallardo/apuntes-lpp/master/src/lpp.rkt),
pulsando el botón derecho del ratón y seleccionando la opción _Guardar
como_ `lpp.rkt`. Guárdalo en la misma carpeta en la que tengas el
fichero `practica3.rkt`. Contiene la definición de una función
auxiliar `(caja-puntero dato)` que te permite crear diagramas caja y
puntero de estructuras de parejas.

El siguiente programa muestra un ejemplo del uso de esta función:

```racket
#lang racket
(require rackunit)
(require "lpp.rkt")

(caja-puntero '(1 . 2))
(caja-puntero (cons 1 (cons 2 (cons 3 4))))
(caja-puntero (list 1 2 3))
(caja-puntero '((1 2) . 2))
(caja-puntero '(1 (2 3) 4))
```

La siguiente imagen muestra la ejecución del programa en el DrRacket.

<img src="imagenes/programa-caja-puntero.png" width="400px"/>

Puedes mirar el código fuente del fichero `lpp.rkt` para curiosear
cómo está implementada la función `caja-puntero`. Se utiliza la
[librería de imágenes de
Racket](https://docs.racket-lang.org/teachpack/2htdpimage.html) `2htdp/image`.

Para usar la librería hay que incluir la siguiente línea en nuestro
programa:

```racket
#lang racket
(require 2htdp/image)
```

Una cosa muy interesante de esta librería es que define las imágenes
como objetos de primera clase del lenguaje, que pueden asignarse a
variables o pasarse como parámetro para construir otras imágenes. Lo
podemos ver en el siguiente ejemplo:

<img src="imagenes/libreria-imagenes.png" width="400px" />

Incluso podemos incluir imágenes en listas:

<img src="imagenes/lista-imagenes.png" width="370px" />


### Ejercicio 1 ###

a.1) Implementa la función recursiva `(minimo lista)` que recibe una lista
con números como argumento y devuelve el menor número de la
lista. Suponemos listas de 1 o más elementos.

Para la implementación debes usar la función `menor` definida en la
práctica anterior.

!!! Tip "Pista"

    Podemos expresar el caso general de la recursión de la
    siguiente forma:

    > El mínimo de los elementos de una lista es el menor entre el
    > primer elemento de la lista y el mínimo del resto de la lista.

    Y el caso base:
    
    > El mínimo de una lista con un único número es ese número.
    
    
Ejemplos:

```racket
(minimo '(2)) ; ⇒ 2
(minimo '(1 8 6 4 3)) ; ⇒ 1
(minimo '(1 -1 3 -6 4)) ; ⇒ -6
```

!!! Note "Cómo comprobar el caso base de `minimo`"
    Para el caso base de la función `minimo` debemos comprobar si la
    lista que recibimos tiene un solo elemento. En ese caso el mínimo
    de la lista es el propio elemento. Sería un error llamar a la
    recursión porque no se puede calcular el menor elemento de una
    lista vacía.
    
    La mejor forma de comprobar en Scheme si una lista tiene un solo
    elemento es:
    
    ```racket
    (null? (rest lista))
    ```
    
    Esta forma es más eficiente que llamar a la función `length` que necesita
    recorrer toda la lista. El coste de la instrucción `(null? (rest
    lista))` no depende de la longitud de la lista, es O(1). Sin
    embargo, la instrucción `(length lista)` tiene que recorrer toda
    la lista por lo que tiene una complejidad de O(n).

a.2) Vamos a investigar el funcionamiento de la recursión en la función
`minimo`. Supongamos la siguiente llamada:

```racket
(minimo '(1 8 6 4 3)) ; ⇒ 1
```

- ¿Qué lista se pasa como parámetro a la primera llamada recursiva a
  la función?
- ¿Qué devuelve esa llamada recursiva?
- ¿Con qué argumentos se llama a la función `menor` que devuelve el
  resultado final?

b) Implementa la función recursiva `(concatena lista-chars)` que recibe
una lista de caracteres y devuelve la cadena resultante de
concatenarlos.

Ejemplos:

```racket
(concatena '()) ; ⇒ ""
(concatena '(#\H #\o #\l #\a)) ; ⇒ "Hola"
(concatena '(#\S #\c #\h #\e #\m #\e #\space #\m #\o #\l #\a))  
; ⇒ "Scheme mola"
```

c) Implementa la función recursiva `(cifra-cadena cad desplazamiento)` que,
usando la función `cifra-caracter` de la práctica anterior, cifre una cadena
completa usando el cifrado de César. 

Implementa después la función `(descifra-cadena cad desplazamiento)` que
descifra una cadena completa. 

Ejemplos:

```racket
(cifra-cadena "En un lugar de la Mancha, de cuyo nombre no quiero acordarme" 10) ; ⇒
"Ox ex veqkb no vk Wkxmrk, no meiy xywlbo xy aesoby kmybnkbwo"

(descifra-cadena "Ox ex veqkb no vk Wkxmrk, no meiy xywlbo xy aesoby kmybnkbwo" 10) ; ⇒
"En un lugar de la Mancha, de cuyo nombre no quiero acordarme"
```

d) Implementa el predicado recursivo `(contiene? lista elemento)` que comprueba si
una lista tiene un elemento determinado. Después úsala para
implementar la función `(str-contiene? cadena char)` que comprueba si
una cadena contiene un carácter. Recuerda que la función `string->list`
que convierte una cadena en una lista de caracteres.

Ejemplos:

```racket
(contiene? '(algo 3 #\A) 3) ; ⇒ #t
(contiene? '(algo 3 #\A) "algo") ; ⇒ #f
(contiene? '(algo 3 #\A) 'algo) ; ⇒ #t
(str-contiene? "Hola" #\o) ; ⇒ #t
(str-contiene? "Esto es una frase" #\space) ; ⇒ #t
(str-contiene? "Hola" #\h) ; ⇒ #f
```


### Ejercicio 2 ###

a) Implementa el predicado recursivo `(todos-iguales? lista)` que
comprueba si todos los elementos de una lista son iguales.


```racket
(todos-iguales? '()) ; ⇒ #t
(todos-iguales? '(a)) ; ⇒ #t
(todos-iguales? '(a a a a a a a)) ; ⇒ #t
(todos-iguales? '((a b) (a b) (a b))) ; ⇒ #t
(todos-iguales? '(a a a a a b)) ; ⇒ #f
```

b) Implementa el predicado recursivo `(todos-distintos? lista)` que
comprueba si todos los elementos de una lista son distintos. Para su
implementación debes usar el predicado del ejercicio 1 `contiene?`.


```racket
(todos-distintos? '()) ; ⇒ #t
(todos-distintos? '(a)) ; ⇒ #t
(todos-distintos? '(a b c)) ; ⇒ #t
(todos-distintos? '(a b c a)) ; ⇒ #f
```

c) Implementa el predicado recursivo `(solo-dos-iguales? lista)`que
comprueba que solo hay dos elementos iguales en una lista (los únicos
elementos repetidos que hay en la lista se repiten dos veces). Para su
implementación puedes usar los predicados anteriores.

```racket
(solo-dos-iguales? '()) ; ⇒ #f
(solo-dos-iguales? '(a)) ; ⇒ #f
(solo-dos-iguales? '(a b c a)) ; ⇒ #t
(solo-dos-iguales? '(a b c b a a)) ; ⇒ #f
(solo-dos-iguales? '(a b c a a)) ; ⇒ #f
(solo-dos-iguales? '(a b c a b)) ; ⇒ #f
```


### Ejercicio 3 ###

a.1) Dado el siguiente _box & pointer_, escribe la expresión en Scheme
que define `p1` usando el mínimo número de llamadas a `list` y
`cons`. No debes utilizar expresiones con `quote` para construir las listas ni
las parejas. Puedes usar la función gráfica `caja-puntero` para comprobar si tu
solución es correcta. 

<img src="imagenes/box-and-pointer.png" width="200px"/>

a.2) Escribe las expresiones que devuelven `b` y `d` a partir de
`p1`. Debes usar las funciones sobre listas `first`, `second`, etc. si el argumento es una
lista y `car` y `cdr` si es una pareja que no forma parte de una lista.

b.1) Dado el siguiente diagrama caja y puntero, escribe la expresión en
Scheme que define `p2` usando el mínimo número de llamadas a `list` y `cons`.

<img src="imagenes/box-and-pointer2.png" width="250px"/>

b.2) Escribe las expresiones que devuelven `c` y `e` a partir de
`p2`. Debes usar las funciones sobre listas `first`, `second`, etc. si
el argumento es una lista y `car` y `cdr` si es una pareja que no
forma parte de una lista.

### Ejercicio 4 ###

Implementa la función recursiva `(contar-datos-iguales lista-parejas)`
que recibe una lista de parejas y devuelve el número de parejas que
tienen sus dos datos iguales.


```racket
(contar-datos-iguales '((2 . 3) ("hola" . "hola") (\#a . \#a) (true . false))) ; ⇒ 2
(contar-datos-iguales '((2 . "hola") ("hola" . 3) (\#a . true) (\#b . false))) ; ⇒ 0
```

### Ejercicio 5 ###

Vamos a seguir jugando al poker. Esta vez vamos a definir funciones
sobre **manos de cartas**, definidas como listas de 5 símbolos que
representan cartas.

Por ejemplo, las siguientes manos:

```racket
(define mano1 '(A♦ 2♦ 3♣ 4♦ 5♥))
(define mano2 '(J♦ J♣ J♠ J♥ K♣))
```

Copia de la práctica anterior la solución de la función `(valor-carta
carta)` que devuelve el valor numérico de una carta:

```racket
(valor-carta '5♣) ; ⇒ 5
(valor-carta 'K♦) ; ⇒ 12
```

a) Implementa la función `(palo-carta carta)` de forma similar a la
función `valor-carta` para que devuelva el símbolo con la descripción
del palo de la carta.

```racket
(palo-carta 'A♠) ; ⇒ Picas
(palo-carta '2♣) ; ⇒ Tréboles
(palo-carta '3♥) ; ⇒ Corazones
(palo-carta '4♦) ; ⇒ Diamantes
```

Tendrás que usar las funciones `valor-carta` y `palo-carta` para implementar las siguientes
funciones del ejercicio.

b) Implementa la función recursiva `(veces-palo lista palo)` que devuelve el
número de veces que aparece un palo en una lista de cartas.

```racket
(veces-palo '(5♠ 6♣ 7♥ 8♦ 9♠) 'Picas) ; ⇒ 2
(veces-palo '(J♠ Q♣ K♥) 'Diamantes) ; ⇒ 0
(veces-palo '(A♣ 2♥ 3♠) 'Corazones) ; ⇒ 1
(veces-palo '() 'Tréboles) ; ⇒ 0
```

Usando la función anterior, implementa el predicado `color?` que
comprueba si en una mano tenemos todas las cartas del mismo palo:

```racket
(color? '(5♣ J♦ J♣ Q♠ Q♥)) ; ⇒ #f
(color? '(2♦ 5♦ 6♦ J♦ K♦)) ; ⇒ #t
```

c) Implementa el predicado recursivo `escalera?` que recibe una lista
de cartas y comprueba si todas ellas tienen valores consecutivos,
ordenados de menor a mayor.


```racket
(escalera? '(5♣ 4♦ 3♣)) ; ⇒ #f
(escalera? '(8♣ 9♦ J♣ Q♦)) ; ⇒ #t
(escalera? '(8♣ 2♣)) ; ⇒ #f
(escalera? '(A♣ 2♦ 3♣)) ; ⇒ #t
```

Usando las funciones anteriores implementa la función
`(escalera-color? mano)` que comprueba si una mano de cartas es una
escalera de color. Suponemos que las cartas que forman la mano están
ordenadas de menor a mayor.

```racket
(escalera-color? '(5♣ 6♦ 7♣ 8♠ 9♥)) ; ⇒ #f
(escalera-color? '(A♦ 2♦ 3♦ 4♦ 5♦)) ; ⇒ #t
```

### Ejercicio 6 ###

a) Implementa las funciones `(suma-izq pareja n)` y `(suma-der pareja n)`
definidas de la siguiente forma:

- `(suma-izq pareja n)`: devuelve una nueva pareja con la parte izquierda
  incrementada en `n`.
- `(suma-der pareja n)`: devuelve una nueva pareja con la parte derecha
  incrementada en `n`.

Ejemplos:

```racket
(suma-izq (cons 10 20) 3)  ; ⇒ (13 . 20)
(suma-der (cons 10 20) 5)  ; ⇒ (10 . 25)
```

b.1) Implementa la función recursiva `(suma-impares-pares lista-num)`
que devuelva una pareja cuya parte izquierda sea la suma de los
números impares de la lista y la parte derecha la suma de los números
pares. Debes utilizar las funciones auxiliares definidas en el
apartado anterior. También puedes utilizar las funciones predefinidas
`even?` y `odd?`.

Ejemplos:

```racket
(suma-impares-pares '(3 2 1 4 8 7 6 5)) ; ⇒ (16 . 20)
(suma-impares-pares '(3 1 5))           ; ⇒ (9 . 0)
```
b.2) Dada la siguiente llamada, indica qué devuelve la primera llamada recursiva:

```racket
(suma-impares-pares '(2 1 2 1 4))
```

c) Implementa la función recursiva `(cadena-mayor lista)` que recibe un
lista de cadenas y devuelve una pareja con la cadena de mayor longitud
y dicha longitud.  En el caso de que haya más de una cadena con la
máxima longitud, se devolverá la última de ellas que aparezca en la
lista.

En el caso en que la lista sea vacía se devolverá la pareja con la
cadena vacía y un 0 (la longitud de la cadena vacía).

**Pista**: puedes utilizar la función `string-length`

```racket
(cadena-mayor '("vamos" "a" "obtener" "la" "cadena" "mayor")) ; ⇒  ("obtener" . 7)
(cadena-mayor '("prueba" "con" "maximo" "igual")) ; ⇒ ("maximo" . 6)
(cadena-mayor '()) ; ⇒ ("" . 0)
```


# Práctica 4: Funciones recursivas que devuelven listas

## Antes de la clase de prácticas ##

- Antes de empezar esta práctica es importante que revises la solución
  de la práctica 3. Puedes preguntar las dudas al profesor de prácticas.

- Los siguientes ejercicios están basados en los conceptos de teoría
vistos la semana pasada. Antes de la clase de prácticas debes repasar
todos los conceptos y **probar en el DrRacket** todos los ejemplos de
los siguientes apartados del tema 2 [_Programación
Funcional_](../../teoria/tema02-programacion-funcional/tema02-programacion-funcional.md#43-funciones-recursivas-que-construyen-listas):

    - 4.3. _Funciones recursivas que construyen listas_
    - 4.4. _Funciones con número variable de argumentos_
    - 5 _Funciones como tipos de datos de primera clase_ (incluido hasta el
      apartado 5.3. _Función apply_)


## Ejercicios


### Ejercicio 1 ###

a) Implementa la función recursiva `(contiene-prefijo prefijo
lista-pal)` que recibe una cadena y una lista de palabras. Devuelve
una lista con los booleanos resultantes de comprobar si la cadena es
prefijo de cada una de las palabras de la lista.

Debes definir una función auxiliar `(es-prefijo? pal1 pal2)` que
compruebe si la palabra 1 es prefijo de la palabra 2.

!!! Hint "Pista"
    Puedes usar la función `(substring palabra inicio final)` que devuelve
    la subcadena de la `palabra` que va desde la posición `inicio` hasta
    la posición `final` (sin incluir).

Ejemplos:

```racket
(es-prefijo? "ante" "anterior") ; ⇒ #t
(contiene-prefijo "ante" '("anterior" "antígona" "antena" "anatema")) 
; ⇒ (#t #f #t #f)
```

b) Vamos a generalizar la solución del ejercicio 5 de la práctica 2 e
implementar la función recursiva `(cadenas-mayores lista1 lista2)`
teniendo en cuenta que las listas que recibe tienen un número
indeterminado de cadenas. En el caso en que una de las listas sea
mayor que la otra, se deberán añadir todas sus cadenas a la lista
resultante.

Ejemplos:

```racket
(cadenas-mayores '("hola" "que" "tal") '("adios")) 
; ⇒ ("adios" "que" "tal")
(cadenas-mayores '("hola" "que" "tal") '("meme" "y" "adios"))
; ⇒ ("hola" "que" "adios")
(cadenas-mayores '("la" "primera" "práctica" "de" "recursión")
                 '("confiar" "en" "la" "recursión" "facilita" "su" "resolución"))
; ⇒ ("confiar" "primera" "práctica" "recursión" "recursión" "su" "resolución")
```

### Ejercicio 2 ###


a) Implementa la función recursiva `(inserta-pos dato pos lista)` que
recibe un dato, una posición y una lista y devuelve la lista
resultante de insertar el dato en la posición indicada de la lista. Si
la posición es 0, el dato se inserta en cabeza. Suponemos que la
posición siempre será positiva y menor o igual que la longitud de la
lista.

Ejemplos:

```racket
(inserta-pos 'b 2 '(a a a a)) ; ⇒ '(a a b a a)
(inserta-pos 'b 0 '(a a a a)) ; ⇒ '(b a a a a)
```

b) Implementa la función recursiva `(inserta-ordenada n
lista-ordenada)` que recibe un número y una lista de números ordenados
de menor a mayor y devuelve la lista resultante de insertar el número
`n` en la posición correcta para que la lista siga estando ordenada.

Ejemplo:

```racket
(inserta-ordenada 10 '(-8 2 3 11 20)) ; ⇒ (-8 2 3 10 11 20)
```

c) Usando la función anterior `inserta-ordenada` implementa la función recursiva
`(ordena lista)` que recibe una lista de números y devuelve una lista
ordenada.

Ejemplo:

```racket
(ordena '(2 -1 100 4 -6)) ; ⇒ (-6 -1 2 4 100)
```

### Ejercicio 3 ###

a) Implementa la función recursiva `(mueve-al-principio lista dato)` que recibe una lista y un 
dato que está contenido en la lista. La función debe devolver la lista resultante de
mover la primera aparición del dato al comienzo de la lista, dejando el resto de la lista
sin modificar. Suponemos que el dato que se pasa como parámetro está contenido en la lista.

Ejemplo:

```racket
(mueve-al-principio '(a b e c d e f) 'e) ; ⇒ (e a b c d e f)
(mueve-al-principio '(a b c d e f g) 'a) ; ⇒ (a b c d e f g)
```

b) Implementa una función recursiva `(comprueba-simbolos lista-simbolos
lista-num)` que recibe una lista de símbolos y una lista de números
enteros (ambas de la misma longitud) y devuelve una lista de
parejas. Cada pareja está formada por el símbolo de la i-ésima
posición de `lista-simbolos` y el número entero situado esa posición
de `lista-num`, siempre y cuando dicho número se corresponda con la
longitud de la cadena correspondiente al símbolo. Puedes utilizar las
funciones predefinidas `string-length` y `symbol->string`.

Ejemplo:

```racket
(comprueba-simbolos '(este es un ejercicio de examen) '(2 1 2 9 1 6))
; ⇒ ((un . 2) (ejercicio . 9) (examen . 6))
```



### Ejercicio 4 ###

Vamos a implementar distintas versiones de funciones que expanden
una lista original. 

En el primer apartado definiremos una función auxiliar que se deberá
usar en todos los demás apartados.

a) Escribe la función recursiva `(expande-pareja pareja)` que recibe
una pareja formada por un dato y un número _n_ y devuelve la lista
formada por _n_ repeticiones del dato.

Ejemplo:

```racket
(expande-pareja '(hola . 3)) ; ⇒ (hola hola hola)
(expande-pareja '(#t . 5)) ; ⇒ (#t #t #t #t #t)
```

b) Vamos a implementar dos versiones de la función `(expande-parejas
pareja_1 ... pareja_n)` que recibe un número variable de
argumentos (todos opcionales) y devuelve una lista donde se han "expandido" las parejas,
creando una lista con tantos elementos como el número que indique cada
pareja. Todos los argumentos son opcionales; si no hay argumentos se
devolverá la lista vacía.

Ejemplo:

```racket
(expande-parejas '(#t . 3) '("LPP" . 2) '(b . 4)) 
; ⇒ (#t #t #t "LPP" "LPP" b b b b)
```

b.1) Escribe una solución en la que la función `expande-parejas`
llame a una función recursiva `(expande-lista lista-parejas)`
que trabaje sobre una lista de parejas.

b.2) Escribe una solución en la que la propia función
`expande-parejas` sea recursiva. Llámala `expande-parejas-2` y ten
cuidado de que la llamada recursiva sea también a la propia
`expande-parejas-2`.

!!! Hint "Pista"
    Repasa el [apartado
    5.3.1](https://domingogallardo.github.io/apuntes-lpp/teoria/tema02-programacion-funcional/tema02-programacion-funcional.html#531-funcion-apply-y-funciones-recursivas)
    de teoría, en el que se explica cómo usar `apply` para implementar funciones
    recursivas con número variable de argumentos.

c) Implementa la función recursiva `(expande lista)`. Recibe una
lista en la que hay intercalados algunos números enteros
positivos. Devuelve la lista original en la que se han expandido los
elementos siguientes a los números, tantas veces como indica el
número. La lista nunca va a contener dos números consecutivos y
siempre va a haber un elemento después de un número.

Debes usar también para su implementación la función `(expande-pareja
pareja)` definida en el apartado a).

Ejemplo:

```racket
(expande '(4 clase ua 3 lpp aulario)) 
; ⇒ (clase clase clase clase ua lpp lpp lpp aulario)
```

En el ejemplo, el 4 indica que el siguiente elemento
(`clase`) se debe repetir 4 veces en la lista expandida y el 3 indica
que el siguiente elemento (`lpp`) se va a repetir 3 veces.


### Ejercicio 5 ###

a) Indica qué devuelven las siguientes expresiones en Scheme. Puede ser
que alguna expresión contenga algún error. Indícalo también en ese
caso y explica qué tipo de error. Hazlo sin el intérprete, y después
comprueba con el intérprete si tu respuesta era correcta.


```racket
((lambda (x) (* x x)) 3) ; ⇒ ?
((lambda () (+ 6 4))) ; ⇒ ?
((lambda (x y) (* x (+ 2 y))) (+ 2 3) 4) ; ⇒ ?
((lambda (x y) (* x (+ 2 x))) 5) ; ⇒ ?


(define f (lambda (a b) (string-append "***" a b "***")))
(define g f)
(procedure? g) ; ⇒ ?
(g "Hola" "Adios") ; ⇒ ?
```

b) Hemos visto en teoría que la forma especial `define` para construir
funciones es _azucar sintáctico_ y que el intérprete de Scheme la
convierte en una expresión equivalente usando la forma especial
`lambda`.

Escribe cuál sería las expresiones equivalentes, usando la forma
especial `lambda` a las siguientes definiciones de funciones:

```racket
(define (suma-3 x)
   (+ x 3))
    
(define (factorial x)
   (if (= x 0)
      1
      (* x (factorial (- x 1)))))
```


c) Suponiendo las siguientes definiciones de funciones indica qué
devolverían las invocaciones. Puede ser que alguna expresión contenga
algún error. Indícalo también en ese caso y explica qué tipo de error.

Hazlo sin el intérprete, y después comprueba con el intérprete si tu
respuesta era correcta.


```racket
(define (doble x)
   (* 2 x))
   
(define (foo f g x y)
   (f (g x) y))

(define (bar f p x y)
   (if (and (p x) (p y))
       (f x y)
       'error))
       
(foo + 10 doble 15) ; ⇒ ?
(foo doble + 10 15) ; ⇒ ?
(foo + doble 10 15) ; ⇒ ?
(foo string-append (lambda (x) (string-append "***" x)) "Hola" "Adios") ; ⇒ ?

(bar doble number? 10 15) ; ⇒ ?
(bar string-append string? "Hola" "Adios") ; ⇒ ?
(bar + number? "Hola" 5) ; ⇒ ?
```

### Ejercicio 6 ###

Vamos a seguir jugando a las cartas con Scheme. Vas a tener que
implementar una serie de funciones auxiliares con las que vas a poder
hacer un truco de cartas al final del ejercicio.

Comienza por volver a descargar el [fichero
`lpp.rkt`](https://raw.githubusercontent.com/domingogallardo/apuntes-lpp/master/src/lpp.rkt). En
él hemos incluido una nueva función `(cartas n)` con las que
puedes generar una lista de _n_ cartas aleatorias de una baraja de hasta
48 cartas. Por ejemplo:

```racket
(cartas 10) ; ⇒ (9♣ 7♠ Q♠ 4♥ 8♠ 3♠ 7♦ A♠ A♥ K♠)
(cartas 5) ; ⇒ (7♣ 3♣ 6♣ 7♠ 5♣)
```

Como máximo puedes poner como parámetro 48 para generar aleatoriamente
las 48 cartas de una baraja francesa sin dieces.

!!! Note "La función `cartas` no cumple el paradigma funcional"
    La función `cartas` es una función que devuelve una lista
    aleatoria de cartas. No cumple el paradigma funcional porque
    devuelve valores distintos cuando se llama con los mismos
    parámetros.

a) Define una función `(coloca tres-listas un dos tres)` que recibe
una listas con tres listas y tres elementos y devuelva el resultado de
colocar los elementos en la cabeza de las tres listas.

Ejemplo:

```racket
(coloca '(() () ()) 'a 'b 'c) ; ⇒ '((a) (b) (c))
(coloca '((a) (a) (a)) 'b 'b 'b) ; ⇒ '((b a) (b a) (b a))
(coloca '((a) (b c) (d e f)) 'g 'h 'i) ; ⇒ '((g a) (h b c) (i d e f)))
```

b) Usando la función anterior como función auxiliar implementa una
función recursiva `(reparte-tres lista-cartas)` que recibe una lista de
cartas con un número de cartas múltiplo de 3 y devuelve el resultado
de repartir esas cartas una a una en tres montones. Las cartas en
las posiciones 0, 3, 6, etc. irán en un montón. Las cartas en las
posiciones 1, 4, 7, etc. irán en el segundo montón. Y las cartas en
las posiciones 2, 5, 8, etc. irán en el tercero.

El resultado será una lista con tres listas representando esos tres
montones de cartas.

Ejemplo:

```racket
(define doce-cartas '(A♣ 2♣ 3♣ 4♣ 5♣ 6♣ 7♣ 8♣ 9♣ J♣ Q♣ K♣))
(reparte-tres doce-cartas) ; ⇒ '((A♣ 4♣ 7♣ J♣) (2♣ 5♣ 8♣ Q♣) (3♣ 6♣ 9♣ K♣))
```

c) Implementa una función recursiva `(elemento-central lista)` que
reciba una lista con un número impar de elementos (mayor o igual que
uno) y devuelva su elemento central.

!!! Note "Pista"
    Supongamos que defines una función recursiva auxiliar
    `(quita-ultimo lista)` que devuelve una lista sin el último
    elemento.
    
    ¿Podrías usar esta función para pasarle un caso más sencillo a la
    llamada recursiva y que sea la llamada recursiva la que devuelva
    el elemento central? 
    

Ejemplo:

```racket
(elemento-central '(a b c d e f g)) ; ⇒ d
```

d) Una vez que has implementado las funciones anteriores ya solo te
queda copiar las siguientes definiciones para poder hacer el truco de
cartas. Son funciones que recomponen la baraja a partir de los tres
montones dependiendo de si la carta elegida está en el montón de la
izquierda, del centro o de la derecha.

Y la función `adivina` es la que devuelve la carta elegida en el truco.

```racket
(define (izquierda tres-listas)
  (append (third tres-listas)
          (first tres-listas)
          (second tres-listas)))

(define (centro tres-listas)
  (append (third tres-listas)
          (second tres-listas)
          (first tres-listas)))

(define (derecha tres-listas)
  (append (second tres-listas)
          (third tres-listas)
          (first tres-listas)))

(define (adivina lista)
  (elemento-central lista))
```

Por último, antes de empezar el truco, un par de consideraciones sobre
los programas con números aleatorios.

La siguiente función, con la constante 90 como argumento, genera
siempre la secuencia aleatoria que permite seguir el ejemplo. Si se
cambia por otra constante, la secuencia también se reperirá siempre
aunque será otra. Tener siempre la misma secuencia aleatoria permite
poder depurar la programación trabajando siempre con el mismo ejemplo
aleatorio.

```racket
(random-seed 90)
```
Si en lugar de una constante se usa un valor variable, se obtiene una
secuencia aleatoria distinta cada vez que se ejecute el programa. 

Ejemplo:

```racket
(random-seed (modulo (current-milliseconds) (expt 2 31)))
```

Y ahora ya podemos empezar el truco de cartas.

1. Repartimos una lista de cartas y las guardamos en la variable
`t1`. Podríamos jugar con 3, 9, 15, 21 o 27 cartas. Vamos a hacerlo
con 27:

    ```racket
    (define t1 (reparte-tres (cartas 27)))
    ```

2. Visualizamos los montones y pedimos al espectador que piense en una
carta sin decirla. Por ejemplo el as de tréboles.

    ```racket
    t1 ; ⇒ ((J♣ 8♦ K♥ J♠ 2♠ 8♥ Q♣ 4♦ A♥) (5♥ 9♣ 5♦ Q♠ A♦ 9♥ 5♠ 9♦ Q♦) (7♣ 3♠ 6♥ 6♣ 7♥ 3♣ 4♣ A♣ J♥))
    ```

3. Preguntamos al espectador en qué montón está la carta
   pensada. Juntamos los montones usando la función correspondiente a
   lugar del montón (`izquierda`, `derecha` o `centro`). En este caso
   el as de tréboles está en el montón derecho, por lo que usamos la
   función `derecha`. Y volvemos a repartir en tres montones el mazo
   resultante. Los guardamos en la variable `t2`:
   
    ```racket
    (define t2 (reparte-tres (derecha t1)))
    ```

4. Visualizamos de nuevo los montones y preguntamos dónde está la
   carta. En este caso se encuentra en el centro.
   
    ```racket
    t2 ; ⇒  ((5♥ Q♠ 5♠ 7♣ 6♣ 4♣ J♣ J♠ Q♣) (9♣ A♦ 9♦ 3♠ 7♥ A♣ 8♦ 2♠ 4♦) (5♦ 9♥ Q♦ 6♥ 3♣ J♥ K♥ 8♥ A♥))
    ```
   
    Juntamos usando la función `centro` y volvemos a repartir,
    guardando el resultado en la variable `t3`:
   
    ```racket
    (define t3 (reparte-tres (centro t2)))
    ```
   
5. Visualizamos los montones:

    ```racket
    t3 ; ⇒  ((5♦ 6♥ K♥ 9♣ 3♠ 8♦ 5♥ 7♣ J♣) (9♥ 3♣ 8♥ A♦ 7♥ 2♠ Q♠ 6♣ J♠) (Q♦ J♥ A♥ 9♦ A♣ 4♦ 5♠ 4♣ Q♣))
    ```
    
    Y preguntamos dónde se encuentra la carta. En este caso el as de
    trébol se encuentra en el montón de la derecha. Volvemos a juntar
    los montones usando entonces la función `derecha` y ya podemos
    llamar a la función `adivina` con la baraja resultante. Esta
    función devolverá mágicamente la carta escogida:
    
    ```racket
    (adivina (derecha t3)) ; ⇒ A♣
    ```



# Práctica 5: Funciones como datos de primera clase y funciones de orden superior

## Antes de la clase de prácticas ##

- Los siguientes ejercicios están basados en los conceptos de teoría vistos en la teoría practica 5:

    - 5.4. Generalización. 
    - 5.5. Funciones que devuelven otras funciones. 
    - 5.6. Funciones en estructuras de datos. 
    - 5.7. Funciones de orden superior.

## Ejercicios

Descarga el [fichero `lpp.rkt`](https://raw.githubusercontent.com/domingogallardo/apuntes-lpp/master/src/lpp.rkt),
pulsando el botón derecho del ratón y seleccionando la opción _Guardar
como_ `lpp.rkt`. Guárdalo en la misma carpeta en la que tengas el
fichero `practica5.rkt`.

El fichero contiene la definición de las funciones de orden superior `exists?` y `for-all?`.

### Ejercicio 1 ###

a) Define la función recursiva `(aplica-veces f1 f2 n x)` que aplica
`n` veces las funciones `f2` y `f1` al número `x`. 

Por ejemplo, `(aplica-veces doble suma-2 3 5)` deberá devolver el
resultado de sumarle 2 a 5 (7), después calcular el doble (14),
después sumarle otra vez 2 al resultado (16), volver a calcular su
doble (32) y, por último, sumarle 2 al resultado (34) y calcular su
doble. Esto es, aplica 3 veces las funciones `suma-2` y `doble`
tomando como número inicial el 5. El resultado será 68.

Ejemplos:

```racket
(aplica-veces (lambda (x) (+ x 1)) (lambda (x) (+ x 2)) 2 10) ; ⇒ 16
(aplica-veces (lambda (x) (* x x)) (lambda (x) (+ x 1)) 4 3) ; ⇒ 7072978201
```

b) Implementa la función recursiva `(mueve-al-principio-condicion pred
lista)` que recibe un predicado y una lista. La función es una
generalización de la función de la práctica anterior y debe devolver
la lista resultante de mover la primera aparición del dato que cumpla
el predicado al comienzo de la lista, dejando el resto de la lista sin
modificar.

A diferencia de la práctica anterior, en la lista puede no haber
ningún elemento que cumpla el predicado. En ese caso se devolverá la
lista original.


Ejemplos:

```racket
(mueve-al-principio-condicion number? '(a b c 1 d 1 e) ; ⇒ (1 a b c d 1 e)
(mueve-al-principio-condicion number? '(1 a b 1 c)) ; ⇒ (1 a b 1 c)
(mueve-al-principio-condicion number? '(a b c d)) ; ⇒ (a b c d)
```

!!! Hint "Pista"
    El hecho de que se permita que no haya ningún elemento que cumpla
    el predicado obliga a cambiar bastante la solución de la práctica
    anterior. 
    
    Fíjate por ejemplo en la función `(inserta-en-segunda-posicion
    dato lista)` de la solución. En el caso en que no haya en la lista
    ningún elemento que cumpla la condición esta función deberá
    **añadir en cabeza** el dato, en lugar de insertarlo en segunda
    posición. De hecho, podríamos cambiar el nombre de la función
    auxiliar y llamarla `inserta-segundo-cond` o algo así.


c) Vamos a generalizar la función de la práctica anterior
`(comprueba-simbolos)` llamándola `(comprueba pred lista1
lista2)` y pasándole como parámetro un predicado de comparación. La
función ahora podrá procesar cualquier tipo de listas (de símbolos, de
cadenas, de listas, etc.). La función pasada como parámetro se encarga
de comparar si el elemento de la primera lista cumple la condición con el
elemento de la segunda.

Implementa la función `(comprueba pred lista1 lista2)`.

Ejemplo:

```racket
(comprueba (lambda (x y)
             (= (string-length (symbol->string x)) y))
           '(este es un ejercicio de examen) 
           '(2 1 2 9 1 6))
; ⇒ ((un . 2) (ejercicio . 9) (examen . 6))

(comprueba (lambda (x y)
              (= (string-length x) (string-length y)))
             '("aui" "a" "ae" "c" "aeiou")
             '("hola" "b" "es" "que" "cinco"))
; ⇒ (("a" . "b") ("ae" . "es") ("aeiou" . "cinco"))
```


### Ejercicio 2 ###

Queremos ordenar de menor a mayor una lista que contenga cualquier
tipo de elemento, no solo números. Para ello vamos a generalizar el
ejercicio 2 de la práctica anterior, añadiendo un parámetro adicional (un predicado),
al que llamaremos `menor-igual?`.

a) Generaliza las funciones `inserta-ordenada` y `ordena` añadiéndoles
este parámetro adicional que es un predicado que
comprueba si un dato de los que componen la lista es menor o igual que
otro. Llama a las funciones resultantes `inserta-ordenada-genérica` y
`ordena-genérica`.

```racket
(ordena-generica '(3 5 1) <=) ;=> (1 3 5)
```

b) Completa las siguientes tres pruebas. En la primera deberás ordenar una lista de
cadenas por su longitud, en la segunda la lista de cadenas por su
orden lexicográfico y en la tercera deberás ordenar una lista de
parejas de números por la suma de su parte izquierda y su parte
derecha:

```racket
(check-equal? (ordena-generica '("Hola" "me" "llamo" "Iñigo" "Montoya") ________ ) '("me" "Hola" "llamo" "Iñigo" "Montoya"))
(check-equal? (ordena-generica '("Hola" "me" "llamo" "Iñigo" "Montoya") ________ ) '("Hola" "Iñigo" "Montoya" "llamo" "me"))
(check-equal? (ordena-generica '((2 . 2) (1 . 1) (3 . 0) (5 . 1)) ________ ) '((1 . 1) (3 . 0) (2 . 2) (5 . 1)))
```

c) Define la función `(ordena-cartas lista-cartas)` que ordene una
lista de cartas de menor a mayor valor usando la función anterior
`ordena-generica`. Deberás incluir la función `valor-carta` y sus
funciones auxiliares definidas en prácticas anteriores.


Ejemplo:

```racket
(ordena-cartas '(Q♠ J♣ 5♣ Q♥ J♦)) ; ⇒ (5♣ J♣ J♦ Q♠ Q♥)
```

### Ejercicio 3 ###

a) Indica qué devuelven las siguientes expresiones, sin utilizar el
intérprete. Comprueba después si has acertado.

```racket
(map (lambda (x)
         (cond 
            ((symbol? x) (symbol->string x))
            ((number? x) (number->string x))
            ((boolean? x) (if x "#t" "#f"))
            (else "desconocido"))) '(1 #t hola #f (1 . 2))) ; ⇒ ?
         
(filter (lambda (x) 
            (equal? (string-ref (symbol->string x) 1) #\a)) 
    '(alicante barcelona madrid almería)) ; ⇒ ?

(foldr (lambda (dato resultado)
          (string-append dato "*" resultado)) "" 
          '("Hola" "que" "tal")) ; ⇒ ?

(foldr append '() '((1 2) (3 4 5) (6 7) (8))) ; ⇒ ?

(foldl (lambda (dato resultado)
         (string-append
          (symbol->string (car dato))
          (symbol->string (cdr dato))
          resultado)) "" '((a . b) (hola . adios) (una . pareja))) ; ⇒ ?

(foldr (lambda (dato resultado)
           (cons (+ (car resultado) dato)
                 (+ (cdr resultado) 1))) '(0 . 0) '(1 1 2 2 3 3)) ; ⇒ ?

(apply + (map cdr '((1 . 3) (2 . 8) (2 . 4)))) ; ⇒ ?

(apply min (map car (filter (lambda (p)
                                  (> (car p) (cdr p))) 
                                  '((3 . 1) (1 . 20) (5 . 2))))) ; ⇒ ?
```

b) Sin utilizar el intérprete DrRacket, rellena los siguientes huecos
para obtener el resultado esperado. Después usa el intérprete para
comprobar si has acertado.


```racket 

; Los siguientes ejercicios utilizan esta definición de lista

(define lista '((2 . 7) (3 . 5) (10 . 4) (5 . 5)))


; Queremos obtener una lista donde cada número es la suma de las
; parejas que son pares

(filter ________
        (________ (lambda (x) (+ (car x)
                                 (cdr x)))
               lista))
; ⇒ (8 14 10)

; Queremos obtener una lista de parejas invertidas donde la "nueva"
; parte izquierda es mayor que la derecha.

(filter ___________
        (map ____________ lista))
; ⇒ ((7 . 2) (5 . 3))

; Queremos obtener una lista cuyos elementos son las partes izquierda
; de aquellas parejas cuya suma sea par.

(foldr __________ '()
        (_________ (lambda (x) (even? (+ (car x) (cdr x)))) lista))
; ⇒ (3 10 5)
```

c) Rellena los siguientes huecos **con una única expresión** en la que
se utilice alguna función previamente definida (`f` o `g`). Comprueba
con el intérprete si lo has hecho correctamente.


```racket
(define (f1 x) (lambda (y z) (string-append y z x)))
(define g1 (f1 "a"))
(check-equal? ____________________ "claselppa")



(define (f2 x) (lambda (y z) (list y x z)))
_____________
(check-equal? (g2 "hola" "clase") (list "hola" "lpp" "clase"))


(define (f3 g3) (lambda(z x) (g3 z x)))
(check-equal? _____________________  '(3 . 4))
```

### Ejercicio 4 ###

a) Implementa utilizando funciones de orden superior la función
`(contar-datos-iguales-fos lista-parejas)` que recibe una lista de
parejas y devuelve el número de parejas que tienen sus dos datos
iguales.

```racket
(contar-datos-iguales-fos 
   '((2 . 3) ("hola" . "hola") (\#a . \#a) (true . false))) 
; ⇒ 2
(contar-datos-iguales-fos 
   '((2 . "hola") ("hola" . 3) (\#a . true) (\#b . false))) 
; ⇒ 0
```

b) Implementa, utilizando funciones de orden superior, la función
`(expande-lista-fos lista-parejas)`, que hace lo mismo que la función
`(expande-lista lista-parejas)` de la práctica anterior. Igual que en
la práctica anterior debes usar la función `expande-pareja`.

```
(expande-lista-fos '((#t . 3) ("LPP" . 2) (b . 4))) 
; ⇒ (#t #t #t "LPP" "LPP" b b b b))
```

c) Implementa, utilizando funciones de orden superior, la función
`(comprueba-simbolos-fos lista-simbolos lista-num)` que hace lo mismo
que la función `comprueba-simbolos` del ejercicio 3b) de la práctica
pasada.

Ejemplo:

```
(comprueba-simbolos-fos '(este es un ejercicio de examen) '(2 1 2 9 1 6))
; ⇒ ((un . 2) (ejercicio . 9) (examen . 6))
```

### Ejercicio 5 ###

a) Implementa usando funciones de orden superior la función `(suma-n-izq n
lista-parejas)` que recibe una lista de parejas y devuelve otra lista
a la que hemos sumado `n` a todas las partes izquierdas.

Ejemplo

```racket
(suma-n-izq 10 '((1 . 3) (0 . 9) (5 . 8) (4 . 1)))
; ⇒ ((11 . 3) (10 . 9) (15 . 8) (14 . 1))
```

b) Completa la definición de la siguiente función de orden superior
`(busca-mayor mayor? lista)` que busca el mayor elemento de una
lista. Recibe un predicado `mayor?` que compara dos elementos de la
lista y devuelve `#t` o `#f` dependiendo de si el primero es mayor que
el segundo. 

Al usar un predicado como argumento, estamos definiendo una función
genérica que podemos usar para obtener el mayor elemento de listas de
números, de cadenas, de parejas, etc. En cada caso deberemos pasar
como parámetro `mayor?` la función de comparación apropiada.

```racket
(define (busca-mayor mayor? lista)
  (foldl __________ (first lista) (rest lista)))
```  


!!! Hint "Pista"
    Fíjate que como elemento base de `foldl` estamos usando el primer
    elemento de la lista y que el plegado lo hacemos sobre el resto de
    la lista.

Escribe algunos `check-equal?` en los que compruebes el funcionamiento
de `busca-mayor`, utilizando funciones `mayor?` distintas.

c) Implementa, usando el predicado de orden superior `for-all?` dos
versiones de la función `(todos-menores? lista n)` que recibe una
lista con sublistas de números y un número `n` y comprueba si todos
los números en las sublistas son menores que `n`.

La primera versión la debes implementar usando `for-all?` y la
función `busca-mayor` definida en el apartado anterior y la segunda
usando `for-all?` y la función de orden superior `exists?`.

Ejemplo:

```racket
(todos-menores? '((10 30 20) (1 50 30) (30 40 90)) 100) ; ⇒ #t
(todos-menores? '((10 30 20) (1 50 30) (30 40 90)) 90) ; ⇒ #f
(todos-menores? '((10 30 20) (1 50 30) (30 40 90)) 55) ; ⇒ #f
```

### Ejercicio 6

Vamos a mejorar el juego de cartas de la semana anterior, usando la baraja
completa y dando más libertad al reparto de cartas en montones, haciendo más
inverosímil todavía la adivinación de la carta elegida.

Usamos la función `(cartas num-cartas)` del fichero `lpp.rkt` y la función
`(reparte-tres lista-cartas)` definida en la práctica anterior.

!!! Important "Usa funciones de orden superior"
    Para la implementación de las siguientes funciones deberás usar, siempre que sea
    posible, funciones de orden superior en lugar de funciones recursivas.

a) Define una nueva versión de la función `coloca` usando número variable de
argumentos. La nueva versión de la función `(coloca ...)` solo tiene como
obligatorio el primer argumento, la lista de n listas. El resto de argumentos es
opcional y puede ir de 0 a n elementos.

Se asume que la lista de n listas debe tener tantas listas como
elementos se pasen como argumentos, y si no se pasa ningún argumento
se devuelve por convenio la lista de n listas tal cual, sin variar.

Ejemplo:

```racket
(coloca '(() () ()) 'a 'b 'c)) ; ⇒ ((a) (b) (c))
(coloca '((a) (a)) 'b 'b)) ; ⇒ ((b a) (b a))
(coloca '((a b c d)) 'e) ; ⇒ ((e a b c d))
(coloca '()) ; ⇒ '()
(coloca '((a) (b c) (d e f) (g h i j)) 'k 'l 'm 'n)) ; ⇒ ((k a) (l b c) (m d e f) (n g h i j))
```

Implementa una función `reparte-cuatro` inspirada en `reparte-tres` y con idéntica estructura.

```racket
(reparte-cuatro '(A♣ 2♣ 3♣ 4♣ 5♣ 6♣ 7♣ 8♣ 9♣ J♣ Q♣ K♣)) ; ⇒ '((A♣ 5♣ 9♣) (2♣ 6♣ J♣) (3♣ 7♣ Q♣) (4♣ 8♣ K♣))
```

b) Implementa la función `(escoge-en-orden lista funcion_ordinal_1
... función_ordinal_n)` que aplica a un primer argumento obligatorio `lista`
la serie de funciones "ordinales" (`first`, `second`, `third` ... `tenth`)
pasadas a continuación de la lista como un número variable de argumentos,
devolviendo la lista de resultados de aplicar esas funciones en el
orden en que se han proporcionado.

```racket
(escoge-en-orden '(1 2 3 4 5)) ; ⇒  '()
(escoge-en-orden '(1 2 3 4 5) fourth second) ; ⇒ (4 2)
(escoge-en-orden '(a b c d) third second fourth first) ; ⇒ (c b d a)
(escoge-en-orden '(dos tres un) third first second) ; ⇒ (un dos tres)
```

Usando las funciones definidas anteriormente, implementa las funciones
`(reordena-tres-montones baraja f-ordinal1 f-ordinal2 f-ordinal3)` y
`(reordena-cuatro-montones baraja f-ordinal1 f-ordinal2 f-ordinal3 f-ordinal4)`
que reparten las cartas de una supuesta baraja (lista de cartas) en tres o
cuatro montones (lista de sublistas de cartas) y después reordena los montones,
o sublistas, según el orden establecido por las funciones "ordinales" pasadas
como argumentos a continuación de la baraja.

```racket
(reordena-tres-montones  '(A♣ 2♣ 3♣ 4♣ 5♣ 6♣ 7♣ 8♣ 9♣ J♣ Q♣ K♣) second first third)
; ⇒
; ((2♣ 5♣ 8♣ Q♣) (A♣ 4♣ 7♣ J♣) (3♣ 6♣ 9♣ K♣))
              
(reordena-cuatro-montones  '(A♣ 2♣ 3♣ 4♣ 5♣ 6♣ 7♣ 8♣ 9♣ J♣ Q♣ K♣) fourth second first third)
; ⇒
; ((4♣ 8♣ K♣) (2♣ 6♣ J♣) (A♣ 5♣ 9♣) (3♣ 7♣ Q♣))
```

c) Implementa la función `(junta-montones montones)` concatena la lista de sublistas
de cartas (montones) en una sola lista de cartas.

```racket
(junta-montones '((4♣ 8♣ K♣) (2♣ 6♣ J♣) (A♣ 5♣ 9♣) (3♣ 7♣ Q♣)))
; ⇒
; (4♣ 8♣ K♣ 2♣ 6♣ J♣ A♣ 5♣ 9♣ 3♣ 7♣ Q♣)
```

d) Una vez que has implementado las funciones anteriores ya solo te
queda copiar la siguiente definición para poder hacer el truco de
cartas. 

La función `(adivina lista-cartas par1 par2 par3)` es la que hace toda la magia
y calcula la posición de la carta escogida a partir de las posiciones de los
montones en los que ésta ha aparecido en tres reparticiones de la baraja.

```racket
(define (adivina baraja par1 par2 par3)
  (list-ref baraja
            (+ (* (- (car par3) 1) (cdr par2) (cdr par1))
               (* (- (car par2) 1) (cdr par1))
               (- (car par1) 1))))
```

Cada pareja codifica en su parte derecha el número de montones en los que se ha
repartido la baraja y en su parte izquierda el montón en el que el espectador ha
visto la carta. Por ejemplo, la pareja `(2 . 4)` representa que la baraja se ha
repartido en 4 montones y que la carta escogida está en el segundo montón.

Lo curioso de la función de adivinación es que funciona correctamente siempre
que se haya repartido la baraja dos veces en cuatro montones y una en tres (las
partes derechas de las tres parejas deben sumar 11).

Veamos un ejemplo de realización del juego, tal y como ya hicimos en la práctica
pasada.

La siguiente función, con la constante 90 como argumento, genera
siempre la secuencia aleatoria que permite seguir el ejemplo. Si se
cambia por otra constante, la secuencia también se reperirá siempre
aunque será otra. Tener siempre la misma secuencia aleatoria permite
poder depurar la programación trabajando siempre con el mismo ejemplo
aleatorio.

```racket
(random-seed 90)
```
Si en lugar de una constante se usa un valor variable, se obtiene una
secuencia aleatoria distinta cada vez que se ejecute el programa. 

Ejemplo:

```racket
(random-seed (modulo (current-milliseconds) (expt 2 31)))
```

1. Repartimos una lista de 48 cartas en cuatro montones. Pedimos a un espectador
   que nos diga en qué orden colocamos los montones, poniendo, por ejemplo,
   primero el primero, después el cuarto, después el segundo y después el tercero:

    ```racket
    (define t1 (reordena-cuatro-montones (cartas 48) first fourth second third))
    ```

2. Visualizamos los montones y pedimos al espectador que piense en una
carta sin decirla. Por ejemplo el as de tréboles. 

    ```racket
    t1 ; ⇒ ((K♦ 3♦ 6♠ 6♦ 3♥ K♣ 8♦ 5♦ 6♣ 8♥ 5♠ A♣)
       ;   (8♠ 8♣ 9♠ 7♠ 2♣ 7♣ K♥ Q♠ 7♥ Q♣ 9♦ J♥)
       ;   (4♠ 2♥ K♠ Q♥ 7♦ J♣ 9♣ 6♥ 2♠ 9♥ 4♣ A♥)
       ;   (5♣ 2♦ J♦ 4♥ A♠ 5♥ 3♠ J♠ A♦ 3♣ 4♦ Q♦))
    ```

3. Preguntamos al espectador en qué montón se encuentra la carta. Anotamos en la
parte izquierda de `p1` el montón en el que está (montón 1), y la parte derecha el
número de montones (4).

    ```racket
    (define p1 '(1 . 4))
    p1
    ```

4. Repetimos la operación con `t2`, pero ahora repartiendo en tres montones nada
más. Podemos pedir a otro espectador que nos diga el orden en el que se
colocan los montones. Por ejemplo, primero el segundo, después el tercero y
después el primero.

    ```racket
    (define t2 (reordena-tres-montones (junta-montones t1) second third first))
    ```

5. Visualizamos `t2` y determinamos la pareja según donde está el as de trébol:

    ```racket
    t2 ; ⇒ ((3♦ 3♥ 5♦ 5♠ 8♣ 2♣ Q♠ 9♦ 2♥ 7♦ 6♥ 4♣ 2♦ A♠ J♠ 4♦)
       ;    (6♠ K♣ 6♣ A♣ 9♠ 7♣ 7♥ J♥ K♠ J♣ 2♠ A♥ J♦ 5♥ A♦ Q♦)
       ;    (K♦ 6♦ 8♦ 8♥ 8♠ 7♠ K♥ Q♣ 4♠ Q♥ 9♣ 9♥ 5♣ 4♥ 3♠ 3♣))
       ;En este caso (2 . 3) (el montón 2 de 3)
    (define p2 '(2 . 3))
    p2
    ```

6. Repetimos una última vez el reparto y ordenación de montones, pero con 4. Hay
que hacer tres repartos, uno de 3 montones y los otros dos de 4, pero no
necesariamente en el orden en el que se ha hecho (4-3-4). Se podía haber hecho
primero el reparto en tres montones, o haberlo dejado para el final. 

    ```racket
    (define t3 (reordena-cuatro-montones (junta-montones t2) fourth second first third))
    ```
    
7. Visualizamos `t3` y definimos la pareja `p3` según el montón del as de trébol: 

    ```racket
    t3 ; ⇒ ((5♠ 9♦ 4♣ 4♦ A♣ J♥ A♥ Q♦ 8♥ Q♣ 9♥ 3♣)
       ;    (5♦ Q♠ 6♥ J♠ 6♣ 7♥ 2♠ A♦ 8♦ K♥ 9♣ 3♠)
       ;    (3♦ 8♣ 2♥ 2♦ 6♠ 9♠ K♠ J♦ K♦ 8♠ 4♠ 5♣)
       ;    (3♥ 2♣ 7♦ A♠ K♣ 7♣ J♣ 5♥ 6♦ 7♠ Q♥ 4♥))
       ;Esta vez es (1 . 4)
    (define p3 '(1 . 4))
    p3
    ```

8. Ya tenemos las tres parejas mágicas que nos adivian la carta:

    ```racket
    (adivina (junta-montones t3) p1 p2 p3) ; ⇒ A♣
    ```

