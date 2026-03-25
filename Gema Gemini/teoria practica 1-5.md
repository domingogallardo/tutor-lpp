# Seminario 1: Seminario de Scheme

## 1. El lenguaje de programación Scheme

Scheme es un lenguaje de programación que surgió en los laboratorios
del MIT en 1975, cuando Guy L. Steele y Gerarld J. Sussman buscaban un
lenguaje con una semántica muy clara y sencilla. 

Scheme es un dialecto de Lisp, es un lenguaje interpretado, muy
expresivo y soporta varios paradigmas. Estuvo influenciado por el
cálculo lambda. El desarrollo de Scheme ha sido lento, ya que la gente
que estandarizó Scheme es muy conservadora en cuanto a añadirle nuevas
características,porque la calidad ha sido siempre más importante que
la utilidad empresarial. Por eso Scheme es considerado como uno de los
lenguajes mejor diseñados de propósito general. Aprender Scheme hará
que seáis mejores programadores cuando utilicéis otros lenguajes de
programación.

### 1.1. El lenguaje de programación Racket ###

¿Qué vamos a aprender? ¿Racket o Scheme? La respuesta es: Scheme
trabajando en Racket. 

[Racket](https://en.wikipedia.org/wiki/Racket_(programming_language))
se diseñó en 1995 basándose en Scheme y ampliándolo con nuevas
funcionalidades, como la posibilidad de extenderlo con librerías. El
lenguaje contiene librerías muy útiles (librerías gráficas, de
conexión a servidores HTTP, de conexión a bases de datos, etc.) con
las que se moderniza el lenguaje original y se convierte en un
lenguaje práctico para desarrollar todo tipo de aplicaciones, desde
videojuegos a servidores web. Sin embargo, nosotros sólo vamos a usar
Racket para aprender la parte que corresponde al núcleo original de
Scheme.

### 1.2. El entorno de programación DrRacket

Veamos una pequeña introducción al entorno de programación que
proporciona DrRacket. Puedes encontrar más información en la
[documentación original](http://docs.racket-lang.org/drracket/index.html).

#### 1.2.1. Descarga de DrRacket ####

DrRacket es multiplataforma y puede ejecutarse en Linux, MacOS o
Windows. Puedes descargarte la última versión en el siguiente enlace:

[Descarga de DrRacket](https://download.racket-lang.org/)


#### 1.2.2. Configuración de DrRacket

Para poder trabajar correctamente con DrRacket debemos asegurarnos que
el lenguaje activo es `The Racket Language` y que la sintaxis de la
salida tiene activada la opción `write`, como aparece en la siguiente
imagen:

<img src="imagenes/output-syntax.png" width="600px" style="border:1px solid black;"/>

Podemos modificar esa opción con los siguientes menús:

_Language > Choose Language (seleccionamos The Racket Language) > Show
details > Output Syntax > write_

Esta opción determina la sintaxis de la salida del intérprete del
lenguaje, que va a ser uno de los elementos fundamentales para
aprender Scheme.

!!! Warning "Aviso" 
    Una vez seleccionadas estas opciones, la configuración se guarda en
    las preferencias del usuario. En los laboratorios de la EPS hay
    que realizar la configuración al comienzo de cada sesión.

Cuando lanzamos DrRacket, vemos que tiene tres partes: una fila de
botones arriba, dos paneles de edición en el medio y una barra de
estado abajo.

<img src="imagenes/racket1.png" width="500px" style="border:1px solid black;"/>

El panel de edición superior es la ventana de definiciones. Se utiliza
para implementar funciones, como la función `cuadrado` en el ejemplo. El
panel inferior, llamado _ventana de interacción_, se utiliza para
evaluar expresiones interactivamente, usando el intérprete de
Racket. Pulsando el botón _Run_, se evalúa el programa de la _ventana
de definiciones_, haciendo que esas definiciones estén disponibles en
la ventana de interacción. Así, dada la definición de `cuadrado`,
después de pulsar _Run_, podemos teclear la expresión `(cuadrado 2)` en
el intérprete, se evaluará y mostrará el resultado, en este caso 4.

DrRacket soporta muchos lenguajes y dialectos de Scheme. Nosotros
vamos a utilizar el lenguaje por defecto, el lenguaje _Racket_. Para
ello no es necesario realizar nada, sólo asegurarnos de lo siguiente:

1. En la parte inferior de la ventana aparece
   "_Determine language from source_"

2. El fichero que se está editando en el panel de edición comienza con la línea:

    ```racket
    #lang racket
    ```

3. Finalmente, si pulsamos el botón _Run_ (Ejecutar) comprobaremos que
   se carga ese lenguaje en el intérprete.

<img src="imagenes/racket3.png" width="500px" style="border:1px solid black;"/>

#### 1.2.3. Cómo escribir en el intérprete ####

En la ventana inferior se encuentra el intérprete de Racket. El
intérprete realiza un bucle en el que se lee una expresión, se evalúa
su resultado y se imprime. A este tipo de bucle se denomina en inglés
REPL (_Read-Evaluate-Print Loop_).

Las expresiones que escribimos en el intérprete se guardan en un
histórico. Podemos recuperar las expresiones anteriores y movernos por
ese histórico usando las siguientes combinaciones de teclas:

- `CTRL` + flecha arriba/abajo

Puede ser que esa combinación de teclas esté asignada a otras
funciones en tu configuración de sistema operativo. Puedes cambiar esa
configuración o usar la combinación alternativa de DrRacket:

- `ESC` + `p` (previous) / `n` (next)

También podemos seleccionar con el cursor una expresión y al pulsar
`RETURN` se copia automáticamente en el _prompt_.

## 2. El lenguaje Scheme

### 2.1. Vamos a empezar probando algunos ejemplos

Scheme es un lenguaje interpretado. Vamos a lanzar DrRacket y teclear
en la ventana de interacción algunas expresiones. El intérprete
analizará la expresión y mostrará el valor resultante de evaluarla.

```racket
2 ; ⇒ 2
(+ 2 3) ; ⇒ 5
(+ (* 2 3) (- 3 1)) ; ⇒ 8
```

Las expresiones en Scheme tienen una forma denominada _notación
prefija de Cambridge_ (el nombre de Cambridge es por la localidad
Cambridge, Massachusets, donde reside el MIT, lugar en el que se ideó
el Lisp), en la que la expresión está delimitada por paréntesis y el
operador va seguido de los operandos. La sintaxis es la siguiente:

```racket
(<función> <arg1> ... <argn>)
```

En Scheme podemos interpretar los paréntesis abiertos ‘(’ como
evaluadores o lanzadores de la función que hay a continuación. La
forma que tiene Scheme de evaluar una expresión es muy sencilla:

1. Evalúa cada uno de los argumentos
2. Aplica la función nombrada tras el paréntesis a los valores
   resultantes de la evaluación anterior

```text
(+ (* 2 3) (- 3 (/ 12 3)))
⇒ (+ 6 (- 3 (/ 12 3)))
⇒ (+ 6 (- 3 4))
⇒ (+ 6 -1)
⇒ 5
```

Existen funciones que admiten un número variable de argumentos, como
la suma o la resta:

```racket
(+) ; ⇒ 0
(+ 2 4 5 6) ; ⇒ 17
(- 10 2 3) ; ⇒ 5
```

En el caso de la resta, los argumentos se van restando de izquierda a
derecha (al primer argumento se le resta el segundo, al resultado se
le resta el tercero, y así sucesivamente):

```racket
(- 4 5 4 8) ; ⇒ -13
(- 4 (+ 5 4) 8) ; ⇒ -13
(- 4 (+ 5 4 8)) ; ⇒ -13
```

En Scheme los términos función y procedimiento significan lo mismo y
se usan de forma intercambiable. Son ejemplos de funciones o
procedimientos: +, -, \, *. En Scheme la evaluación de una función
siempre devuelve un valor, a no ser que se produzca un error que
detiene la evaluación:

```racket
(* (+ 3 4) (/ 3 0))
; Error /: division by zero
```

### 2.2. Definiendo variables y funciones

Scheme es un lenguaje multiparadigma pero principalmente funcional, y
una de sus características principales es que los programas se
construyen mediante la definición de funciones.

Podemos utilizar en el intérprete la forma especial `define` para
definir variables y funciones. En clase de teoría se explica cómo es el
funcionamiento del `define`, pero por el momento lo utilizaremos para
definir variables asociadas a valores, y para implementar funciones.

Podemos definir variables en la ventana de interacción para facilitar
la escritura de expresiones:

```racket
(define a (+ 2 (* 3 4)))
a ; ⇒ 14
(+ a (* 2 3)) ; ⇒ 20
```

Existen identificadores (en Scheme los llamamos _símbolos_) que ya
están definidos en el intérprete de Racket, por ejemplo `pi`:

```
pi ; ⇒ 3.141592653589793
(sin (/ pi 2)) ; ⇒ 1.0
```

Para implementar una función también se utiliza define, con la
siguiente sintaxis:

```racket
(define (<nombre-funcion> <args>)
	<cuerpo-funcion>
)
```

Por ejemplo, vamos a implementar una función que toma dos números como
parámetros y devuelve la suma de sus cuadrados:

```racket
(define (suma-cuadrados x y)
	(+ (* x x) (* y y)))
```

Si llamamos a la función pasando el 2 y el 3 como parámetros, la
función devuelve el número 13:

```racket
(suma-cuadrados 2 3)  ; ⇒ 13
```

!!! Note "Nota"
    A diferencia de la mayoría de lenguajes de programación, en Scheme
    no se utiliza la palabra `return` para indicar que una función
    devuelve un valor. Las funciones se definen con una única
    expresión y el resultado calculado en esa expresión es el que
    siempre se devuelve.


### 2.3. Lenguaje débilmente tipado ###

Vamos a comprobar una característica muy importante de Scheme: ser un
**lenguaje débilmente tipado**. Por esto entendemos, entre otras
cosas, que las variables, funciones y argumentos no tienen un tipo
declarado. Es posible usar valores de distintos tipos de datos para
asignar sucesivamente a una misma variable (en el caso de un lenguaje
imperativo) o para pasar como parámetro a una misma función (en el
caso de un lenguaje funcional). Por ejemplo, JavaScript o PHP son
también lenguajes débilmente tipados imperativos.

Veamos cómo funciona esto en Scheme usando la función anterior como
ejemplo.

```racket
(define (suma-cuadrados x y)
   (+ (* x x) (* y y)))
```

Vemos que los argumentos `x` e `y` no tienen ningún tipo.  Si se
invoca a la función pasando algún dato que no sea un número, el
intérprete no detectará ningún error y permitirá asignar a los
argumentos `x` e `y` esos datos. El error se produce en el momento en
que se intenta evaluar la multiplicación.

Lo podemos comprobar con el siguiente ejemplo, en el que se muestra el
mensaje de error resultante:

```racket
> (suma-cuadrados 10 "hola")
*: contract violation
  expected: number?
  given: "hola"
  argument position: 1st
  other arguments...:
```

Veremos más adelante que hay distintos tipos de números que podemos
operar usando la división, la suma y la multiplicación. La función
definida va a funcionar bien para todos ello. 

Podemos pasar a la función números enteros, números reales o incluso fracciones:

```racket
(suma-cuadrados 2 5) ; ⇒ 29
(suma-cuadrados 2.4 5.8)  ; ⇒ 39.4
(suma-cuadrados (/ 2 3) (/ 3 5))  ; ⇒ 181/225
```

En la última expresión también pueden pasarse directamente los
números fracionales, el intérprete de Scheme entiende esa notación:

```racket
(suma-cuadrados 2/3 3/5) ; ⇒ 181/225
```

### 2.4. Tipos de datos simples

Las primitivas de Scheme consisten en un conjunto de tipos de datos,
formas especiales y funciones incluidas en el lenguaje. A lo largo del
curso iremos introduciendo estas primitivas. 

Vamos a revisar algunos tipos de datos simples de Scheme, así como
algunas funciones primitivas para trabajar con valores de esos tipos.

* Booleanos
* Números
* Caracteres

#### 2.4.1. Booleanos

Un booleano es un valor de verdad, que puede ser verdadero o falso. En
Scheme, tenemos los símbolos `#t` y `#f` para expresar verdadero y falso
respectivamente, pero en muchas operaciones se considera que cualquier
valor distinto de `#f` es verdadero. Ejemplos:

```racket
#t ; verdadero
#f ; falso
(> 3 1.5) ; ⇒ #t
(= 3 3.0) ; ⇒ #t (igualdad matemática)
(equal? 3 3.0) ; ⇒ #f (igualdad de tipo)
(or (< 3 1.5) #t) ; ⇒ #t
(and #t #t #f) ; ⇒ #f
(not #f) ; ⇒ #t
(not 3) ; ⇒ #f (permite cualquier argumento; 
        ;       sólo devuelve #t cuando el argumento es #f)
```

#### 2.4.2. Números

La cantidad de tipos numéricos que soporta Scheme es grande,
incluyendo enteros de diferente precisión, números racionales,
complejos e inexactos. Por ejemplo:

```racket
(/ 1 3) ; ⇒ Devuelve la fracción 1/3
(+ 1/3 1/3) ; ⇒ 2/3
(+ 2 3 4 2) ; ⇒ 11 (la función + admite un número variable de argumentos)
(+ 1/3 0.0) ; número real con infinita precisión ⇒ 0.3333333333333333 
(* (+ 1/3 0.0) 3) ; ⇒ 1
(sqrt -1) ; ⇒ 0+1i (número imaginario)
(+ 3+2i 2-i) ; ⇒ 5+1i (operaciones con números imaginarios)
```

##### 2.4.2.1. Algunas primitivas sobre números

```racket
(<= 2 3 3 4 5) ; ⇒ #t (los argumentos están en orden creciente)
(max 3 5 10 1000) ; ⇒ #1000
(/ 22 4)  ; Devuelve una fracción
(quotient 22 4) ; ⇒ 5 (cociente de la división entera)
(remainder 22 4) ; ⇒ 2 (resto de la división entera)
(equal? 0.5 (/ 1 2)) ; ⇒ #f (distintos tipos de datos)
(= 0.5 (/ 1 2)) ; ⇒ #t (igualdad matemática)
(abs (* 3 -2)) ; ⇒ 6 (valor absoluto)
(sin 2.2) ; relacionados: cos, tan, asin, acos, ata
(expt 4 2) ; ⇒ 16 (exponente: 4 elevado a 2)
```

##### 2.4.2.2. Funciones de redondeo

```racket
; (floor x) devuelve el entero más grande no mayor que x
; (ceiling x) devuelve el entero más pequeño no menor que x
; (truncate x) devuelve el entero más cercano a x cuyo valor absoluto 
;              no es mayor que el valor absoluto de x
; (round x) devuelve el entero más cercano a x, redondeado
(floor -4.3)    ; ⇒ -5.0
(floor 3.5)     ; ⇒ 3.0
(ceiling -4.3)  ; ⇒ -4.0
(ceiling 3.5)   ; ⇒ 4.0
(truncate -4.3) ; ⇒ -4.0
(truncate 3.5)  ; ⇒ 3.0
(round -4.3)    ; ⇒ -4.0
(round 3.5)     ; ⇒ 4.0
```

##### 2.4.2.3. Predicados sobre números

Se denominan _predicados_ a funciones que devuelven un booleano. 

```racket
(positive? -4) ; ⇒ #f (-4 no es positivo)
(negative? -4) ; ⇒ #t (-4 es negativo)
(zero? 0.2) ; ⇒ #f (comprueba si el resultado es cero)
(even? 2) ; ⇒ #t (comprueba si es par)
(odd? 3) ; ⇒ #t (comprueba si es impar)
```

En Scheme tenemos predicados que nos permiten comprobar el tipo de un
parámetro. En el caso de los números, el tipo de número:

```racket
(number? 1) ; ⇒ #t (el argumento 1 es un número)
(integer? 2.3) ; ⇒ #f (el argumento 2.3 no es un entero)
(integer? 4.0) ; ⇒ #t (el número 4.0 matemáticamente es idéntico 
               ;        al número 4)
(real? 1) ; ⇒ #t
```

#### 2.4.3. Caracteres

Se soportan caracteres internacionales y se codifican en UTF-8.

```racket
#\a
#\A
#\space
#\ñ
#\á
```

##### 2.4.3.1. Operaciones sobre caracteres

```racket
(char<? #\a #\b) ; ⇒ #t (el carácter #\a es anterior al #\b)
(char-numeric? #\1) ; ⇒ #t (el carácter #\1 es un número)
(char-alphabetic? #\3) ; ⇒ #f (el carácter #\3 es un número)
(char-whitespace? #\tab) ; ⇒ #t (el carácter tabulador es un espacio
                         ;        en blanco) 
(char-upper-case? #\A) ; ⇒ #t (el carácter #\A es una letra mayúscula)
(char-lower-case? #\a) ; ⇒ #t (el carácter #\a es una letra minúscula)
(char-upcase #\ñ) ; ⇒ #\Ñ (transforma la letra a mayúsculas)
(char-downcase #\A) ; ⇒ #\a (transforma la letra a minúsculas)
(char->integer #\space) ; ⇒ 32 (el carácter espacio ocupa la posición
                        ;        32 en la lista de caracteres)
(integer->char 32) ; ⇒ #\space (igual que antes pero a la inversa)
(char->integer (integer->char 5000)) ; ⇒ 5000 
```

### 2.5. Tipos de datos compuestos

Scheme tiene también un conjunto de tipos de datos compuestos,
que permiten aglutinar elementos simples de los tipos de datos vistos anteriormente.

* Cadenas
* Parejas
* Listas

Estos dos últimos los veremos en detalle en futuras clases de teoría.

#### 2.5.1. Cadenas

Las cadenas son secuencias finitas de caracteres.

```racket
"hola"
"La palabra \"hola\" tiene 4 letras"
```

##### Constructores de cadenas

```racket
(make-string 5 #\o) ; ⇒ "ooooo" (función constructora que recibe un
                    ;            entero y un carácter) 
(string #\h #\o #\l #\a) ; ⇒ "hola" (función constructora que recibe
                         ;           un número variable de caracteres) 
```

##### Operaciones con cadenas

```racket
(substring "Hola que tal" 2 4) ; ⇒ "la" (subcadena que va de la
                               ;      posición 2 a la 4, sin llegar a ella) 
(string? "hola") ; ⇒ #t (predicado que comprueba que el argumento es
                 ;       una cadena) 
(string->list "hola") ; ⇒  (#\h #\o #\l #\a) (devuelve una lista de
                      ;     caracteres) 
(string-length "hola") ; ⇒ 4 (longitud de la cadena)
(string-ref "hola" 0) ; ⇒ #\h (carácter en la posición 0)
(string-append "hola" "adios") ; ⇒ "holaadios" (concatenación de cadenas) 
```

##### Comparadores de cadenas

```racket
(string=? "Hola" "hola") ; ⇒ #f 
(string=? "hola" "hola") ; ⇒ #t 
(string<? "aab" "cde") ; ⇒ #t (se compara usando el orden lexicográfico)
(string>=? "www" "qqq") ; ⇒ #t
```

#### 2.5.2. Parejas

Elemento fundamental de Scheme. Es un tipo compuesto formado por dos
elementos (no necesariamente del mismo tipo).

```racket
(cons 1 2) ; ⇒ (1 . 2) (cons crea una pareja)
(cons #t 3) ; ⇒ (#t . 3) (elementos de tipos diferentes)
(car (cons "hola" 2)) ; ⇒ "hola" (elemento izquierdo de la pareja)
(cdr (cons "bye" 5)) ; ⇒ 5 (elemento derecho de la pareja)
```

Cuando evaluamos las expresiones anteriores en el intérprete, Scheme
muestra el resultado de construir la pareja con la sintaxis:

```text
(elemento izquierdo . elemento derecho)
```

Por ejemplo:

```racket
(cons 1 2) ; ⇒ (1 . 2)
```

La característica de Scheme de que las expresiones se evalúan de
dentro a afuera se aplica a todas las funciones, incluyendo esta
función `cons` que construye parejas:

```racket
(cons (+ 2 3) (string-append "hola" "adios")) ; ⇒ (5 . "holaadios")
(cons (= 2 2.0) (* 2 (+ 1 3))) ; ⇒ (#t . 8)
```

Las parejas pueden contener también otras parejas. Veremos que esta es
la forma de definir estructuras de datos en Scheme:

```racket
(define p1 (cons 1 2)) ; definimos una pareja formada por 1 y 2
(cons p1 3)            ; definimos una pareja formada por la pareja (1 . 2) y 3
                       ; ⇒ ((1 . 2) . 3)
(cons (cons 1 2) 3)    ; igual que la expresión anterior
                       ; ⇒ ((1 . 2) . 3)
```

Hay veces que el trabajo de imprimir una pareja no es tan sencillo
para Scheme. Si la pareja está en la parte derecha de la pareja
principal el intérprete imprime esto, que no se corresponde con lo que
esperamos:

```racket
(cons 1 (cons 2 3)) ; ⇒ (1 2 . 3)
```

Más adelante explicaremos por qué.

#### 2.5.3. Listas

Uno de los elementos fundamentales de Scheme, y de Lisp, son las
listas. Es un tipo compuesto formado por un conjunto finito de
elementos (no necesariamente del mismo tipo). Vamos a ver cómo
definir, crear, recorrer y concatenar listas:

Podemos crear una lista con la función `list`:

```racket
(list 1 2 3 4)     ;list crea una lista
```

Las listas se representan entre paréntesis:

```racket
(list 1 2 3 4) ;  ⇒ (1 2 3 4)
```

La forma más sencilla de trabajar con una lista es usando las
funciones `first` para obtener su primer elemento y `rest` para
obtener el resto de la lista.

```racket
(define l1 (list 1 2 3 4)) ; se crea la lista (1 2 3 4) y se guarda en l1
(first l1)  ; ⇒ 1 (primer elemento de l1)
(rest l1)  ; ⇒ (2 3 4) (resto de la lista, resultado de quitar a la
          ;           lista su primer elemento)
```

Las operaciones sobre listas construyen listas nuevas y no modifican
la lista que se pasa como argumento. En el ejemplo anterior, la lista
`l1` sigue conteniendo la lista original `(1 2 3 4)`.

El `rest` de una lista siempre devuelve otra lista. El `rest` de una
lista de un elemento es la _lista vacía_, que en Scheme se representa
con `()`. 

```racket
(define l2 (list 1 2 3))
(rest l2) ; ⇒ (2 3) 
(rest (rest l2)) ; ⇒ (3) 
(rest (rest (rest l2))) ; ⇒ () lista vacía
null ; ⇒ () lista vacía
```

En Racket se define también el identificador `null` que tiene como
valor la lista vacía:

```racket
null ; ⇒ () lista vacía
```

En Scheme las listas se implementan con parejas. Una lista es, o bien
una lista vacía `()` o bien una pareja cuyo primer elemento es el
primer elemento de la lista y su segundo elemento es el resto de la
lista. Veremos esto con más detalle más adelante.

Dado que una lista se implementa con una pareja, las funciones `car` y
`cdr` también se pueden usar con listas. La función `car` nos devuelve
el primer elemento de la lista y la función `cdr` el resto:

```racket
(define l3 (list 10 20 30 40)) ; 
(car l3)  ; ⇒ 10
(cdr l3)  ; ⇒ (20 30 40)
```

Otra forma de definir una lista es usando el `quote`, una comilla
colocada al comienzo de la lista. Veremos en teoría una explicación
más detallada de cómo funciona este `quote`.

Por ejemplo, podemos definir listas usando las las siguientes
expresiones:

```racket
'(1 2 3) ; ⇒ Construye la lista (1 2 3)
(rest '(1 2 3)) ; ⇒ (2 3)
(define l3 '(1 2 3)) ; Construye la lista (1 2 3) y la guarda en l3
```

Durante el seminario usaremos tanto la función `list` como el `quote`
para construir listas.

La función `list` sin argumentos devuelve una lista vacía y la función
`null?` comprueba si una lista es vacía. La lista vacía también se
puede definir usando `quote`: `'()`. 

Veremos más adelante que la lista vacía es el caso base de gran parte
de funciones recursivas que recorren listas.

```racket
(list) ; ⇒ () 
(null? (list)) ; ⇒ #t
(null? '())    ; ⇒ #t
(null? (list 1 2 3)) ; ⇒ #f
```

También podemos construir una nueva lista añadiendo un elemento a la
cabeza de una lista existente, usando la función `cons` (la misma
función sobre pareja) usando como parámetro un elemento y una lista:

```racket
(cons elemento lista) 
```

Por ejemplo:

```racket
(cons 1 '(2 3 4 5))  ; ⇒ (1 2 3 4 5) (se añade 1 a la cabeza de 
                         ;   la lista (2 3 4 5)
(cons 1 '())  ; ⇒ (1) (se añade 1 a la lista vacía
(cons 1 (cons 2 (list))) ; ⇒ (1 2) 
(cons 1 (cons 2 (cons 3 '()))) ; ⇒ (1 2 3)
```

!!! Danger "Importante"
    Cuando queramos añadir un dato a la cabeza de una lista la
    lista siempre debe ser el **segundo parámetro** de la llamada a la
    función. Si nos equivocamos y pasamos la lista como primer
    parámetro y el dato a añadir como segundo, Scheme no da un
    error sino que construye **una pareja** cuyo primer elemento es
    una lista y su segundo elemento es el dato.
    
    Por ejemplo:
    
    ```racket
    (cons '(1 2 3) 4) ; ⇒ ((1 2 3) . 4)
    ```


También podemos usar la función `append` para concatenar dos o más listas

```racket
(define l3 (list 1))
(define l4 (list 2 3 4))
(define l5 (list 5 6))
(append l3 l4 l5) ; ⇒ (1 2 3 4 5 6)
(append l3 '()) ; ⇒ (1)
(append (list 1 2 3) (list 4)) ; ⇒ (1 2 3 4)
```

!!! Note "Nota"
    Si queremos añadir un dato **al final** de una lista podemos
    hacerlo convirtiéndolo en una lista y usando `append` para
    concatenar la lista resultante al final de la primera:
    
    ```racket
    ;;; Definimos la función cons-al-final
    (define (añade-al-final x lista)
       (append lista (list x)))
    
    ;;; La probamos
    (añade-al-final 10 (list 1 2 3)) ; ⇒ (1 2 3 10)
    ```

Igual que las parejas, las listas pueden contener distintos tipos de
datos:

```racket
(list "hola" "que" "tal") ; ⇒ ("hola" "que" "tal") (lista de cadenas)
(cons "hola" (list #t #\a 3 4))  ; ⇒ ("hola" #t #\a 3 4) lista de distintos
                              ;   tipos de datos)

```

Una lista puede incluso contener otras listas:

```racket
(list (list 1 2) 3 4 (list 5 6)) ; ⇒ ((1 2) 3 4 (5 6)) (lista que contiene listas)
'((1 2) 3 4 (5 6))               ; ⇒ La misma lista, definida con quote
(cons (list 1 2) (list 3 4 5))   ; ⇒ ((1 2) 3 4 5)) (se añade una
                                 ;    lista como primer elemento)
(cons '(1 2) '(3 4 5))           ; ⇒ La misma expresión anterior, con quote
```

La característica de Scheme de que las expresiones se evalúan de
dentro a afuera se aplica a todas las funciones, incluyendo está
función `list` que construye listas:

```racket
(list (+ 1 2) (string-append "hola" "adios") (* 2 3)) ; ⇒ (3 "holaadios" 6)
(list (cons 1 2) (cons 3 4)) ; ⇒ ((1 . 2) (3 . 4)) (lista que contiene parejas)
```

En clase de teoría estudiaremos con más profundidad las listas en
Scheme, cómo están implementadas y cómo se utilizan para crear otras
estructuras de datos más complejas como árboles. Para este seminario
de introducción es suficiente con estas funciones básicas que nos
permiten crear, combinar y obtener elementos de listas.

## 3. Estructuras de control

Como en cualquier lenguaje de programación, las estructuras de control
en Scheme nos permiten seleccionar qué parte de una expresión
evaluamos en función de la evaluación de una expresión
condicional. Las estructuras de control las veremos con más
detenimiento en las clases de teoría, ahora por el momento vamos a ver
ejemplos de funcionamiento.

En Scheme tenemos dos tipos de estructuras de control: `if` y `cond`.

### 3.1. if

Realiza una evaluación condicional de las expresiones que la siguen,
según el resultado de una condición. Una expresión `if` tiene siempre
cuatro elementos: el propio `if`, la condición, la expresión que se
evalúa si la condición es verdadera y la expresión que se evalúa si la
expresión es falsa:

```racket
(if (> 2 3) "2 es mayor que 3" "2 es menor o igual que 3")
```

Al escribir código en Scheme es habitual colocar el `if` y la
condición en una línea y las otras dos expresiones en las siguientes
líneas:

```racket
(if (> 2 3)
    "2 es mayor que 3"
    "2 es menor o igual que 3")
```

En las expresiones que devuelven el valor cuando la condición es
cierta o falsa se puede escribir cualquier expresión de Scheme,
incluido otro `if`:

```racket
(if (> 2 3)
    (if (< 10 5)
        "2 es mayor que 3 y 10 es menor que 5"
        "2 es mayor que 3 y 10 es mayor o igual que 5")
    "2 es menor o igual que 3")
```

Un ejemplo en el que vemos una función que contiene un `if`. La
siguiente función de tres argumentos devuelve la suma de los últimos
si el primero es positivo o la resta en caso contrario:

```racket
(define (suma-si-x-positivo x y z)
    (if (>= x 0)
        (+ y z)
        (- y z)))

(suma-si-x-positivo 2 3 5) ; ⇒ 8
(suma-si-x-positivo -3 3 5) ; ⇒ -2
```

### 3.2. cond

Cuando tenemos un conjunto de alternativas o para evitar usar ifs
anidados.  `cond` evalúa una serie de condiciones y devuelve el valor
de la expresión asociada a la primera condición verdadera.

```racket
(cond
    ((> 3 4) "3 es mayor que 4")
	((< 2 1) "2 es menor que 1")
	((> 3 2) "3 es mayor que 2")
	(else "ninguna condicion es cierta"))
```

## 4. Comentarios

Para comentar una línea de código en la ventana de definiciones, se
escribe el símbolo punto y coma `;` al comienzo de la línea.  Si
queremos comentar más de una línea, podemos utilizar el menú de
DrRacket: seleccionamos las líneas a comentar y pinchamos en la opción
Racket -> comentar con punto y coma.

## 5. Ejemplos completos

### 5.1. Raíz de segundo grado

Vamos a resolver la ecuación de segundo grado en Scheme. Vamos a
implementar el procedimiento `(ecuacion a b c)` que devuelva una
pareja con las dos raíces de la solución. Nos vamos a ayudar de
funciones auxiliares.

Recordamos la fórmula:

<!--<img src="imagenes/ecuacion1.png" width="200px"/>-->

$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}$$

!!! Note "Nota"
    En lugar de definir una función con una expresión muy larga
    compuesta de muchas expresiones anidadas, vamos a implementar la solución de
    forma modular, definiendo **funciones auxiliares**.

Primer definimos la función que define el discriminante:

```racket
(define (discriminante a b c)
	(- (* b b) (* 4 a c)))
```

Después definimos las funciones que devuelven la raíz positiva y la
raíz negativa, usando la función `discriminante` anterior:

```racket
(define (raiz-pos a b c)
	(/ (+ (* b -1) (sqrt (discriminante a b c))) (* 2 a)))

(define (raiz-neg a b c)
	(/ (- (* b -1) (sqrt (discriminante a b c))) (* 2 a)))
```

Por último, definimos la función `ecuacion` que invoca a las funciones
anteriores y devuelve una pareja con los valores resultantes:

```racket
(define (ecuacion a b c)
	(cons (raiz-pos a b c) (raiz-neg a b c)))
```

Lo probamos:

```racket
(ecuacion 1 -5 6)
; ⇒ (3 . 2)
(ecuacion 2 -7 3)
; ⇒ (3 . 1/2)
(ecuacion -1 7 -10)
; ⇒ (2 . 5)
```

### 5.2. Conversión de grados Celsius a Farenheit

Vamos a definir una función llamada `convertir-temperatura` que
permite realizar una conversión de grados Fahrenheit a Centígrados o
vicerversa.

La función toma dos argumentos, el primero será un número que
representa los grados y el segundo será un carácter (`F` o `C`) que
indica la unidad de medida en la que están expresados los grados.

Las fórmulas de conversión son las siguientes:

<!-- <img src="imagenes/ecuacion2.png" width="200px"/>-->

$$C = (F - 32) * 5/9$$

$$F = (C * 9/5) + 32$$

Primero definimos unas funciones auxiliares que calculan las
expresiones anteriores:

```racket
(define (a-grados-fahrenheit grados-centigrados)
  (+ (* (/ 9 5) grados-centigrados) 32))

(define (a-grados-centigrados grados-fahrenheit)
  (* (/ 5 9) (- grados-fahrenheit 32)))
```

Y ahora ya podemos definir la función principal:

```racket
(define (convertir-temperatura grados tipo)
  (cond ((equal? tipo #\F) 
         (list (a-grados-centigrados grados) "grados centigrados"))
        ((equal? tipo #\C) 
         (list (a-grados-fahrenheit grados) "grados fahrenheit"))
        (else "tipo de cambio incorrecto")))
```

Por ejemplo:

```racket
(convertir-temperatura 50 #\F) ; ⇒ (10 "grados centigrados")
(convertir-temperatura 50 #\C) ; ⇒ (122 "grados fahrenheit")
```

## 6. Pruebas unitarias en Scheme

Para verificar que las funciones que definimos tienen un
funcionamiento correcto, es decir, _"hacen lo que tienen que hacer"_,
podemos diseñar distintos casos de prueba. Cada **caso de prueba** se
caracteriza por unos datos de entrada de la función y por el resultado
que esperamos que devuelva dicha función con esos valores de entrada.

Por ejemplo, en las pruebas de la función _convertir-temperatura_,
hemos diseñado dos casos de prueba:

| Datos de Entrada |  Resultado Esperado |
| :---------------:| :------------------ |
|   50 ,     #\F   | (10 "grados centigrados") |
|   50 ,     #\C   | (122 "grados fahrenheit") |


El resultado esperado a partir de unos valores concretos de entrada,
se determina entendiendo **qué** debe hacer la función. Es decir, se
obtiene a partir de la especificación del problema, antes de
plantearnos **cómo** solucionarlo.

Os aconsejamos tener siempre presente la siguiente idea aunque resulte
obvia:

> Para implementar una función, primero es **imprescindible** entender
> **qué debe hacer la función**. Después, seremos capaces de diseñar
> casos de prueba y ocuparnos de **cómo implementarla**.


En las prácticas de la asignatura, para realizar pruebas usaremos la
librería [**RackUnit**](https://docs.racket-lang.org/rackunit/). 

Para ello, lo primero que tendremos que hacer es importar esta nueva
librería. Por tanto, debemos añadir en nuestros ficheros de prácticas
lo siguiente:

```racket
#lang racket
(require rackunit)
```

Una vez importada la librería, ya podemos hacer uso de algunas de sus
funciones. En concreto, utilizaremos las siguientes:

- **check-true**

```racket
(check-true expr)   
;; Comprueba si su argumento es #t.
;; En caso contrario, se imprime un mensaje de error.
```

- **check-false**

```racket
(check-false expr)   
;; Comprueba si su argumento es #f.
;; En caso contrario, se imprime un mensaje de error.
```

- **check-equal?**

```racket
(check-equal? resultado-real resultado-esperado)   
;; Comprueba si sus dos argumentos son iguales.
;; En caso contrario, se imprime un mensaje de error.
```

Con las funciones _check-true_ y _check-false_ validaremos predicados
(recuerda que en Scheme son funciones que devuelven un valor booleano)
que hayamos implementado, comprobando si el resultado esperado es
_true_ o _false_, respectivamente.

Con la función _check-equal?_ podremos validar si el resultado de la
invocación a la función con unos determinados valores de entrada,
representado por el argumento _resultado-real_, es igual al resultado
que esperamos, dado por el argumento _resultado-esperado_.


### 6.1. Ejemplo de pruebas de la función `ecuacion` definida anteriormente

Supongamos la función completa `ecuacion`, con pruebas incluidas:

```racket
#lang racket
(require rackunit)

(define (discriminante a b c)
	(- (* b b) (* 4 a c)))

(define (raiz-pos a b c)
	(/ (+ (* b -1) (sqrt (discriminante a b c))) (* 2 a)))

(define (raiz-neg a b c)
	(/ (- (* b -1) (sqrt (discriminante a b c))) (* 2 a)))

(define (ecuacion a b c)
	(cons (raiz-pos a b c) (raiz-neg a b c)))

(check-equal? (ecuacion 1 -5 6) '(3 . 2))
(check-equal? (ecuacion 2 -7 3) '(3 . 1/2))
(check-equal? (ecuacion -1 7 -10) '(2 . 5))
```

Las pruebas anteriores no mostrarán ningún mensaje de error, lo que
significa que nuestra función _ecuacion_ es 'CORRECTA' para estas
pruebas, es decir, que con los valores de entrada utilizados, su
resultado se corresponde con el esperado.

Ahora vamos a suponer que nos hemos equivocado en la definición de la
función _ecuacion_, por ejemplo en el orden de los argumentos al
invocar a la función auxiliar _raiz-pos_, en la llamada que se hace en
la parte izquierda de la pareja resultante.

```racket
(define (ecuacion a b c)
	(cons (raiz-pos b a c) (raiz-neg a b c)))
```

Con esta nueva definición, cuando ejecutemos el programa (pulsando el
botón Run) aparecerá el siguiente mensaje:

```text
--------------------
FAILURE
actual:     (-1 . 2)
expected:   (3 . 2)
name:       check-equal?
location:   (#<path:/.../filename.rkt>)
expression: (check-equal? (ecuacion 1 -5 6) (cons 3 2))
--------------------
```

Esta prueba muestra un mensaje de error, lo que significa que la nueva
definición de _ecuacion_ 'FALLA', es decir, que el resultado que
devuelve _(-1 . 2)_ no coincide con el resultado esperado _(3 . 2)_.


## 7. Bibliografía

Este **seminario** está basado en los siguientes materiales. Os
recomendamos que les echéis un vistazo y, si os interesa y os queda
tiempo, que exploréis también en los enlaces que hemos dejado en los
apuntes para ampliar información.

- [The Racket Guide](https://docs.racket-lang.org/guide/)
- [The Racket Reference](https://docs.racket-lang.org/reference/)
- [Simply Scheme](http://www.eecs.berkeley.edu/~bh/ss-toc2.html)

# Teoría práctica 2

### Veremos hoy

1. El paradigma de Programación Funcional
    - 1.1 Pasado y presente del paradigma funcional
    - 1.2. Programación declarativa vs. imperativa
    - 1.3. Evaluación de expresiones
    - 1.4. Modelo de computación de sustitución
2. Scheme como lenguaje de programación funcional
    - 2.1. Funciones y formas especiales
    - 2.2. Formas especiales en Scheme: define, if, cond
    - 2.3. Forma especial quote y símbolos
    - 2.4. Listas
---

<p style="margin-bottom:2cm;"></p>

### Definición de programación funcional

!!! Note "Un programa funcional es"
    Un conjunto de funciones matemáticas que convierten
    unas entradas en unas salidas, sin ningún estado interno y ningún
    efecto lateral.

- Es posible utilizar este paradigma en muchos lenguajes de
  programación, aunque no sean estrictamente funcionales.


<p style="margin-bottom:2cm;"></p>

### Principales características del paradigma funcional ###

- Definiciones de funciones matemáticas puras, sin estado interno ni
  efectos laterales
- Valores inmutables
- Uso profuso de la recursión en la definición de las funciones
- Uso de listas como estructuras de datos fundamentales
- Funciones como tipos de datos primitivos: expresiones lambda y
  funciones de orden superior

<p style="margin-bottom:2cm;"></p>

### Lenguajes de programación funcional

Lenguajes modernos principalmente funcionales:

- [Clojure](https://en.wikipedia.org/wiki/Clojure)
- [Erlang](https://en.wikipedia.org/wiki/Erlang_(programming_language))

Lenguajes multi-paradigma en los que se puede usar POO y PF:

- [Ruby](https://en.wikipedia.org/wiki/Ruby_(programming_language))
- [Python](https://en.wikipedia.org/wiki/Python_(programming_language))
- [Groovy](https://en.wikipedia.org/wiki/Groovy_(programming_language))
- [Scala](https://en.wikipedia.org/wiki/Scala_(programming_language))
- [Swift](https://en.wikipedia.org/wiki/Swift_(programming_language))

Lenguaje funcional puro más importante:

- [Haskell](https://en.wikipedia.org/wiki/Haskell_(programming_language))


<p style="margin-bottom:2cm;"></p>

### Aplicaciones prácticas de la programación funcional

- Paradigma muy popular en la actualidad
- Algunos artículos y charlas:
    - Lupo Montero - [Introducción a la programación funcional en JavaScript](https://medium.com/laboratoria-how-to/introducción-a-la-programación-funcional-en-javascript-parte-1-e0b1d0b2142e) (Blog)
    - Andrés Marzal - [Por qué deberías aprender programación funcional ya mismo](https://www.youtube.com/watch?v=jG4QuREv5fE) (Charla en YouTube)
    - Mary Rose Cook - [A practical introduction to functional programming](https://maryrosecook.com/blog/post/a-practical-introduction-to-functional-programming) (Blog)
    - Ben Christensen - [Functional Reactive Programming in the Netflix API](https://www.infoq.com/presentations/Netflix-API-rxjava-hystrix) (Charla en InfoQ)

- El paradigma funcional facilita:
    - la programación de sistemas concurrentes, con múltiples hilos de
      ejecución o con múltiples computadores ejecutando procesos
      conectados concurrentes.
    - la definición y composición de múltiples operaciones sobre
      *streams* de forma muy concisa y compacta, aplicable a la
      programación de sistemas distribuidos en Internet.
    - la programación interactiva y evolutiva.


<p style="margin-bottom:2cm;"></p>

### Evaluación de expresiones y definición de funciones

- En la asignatura usaremos Scheme como primer lenguaje en el que
  exploraremos la programación funcional.

- En el seminario de Scheme que se imparte en prácticas se estudiará
  en más profundidad los conceptos más importantes del lenguaje: tipos
  de datos, operadores, estructuras de control, intérprete, etc.

- Vamos a empezar a ver ejemplo concretos de programación funcional
  viendo cómo se evalúan expresiones y cómo se definen funciones en Scheme.

<p style="margin-bottom:2cm;"></p>

### Evaluación de expresiones

```racket
2 ⇒ 2
(+ 2 3) ⇒ 5
(+) ⇒ 0
(+ 2 4 5 6) ⇒ 17
(+ (* 2 3) (- 3 1)) ⇒ 8
```

Se dice "**evaluar una expresión**" en lugar de "**ejecutar una expresión**".

Partes de una expresión:

- Operador
- Operandos
- Evaluación de dentro a fuera

Por ejemplo, ¿cuál es la evaluación de la siguiente expresión?:

```racket
(+ (* 2 3) (- 3 (/ 12 3)))
```

<p style="margin-bottom:3cm;"></p>

### Definición de funciones

Definición

```racket
(define (cuadrado x)
   (* x x))
```

Uso y evaluación:

```racket
(cuadrado 10) ⇒ 100
(cuadrado (+ 10 (cuadrado (+ 2 4)))) ⇒ 2116
```

<p style="margin-bottom:2cm;"></p>

### Definición de funciones auxiliares

- Lo habitual en programación funcional es definir funciones muy
pequeñas e ir construyendo funciones cada vez de mayor nivel usando
las anteriores.

- No demasiado bien:

```racket
(define (suma-cuadrados x y)
   (+ (* x x) (* y y)))
```

- Mucho más correcto:

```racket
(define (cuadrado x)
   (* x x))

(define (suma-cuadrados x y)
   (+ (cuadrado x) (cuadrado y)))
```

<p style="margin-bottom:2cm;"></p>

### Funciones puras

- No modifican los parámetros que se les pasa
- Devuelven un único resultado
- No tienen estado local ni el resultado depende de un estado exterior mutable

<p style="margin-bottom:2cm;"></p>

### Composición de funciones

- Una idea fundamental de la programación funcional es la composición de
funciones que transforman unos datos de entrada en otros de salida. 
- Ejemplo: procesamiento de imágenes en vehículos autónomos:

<img src="imagenes/composicion-funciones.png" width="700px"/>

- En un lenguaje de programación funcional como Scheme (cuidado: la evaluación
  se hace de dentro a afuera):

```racket
(define (conduce-vehiculo imagenes)
    (obten-acciones 
        (reconoce 
            (filtra 
                (obten-caracteristicas imagenes)))))
```


<p style="margin-bottom:2cm;"></p>

### Programación declarativa

- La PF es un estilo de **programación declarativa**, frente a la
  programación tradicional imperativa.
- Frente a programación imperativa, basada en pasos de ejecución y
  cambio de estado de variables, la programación declarativa es un
  estilo de programación matemático.
- Se **declaran** valores y objetivos o características de los
  elementos de programa.
- La ejecución del programa es "instantánea", sin que haya que
  considerar los pasos de ejecución.
- Ejemplo: hoja de cálculo.
- La programación funcional es un ejemplo de programación declarativa:
  se declaran funciones y se evalúan matemáticamente expresiones.
- La programación lógica (Prolog) es otro ejemplo de programación declarativa.

Otro ejemplo de programación declarativa: SwiftUI.

<img src="imagenes/swiftui.png" width="700px"/>


- Como hemos visto, en programación funcional **declaramos funciones**
que transforman datos de entrada en datos de salida.

```racket
(define (cuadrado x)
   (* x x))
```

- La llamada a la función con el parámetro 4 devuelve 16:

```racket
(cuadrado 4) ; devuelve 16
```

<p style="margin-bottom:2cm;"></p>

### Programación imperativa

- Lenguajes tradicionales (C, C++, Java, Python, etc.)

Características:

- Pasos de ejecución
- Mutación
- Efectos laterales
- Estado local mutable en las funciones


<p style="margin-bottom:2cm;"></p>

#### Pasos de ejecución

Pasos de ejecución en C:

```c
int a = cuadrado(8);
int b = doble(a);
int c = cuadrado(b);
return c
```

En Swift:

```swift
filtrados = filtra(pedidos);
procesados = procesa(filtrados);
return procesados;
```

En programación funcional, en lugar de pasos de ejecución se utiliza
como hemos visto la composición de funciones. Los ejemplos anteriores
se expresan de la siguiente forma en programación funcional:

```racket
(cuadrado (doble (cuadrado 8)))
```

```racket
(procesa (filtra pedidos))
```


<p style="margin-bottom:2cm;"></p>

#### Mutación 

Asignación destructiva o mutación:

```java
int x = 10;
int x = x + 1;
```

En programación funcional los valores definidos son inmutables:

```racket
#lang racket

(define a 12)
(define a 200)
```

tendremos el siguiente error:

```text
module: identifier already defined in: a
```

En lenguajes imperativos también hay sentencias declarativas:

```text
1. int x = 1;   // declarativa
2. x = x+1;     // imperativa
3. int y = x+1; // declarativa
4. y = x;       // imperativa
```

<p style="margin-bottom:2cm;"></p>

#### Mutación y efectos laterales

- Referencias + mutación = efectos laterales (_side effect_ en inglés)

Ejemplo de mutación:

```java
Point2D p1 = new Point2D(3.0, 2.0); // la coord x de p1 es 3.0
p1.getCoordX(); // la coord x de p1 es 3.0
p1.setCoordX(10.0);
p1.getCoordX(); // la coord x de p1 es 10.0
```

Ejemplo de efecto lateral:

```java
Point2D p1 = new Point2D(3.0, 2.0); // la coord x de p1 es 3.0
p1.getCoordX(); // la coord x de p1 es 3.0
Point2D p2 = p1;
p2.setCoordX(10.0);
p1.getCoordX(); // la coord x de p1 es 10.0, sin que ninguna sentencia haya modificado directamente p1
```

- Los efectos laterales permiten definir estructuras de datos más
  eficientes, pero también generan _bugs_ complicados de
  depurar. Sobre todo cuando se están programando sistemas
  concurrentes con múltiples hilos de ejecución.


<p style="margin-bottom:2cm;"></p>

#### Estado local mutable

Función con estado local mutable en lenguaje imperativo (Java):


```java
public class Contador {
   	int c;
    
    public Contador(int valorInicial) {
        c = valorInicial;
    }
    
    public int valor() {
        c++;
        return c;
    }
}

Contador cont = new Contador(10);
cont.valor(); // 11
cont.valor(); // 12
cont.valor(); // 13
```

En C:

```c
int function contador () {
    static int c = 0;
	
	c++;
	return c;
}
	
contador() ;; 1
contador() ;; 2
contador() ;; 3
```	

**Por el contrario**, los lenguajes funcionales puros tienen la propiedad
de *transparencia referencial*: si se sustituye una expresión por su valor el resultado final no debe cambiar. -> funciones no modifican estado.

<p style="margin-bottom:2cm;"></p>

### Resumen

**Características de la programación declarativa**

* Variable = nombre dado a un valor (declaración)
* No existe asignación ni cambio de estado
* No existe mutación, se cumple la *transferencia referencial*: dentro
  de un mismo ámbito todas las ocurrencias de una variable y las
  llamadas a funciones devuelven el mismo valor

**Características de la programación imperativa**

* Variable = nombre de una zona de memoria
* Asignación
* Referencias
* Pasos de ejecución


<p style="margin-bottom:2cm;"></p>

### Modelo de computación de sustitución

- El **modelo de sustitución** es un modelo muy sencillo que permite
definir la semántica de la evaluación de expresiones en lenguajes
funcionales como Scheme. 

- Basado en la reescritura de unos términos por otros

!!! Note "Reglas del modelo de sustitución"
    1. Si *e* es un valor primitivo (por ejemplo, un número), devolvemos ese
       mismo valor.
    2. Si *e* es un identificador, devolvemos su valor asociado con un
       `define` (se lanzará un error si no existe ese valor).
    3. Si *e* es una expresión del tipo *(f arg1 ... argn)*, donde *f* es
       el nombre de una función primitiva (`+`, `-`, ...), evaluamos uno a
       uno los argumentos *arg1* ... *argn* (con estas mismas reglas) y
       evaluamos la función primitiva con los resultados.
   
La regla 4 tiene dos variantes, dependiendo del orden de
evaluación que utilizamos.

!!! Note "Orden aplicativo"
    4. Si *e* es una expresión del tipo *(f arg1 ... argn)*, donde *f*
       es el nombre de una función definida con un `define`, tenemos
       que evaluar primero los argumentos _arg1_ ... _argn_ y después
       **sustituir _f_ por su cuerpo**, reemplazando cada parámetro
       formal de la función por el correspondiente **argumento
       evaluado**. Después evaluaremos la expresión resultante usando
       estas mismas reglas.

!!! Note "Orden normal"
    4. Si *e* es una expresión del tipo *(f arg1 ... argn)*, donde *f*
       es el nombre de una función definida con un `define`, tenemos
       que **sustituir _f_ por su cuerpo**, reemplazando cada
       parámetro formal de la función por el correspondiente
       **argumento sin evaluar**. Después evaluar la expresión
       resultante usando estas mismas reglas.

- Ambas formas de evaluación darán el mismo resultado en programación
funcional. Scheme utiliza el orden aplicativo.

- En el orden aplicativo se realizan las evaluaciones antes de realizar
las sustituciones, lo que define una evaluación de *dentro a fuera* de
los paréntesis. Cuando se llega a una expresión primitiva se
evalúa.

- En el orden normal se realizan todas las sustituciones hasta que se
tiene una larga expresión formada por expresiones primitivas; se
evalúa entonces.

- Comprobamos las sustituciones en cada tipo de orden.

```racket
(define (doble x) 
    (+ x x))
    
(define (cuadrado y) 
    (* y y))

(define a 2)

(doble (cuadrado a))
```


Orden aplicativo:

```text
(doble (cuadrado a)) ⇒       ; Sustituimos a por su valor (R2)
(doble (cuadrado 2)) ⇒       ; Sustitumos cuadrado por su cuerpo (R4)
(doble (* 2 2)) ⇒            ; Evaluamos (* 2 2) (R3)
(doble 4) ⇒                  ; Sustituimos doble por su cuerpo (R4)
(+ 4 4) ⇒                    ; Evaluamos (+ 4 4) (R3)
8
```


Orden normal:

```text
(doble (cuadrado a)) ⇒            ; Sustituimos doble por su cuerpo (R4)
(+ (cuadrado a) (cuadrado a) ⇒    ; Sustituimos cuadrado por su cuerpo (R4)
(+ (* a a) (* a a)  ⇒             ; Sustitumos a por su valor (R2)
(+ (* 2 2) (* 2 2)  ⇒             ; Evaluamos (* 2 2) (R3)
(+ 4 (* 2 2))  ⇒                  ; Evaluamos (* 2 2) (R3)
(+ 4 4)  ⇒                        ; Evaluamos (+ 4 4) (R3)
8
```

- Scheme utiliza orden aplicativo.
- Repasar un ejemplo algo más complicado en los apuntes.
- El resultado es el mismo, siempre que no se definan funciones no puras.

Ejemplo de resultado distinto con funciones no puras:

```racket
(define (zero x) (- x x))
(zero (random 10))
```

<p style="margin-bottom:2cm;"></p>

### Funciones y formas especiales en Scheme 

- Primitivas de Scheme: funciones y formas especiales
- Las funciones se evalúan con el modelo de evaluación visto. 
- Las *formas especiales* son expresiones primitivas de Scheme que
tienen una forma de evaluarse propia, distinta de las funciones.


<p style="margin-bottom:2cm;"></p>

### Forma especial `define`

**Sintaxis**

```racket
(define <identificador> <expresión>)
```

**Evaluación**

1. Evaluar *expresión*
2. Asociar el valor resultante con el *identificador*

**Ejemplo**

```racket
(define base 10)   ; Asociamos a 'base' el valor 10
(define altura 12) ; Asociamos a 'altura' el valor 12
(define area (/ (* base altura) 2)) ; Asociamos a 'area' el valor 60
```

<p style="margin-bottom:2cm;"></p>

### Forma especial `define` para definir funciones

**Sintaxis**

```text
(define (<nombre-funcion> <argumentos>)
	<cuerpo>)
```

**Evaluación**

1. Crear la función con el *cuerpo*
2. Dar a la función el nombre *nombre-función*

**Ejemplo**

```racket
(define (factorial x)
    (if (= x 0)
        1
        (* x (factorial (- x 1)))))
```


<p style="margin-bottom:2cm;"></p>

### Forma especial `if`

**Sintaxis**

```racket
(if <condición> <expresión-true> <expresión-false>)
```

**Evaluación**

1. Evaluar *condición*
2. Si el resultado es `#t` evaluar la *expresión-true*, en otro
   caso, evaluar la *expresión-false*

**Ejemplo**

```racket
(if (> 10 5) (substring "Hola qué tal" (+ 1 1) 4) (/ 12 0))

;; Evaluamos (> 10 5). Como el resultado es #t, evaluamos 
;; (substring "Hola qué tal" (+ 1 1) 4), que devuelve "la"

```

<p style="margin-bottom:2cm;"></p>

### Forma especial `cond`

**Sintaxis**

```racket
(cond 
	(<exp-cond-1> <exp-consec-1>)
	(<exp-cond-2> <exp-consec-2>)
	...
	(else <exp-consec-else>))
```

**Evaluación**

1. Se evalúan de forma ordenada todas las expresiones hasta que una de
   ellas devuelva `#t`
2. Si alguna expresión devuelve `#t`, se devuelve el valor del
   consecuente de esa expresión
3. Si ninguna expresión es cierta, se devuelve el valor resultante de
   evaluar el consecuente del `else`


**Ejemplo**

```racket
(cond
   ((> 3 4) "3 es mayor que 4")
   ((< 2 1) "2 es menor que 1")
   ((= 3 1) "3 es igual que 1")
   ((> 3 5) "3 es mayor que 2")
   (else "ninguna condición es cierta"))

;; Se evalúan una a una las expresiones (> 3 4),
;; (< 2 1), (= 3 1) y (> 3 5). Como ninguna de ella
;; es cierta se devuelve la cadena "ninguna condición es cierta"
```

<p style="margin-bottom:2cm;"></p>

### Forma especial `quote` y símbolos

**Sintaxis**

```racket
(quote <identificador>)
```

**Evaluación**

- Se devuelve el identificador sin evaluar (un símbolo). 
- Se abrevia en con el carácter `'`.

**Ejemplo**

```racket
(quote x) ; el símbolo x
'hola ; el símbolo hola
```

- En Scheme los *identificadores* (nombres que se les da a las
variables) son datos del lenguaje de tipo **symbol**. 

- Los símbolos son distintos de las cadenas. Una cadena es un tipo de
dato compuesto formado por caracteres que podemos concatenar, dividir
en subcadenas, etc. Nada de esto lo podemos hacer con un símbolo. Un
símbolo es un tipo atómico, es sólo un identificador.

Ejemplos de funciones Scheme con símbolos:

```racket
(define x 12)
(symbol? 'x) ; ⇒ #t
(symbol? x) ; ⇒ #f ¿Por qué?
(symbol? 'hola-que<>)
(symbol->string 'hola-que<>)
'mañana
'lápiz ; aunque sea posible, no vamos a usar acentos en los símbolos
; pero sí en los comentarios
(symbol? "hola") ; #f
(symbol?  #f) ; #f
(symbol? (first '(hola cómo estás))) ; #t
(equal? 'hola 'hola)
(equal? 'hola "hola")
```

Un símbolo es un identificador que puede asociarse o ligarse (*bind*)
a un valor (cualquier dato *de primera clase*).

Cuando escribimos un símbolo en el prompt de Scheme el intérprete lo
evalúa y devuelve su valor:

```racket
(define pi 3.14159)
pi
⇒3.14159
```

Los nombres de las funciones (`equal?, `sin, `+, ...) son también
símbolos (los de las macros no) y Scheme también los evalúa (en un par
de semanas hablaremos de las funciones como objetos primitivos en
Scheme):

```racket
sin
⇒ #<procedure:sin>
+
⇒ #<procedure:+>
(define (cuadrado x) (* x x))
⇒ #<procedure:cuadrado>
```

<p style="margin-bottom:2cm;"></p>

### Símbolos como tipos primitivos

Los símbolos son tipos primitivos del lenguaje: pueden pasarse como
parámetros o ligarse a variables.

```racket
(define x 'hola)
x
⇒ hola
```

<p style="margin-bottom:2cm;"></p>

### Forma especial `quote` y expresiones

**Sintaxis**

```racket
(quote <expresión>)
```

**Evaluación**

Si `quote` recibe una expresión correcta de Scheme (una expresión
entre paréntesis) se devuelve la lista o pareja definida por la
expresión (sin evaluar sus elementos).

**Ejemplos**

```racket
'(1 2 3) ; ⇒ (1 2 3) Una lista
'(+ 1 2 3 4) ; La lista formada por el símbolo + y los números 1 2 3 4
(quote (1 2 3 4)) ; La lista formada por los números 1 2 3 4
'(a b c) ; ⇒ La lista con los símbolos a, b, y c
'(* (+ 1 (+ 2 3)) 5) ; Una lista con 3 elementos, el segundo de ellos otra lista
'(1 . 2) ; ⇒ La pareja (1 . 2)
'((1 . 2) (2 . 3)) ; ⇒ Una lista con las parejas (1 . 2) y (2 . 3)
```

<p style="margin-bottom:2cm;"></p>


### Función `eval` ###

Una vez vista la forma especial `quote` podemos explicar la función
`eval`. La función `eval` es una instrucción muy curiosa de los
lenguajes funcionales. Permite invocar al intérprete en tiempo de
ejecución y hacer que éste evalúe una expresión que puede haberse
construido dinámicamente.

**Sintaxis**

```racket
(eval <expresión>)
```

**Evaluación**

La función `eval` invoca al intérprete para realizar la evaluación de
la expresión que se le pasa como parámetro y devuelve el resultado de
dicha evaluación.

**Ejemplos**

```racket
(define a 10)
(eval 'a) ; ⇒ 10

(eval '(+ 1 2 3)) ; ⇒ 6

(define lista (list '+ 1 2 3))
(eval lista) ; ⇒ 6

(define a 10)
(define x 'a)
(eval 'x) ; ⇒ a
(eval x) ; ⇒ 10
(eval (eval 'x)) ; ⇒ 10 
```


<p style="margin-bottom:2cm;"></p>


### Listas ###

- En el seminario de Scheme vemos que una de sus características
principales es el uso de listas. 

- Repasamos las funciones más importantes y explicamos el uso de la
  forma especial `quote` para construir listas.

<p style="margin-bottom:2cm;"></p>

### Función `list` y forma especial `quote`

- Función `list`

```racket
(list 1 2 3 4 5) ⇒ (1 2 3 4)
(list 'a 'b 'c) ⇒ (a b c)
(list 1 'a 2 'b 3 'c #t) ⇒ (1 a 2 b 3 c #t)
(list 1 (+ 1 1) (* 2 (+ 1 2))) ⇒ (1 2 6)
```

Otro ejemplo:

```racket
(define a 1)
(define b 2)
(define c 3)
(list a b c) ; ⇒ (1 2 3)
```

- La forma especial `quote` delante de una expresión entre paréntesis
  convierte la expresión en una lista y la devuelve:

```racket
'(1 2 3 4) ; ⇒ (1 2 3 4)
(define a 1)
(define b 2)
(define c 3)
'(a b c) ; ⇒ (a b c)
'(1 (+ 1 1) (* 2 (+ 1 2))) ; ⇒ (1 (+ 1 1) (* 2 (+ 1 2)))
```

La última lista tiene 3 elementos:

- El número 1
- La lista (+ 1 1)
- La lista (* 2 (+ 1 2))

- Otro ejemplo sobre la diferencia entre `list` y `quote`:

```racket
(list 1 (/ 2 3) (+ 2 3)) ; ⇒ (1 2/3 5)
```

```racket
'(1 (/ 2 3) (+ 2 3)) ; ⇒ (1 (/ 2 3) (+ 2 3))
```

<p style="margin-bottom:2cm;"></p>

### Selección de elementos de una lista: `first` y `rest`

- Primer elemento: función `first`
- Resto de elementos: función `rest`

Ejemplos:

```racket
(define lista1 '(1 2 3 4))
(first lista1) ; ⇒ 1
(rest lista1) ; ⇒ (2 3 4)
(define lista2 '((1 2) 3 4))
(first lista2) ; ⇒ (1 2)
(rest lista2) ; ⇒ (3 4)
```

<p style="margin-bottom:2cm;"></p>

### Funciones `cons` y `append`

- La función `cons` crea una nueva lista en la que se añade un
  elemento a la cabeza de la lista que pasamos como parámetro:

```racket
(cons 1 '(1 2 3 4)) ; ⇒ (1 1 2 3 4)
(cons 'hola '(como estás)) ; ⇒ (hola como estás)
(cons '(1 2) '(1 2 3 4))  ; ⇒ ((1 2) 1 2 3 4)
```

- La función `append` crea una nueva lista que en la que se concatenan
  dos o más listas que se pasan como parámetro:

```racket
(define list1 '(1 2 3 4))
(define list2 '(hola como estás))
(append list1 list2) ; ⇒ (1 2 3 4 hola como estás)
```

!!! danger "Diferencias entre cons y append"
    Es muy importante diferenciar `cons` y `append`. En ambos
    casos el resultado es una lista y ambas funciones tienen dos parámetros,
    siendo el segundo la lista en la que se añade el primero. La diferencia
    entre ambas funciones es el tipo del primer parámetro. En `cons` es un
    elemento que se añade a la lista, mientras que en `append` es otra lista que
    se concatena con la segunda.



# Teoría práctica 3

## Tema 2: Programación funcional 

### Veremos hoy

- 1. El paradigma de Programación Funcional
- 2. Scheme como lenguaje de programación funcional

	- 2.1. Funciones y formas especiales
	- 2.2. Formas especiales en Scheme: `define`, `if`, `cond`
	- 2.3. Forma especial `quote` y símbolos
	- 2.4. Listas
    - **2.5. Recursión**
    
- **3. Tipos de datos compuestos en Scheme**
	- **3.1 El tipo de dato pareja**
	- **3.2 Las parejas son objetos de primera clase**
	- **3.3  Diagramas caja-y-puntero**

- **4. Listas en Scheme**
    - **4.1 Implementación de listas en Scheme**
    - **4.2 Listas con elementos compuestos**

---

### Recursión ###

- La recursión es una característica básica de la programación funcional.
- Veremos varios ejemplos de cómo **diseñar** funciones recursivas.

### Confía en la recursión

- En programación funcional las iteraciones se realizan con recursión.
- En una definición recursiva siempre tenemos un caso general y un caso
base. 
- El caso base define el valor que devuelve la función en el caso
elemental en el que no hay que hacer ningún cálculo. 
- El caso general
define una expresión que contiene una llamada a la propia función que
estamos definiendo.

Ejemplo: 

Por ejemplo, podemos definir la función `(suma-hasta x)` que devuelve
la suma de los números hasta el parámetro `x` cuyo valor pasamos en la
invocación de la función.

`(suma-hasta 5)` devolverá `0+1+2+3+4+5 = 15`.

Definición recursiva:

```racket
(define (suma-hasta x)
   (if (= 0 x)
      0
      (+ (suma-hasta (- x 1)) x)))
```

!!! Note "Importante"
    Para entender la recursión no es conveniente utilizar el depurador, ni
    hacer trazas, ni *entrar en la recursión*, sino que hay que
    suponer que **la llamada recursiva se ejecuta y devuelve el valor
    que debería. ¡Debemos confiar en la recursión!**.

El caso general del ejemplo anterior indica lo siguiente:

```text
Para calcular la suma hasta x: 
    Llamamos a la recursión para que calcule la suma hasta x-1 
    (confiamos en que la implementación funciona bien y esta llamada 
    nos devolverá el resultado hasta x-1) y a ese resultado le sumamos
    el propio número x.
```

Un ejemplo concreto, cuando `x` vale 5, `(suma-hasta 5)`:

```text
(+ (suma-hasta (- 5 1)) 5)
``` 

Evaluación:

```text
(+ (suma-hasta (- 5 1)) 5) ⇒
(+ (suma-hasta 4) 5) ⇒ (confiamos en la recursión: (suma-hasta 4) = 10)
(+ 10 5) ⇒
15
```

- La llamada recursiva debe trabajar sobre un caso más sencillo que la
llamada general.


### Diseño de la función `(suma-hasta x)`


<img src="imagenes/suma-hasta.png" width="600px"/>

Generalizamos este ejemplo y lo expresamos en Scheme de la siguiente
forma:

```racket
(define (suma-hasta x)
   (+ (suma-hasta (- x 1)) x))
```

- Nos falta el caso base de la recursión. Debemos preguntarnos **¿cuál
es el caso más sencillo del problema, que podemos calcular sin hacer
ninguna llamada recursiva?**. En este caso podría ser el caso en el
que `x` es 0, en el que devolveríamos 0.

- Podemos ya escribirlo todo en Scheme:

```racket
(define (suma-hasta x)
   (if (= 0 x)
      0
      (+ (suma-hasta (- x 1)) x)))
```


### Otro ejemplo de función recursiva `(alfabeto-hasta char)`

Como antes, veamos un ejemplo concreto:

```racket
(alfabeto-hasta #\h) ; ⇒ "abcdefgh"
```

¿Cómo plantear el caso general? Tenemos que hacer una llamada
recursiva que haga casi todo el trabajo y nos devuelva la cadena con
el alfabeto casi calculada. 

<p style="margin-bottom:3cm;"></p>

¿Podríamos llamar a la recursión para que nos devuelva el alfabeto
hasta el carácter anterior a la `#\h` (el carácter `\#g`)? 

Si confiamos en la recursión:

```racket
(alfabeto-hasta #\g) ; ⇒ "abcdefg"
```

Sólo faltaría entonces añadir la `#\h` al final de la cadena:

```text
"abcdefg" + \#h ⇒ "abcdefgh"
```

¿Cómo lo expresamos en Scheme?

<p style="margin-bottom:3cm;"></p>

El caso general:

```racket
(define (alfabeto-hasta char)
    (string-append (alfabeto-hasta (anterior char)) (string char)))
```

Función `(anterior char)`:

```racket
(define (anterior char)
  (integer->char (- (char->integer char) 1)))
```

Nos faltaría únicamente el caso base.

El caso base sería aquel en el que nos piden lo más sencillo: el
alfabeto hasta el carácter `#\a`, en el que habría que devolver la
cadena "a".

Solución final:

```racket
(define (alfabeto-hasta char)
  (if (equal? char #\a)
      "a"
      (string-append (alfabeto-hasta (anterior char)) (string char))))
```


### Repaso: Selección de elementos de una lista: `first` y `rest`

- Primer elemento: función `first`
- Resto de elementos: función `rest`

Ejemplos:

```racket
(define lista1 '(1 2 3 4))
(first lista1) ⇒ 1
(rest lista1) ⇒ (2 3 4)
(define lista2 '((1 2) 3 4))
(first lista2) ⇒ (1 2)
(rest lista2) ⇒ (3 4)
```



### Recursión y listas: Función `(suma-lista lista-nums)`

Supongamos que queremos definir una función `suma-lista` que reciba
como parámetro una lista de números y devuelva la suma de todos ellos.

Ejemplo:

```racket
(suma-lista '(12 3 5 1 8)) ; ⇒ 29
```

- En este caso podemos pensar que para sumar la lista de
números `(12 3 5 1 8)` podemos obtener un problema más sencillo (una
lista más pequeña) haciendo el `rest` de la lista de números y llamando
a la recursión con el resultado. 

- La llamada recursiva devolverá la suma de esos números (confiamos en
la recursión) y a ese valor basta con sumarle el primer número de la
lista. Lo podemos representar en el siguiente dibujo:

<img src="imagenes/suma-lista.png" width="600px"/>

- Podemos generalizar este ejemplo y expresarlo en Scheme de la siguiente forma:

```racket
(define (suma-lista lista)
    (+ (first lista) (suma-lista (rest lista))))
```

- Falta el caso base, que es el caso más sencillo en que podemos
devolver un valor sin llamar a la recursión. En este caso, podría ser
cuando le pesamos a la función una lista sin elementos, en donde hay
que devolver 0.

Con todo junto, quedaría la recursión como sigue

```racket
(define (suma-lista lista)
   (if (null? lista)
       0
	   (+ (first lista) (suma-lista (rest lista)))))
```
   
### Función recursiva `veces`

Como último ejemplo vamos a definir la función `(veces lista id)` que
cuenta el número de veces que aparece un identificador en una lista.

- ¿Cómo planteamos el caso general? Llamaremos a la recursión con el
resto de la lista. Esta llamada nos devolverá el número de veces que
aparece el identificador en este resto de la lista. Y después sumamos
al valor devuelto 1 si el primer elemento de la lista coincide con el
identificador.

El caso general en Scheme:

```racket
(if (equal? (first lista) id)
    (+ 1 (veces (rest lista) id))
    (veces (rest lista) id))
```

Como caso base, si la lista es vacía devolvemos 0.

La versión completa:

```racket
(define (veces lista id)
  (cond
    ((null? lista) 0)
    ((equal? (first lista) id) (+ 1 (veces (rest lista) id)))
    (else (veces (rest lista) id))))

(veces '(a b a a b b) 'a) 
⇒ 3 
```



### Tipos de datos compuestos en Scheme ###

- El tipo pareja
- Las parejas son objetos de primera clase
- Diagramas caja-y-puntero


### El tipo de dato pareja

- Ya lo hemos visto en el seminario
- `cons` para construir parejas:

```racket
(cons 1 2) ; ⇒ (1 . 2)
(define c (cons 1 2))
```

- También podemos construir una pareja utilizando la forma especial
  `quote` escribiendo entre paréntesis separados por un punto los
  elementos que forman la pareja:
  
```racket
(define c '(1 . 2))
```

- Al igual que con las listas, la diferencia entre `cons` y `quote`
  para construir una pareja es que `quote` no evalúa sus parámetros:

```racket
(define a 1)
(define b 2)
(cons a b) ; ⇒ (1 . 2)
'(a . b) ; ⇒ (a . b)
```

### Funciones de acceso `car` y `cdr`

- `car` y `cdr` devuelven la parte izquierda y derecha:

```racket
(define c (cons 1 2))
(car c) ; ⇒ 1
(cdr c) ; ⇒ 2
```


### Definición declarativa


```racket
(car (cons x y)) = x
(cdr (cons x y)) = y
```

### Función pair?


```racket
(pair? 3) ; ⇒ #f
(pair? (cons 3 4)) ; ⇒ #t
```


### Las parejas pueden contener cualquier tipo de dato

```racket
(define c (cons 'hola #f))
(car c) ; ⇒ 'hola
(cdr c) ; ⇒ #f
```

### Las parejas son objetos inmutables

- En programación funcional una vez creada una pareja no está permitido modificar (mutar) su contenido.
- En Scheme hay funciones para mutar parejas, pero no las veremos hasta ver el paradigma de programación imperativa


### Las parejas son objetos de primera clase

En un lenguaje de programación un elemento es de primera clase cuando puede:

* Asignarse a variables
* Pasarse como argumento
* Devolverse por una función
* Guardarse en una estructura de datos mayor

Las parejas son objetos de primera clase.


### Asignación a una variable (1)

Una pareja puede asignarse a una variable:

```racket
(define p1 (cons 1 2))
(define p2 (cons #f "hola"))
```

### Paso como argumento y devolverse como resultado de una función (2 y 3)

```racket
(define (suma-parejas p1 p2)
    (cons (+ (car p1) (car p2))
          (+ (cdr p1) (cdr p2))))
```

Lo probamos ...

<p style="margin-bottom:2cm"></p>


### Ejemplo de función que recibe distintos tipos de datos

- Scheme es débilmente tipado
- Podemos pasar cualquier tipo de dato en los parámetros de las funciones, por ejemplo a la siguiente función `suma`

```racket
(define (suma x y)
  (cond 
    ((and (number? x) (number? y)) (+ x y))
    ((and (pair? x) (pair? y)) (suma-parejas x y))
    ((and (string? x) (string? y)) (string-append x y))
    (else 'error)))
```

Lo probamos ...


<p style="margin-bottom:3cm;"></p>



### Formar parte de otras parejas (4)

- El resultado de un `cons` puede usarse como parámetro de nuevas llamadas a `cons`.


```racket
(define p1 (cons 1 2))
(define p2 (cons 3 4))
(define p (cons p1 p2))
```

### Diagramas caja-y-puntero

```racket
(define p (cons (cons 1 2)
                (cons 3 4)))
```

<img src="./imagenes/pareja-pareja.png" width="300px"/>

Diagramas *caja-y-puntero* (*box-and-pointer* en inglés):

<img src="./imagenes/pareja-pareja2.png" width="250px"/>


### Ejemplos de diagramas caja-y-puntero

- Es conveniente indentar correctamente los `cons`:

```racket
(define p (cons (cons 1
                      (cons 3 4))
                2))
```

- Es importante recordar que las expresiones se evalúan *de dentro a afuera*.
- ¿Qué estructura se construye con la sentencia anterior? Dibuja el diagrama *box-and-pointer*.

<p style="margin-bottom:3cm;"></p>

- ¿Cuál sería el diagrama resultante de la siguiente expresión?


```racket
(define p2 (cons 5 (cons p 6)))
```

<p style="margin-bottom:4cm;"></p>

- ¿Cómo sería la expresión formada por `car` y `cdr`s que devolviera 3 a partir de la variable `p2`?

<p style="margin-bottom:4cm;"></p>


### Funciones c????r

- Al trabajar con estructuras de parejas anidades es muy habitual realizar llamadas del tipo:

```racket
(cdr (cdr (car p)))
```

- Es equivalente a la función `cadar` de Scheme:

```racket
(cddar p)
```

- El nombre de la función se obtiene concatenando a la letra "c", las letras "a" o "d" según hagamos un car o un cdr y terminando con la letra "r".

- Hay definidas 2^4 funciones de este tipo: `caaaar`, `caaadr`, …, `cddddr`.

- También hay combinaciones de 3, 2 y 1 letra. En total hay 30 funciones de este tipo: 2^1 + 2^2 + 2^3 + 2^4 

### Listas en Scheme 

- Las listas se implementan en Scheme usando parejas.
- Hemos usado las funciones `first` y `rest` para trabajar con
  listas. Pero como una lista es una pareja, también podemos usar las
  funciones `car` y `cdr`. ¿Qué devolverían esas funciones?

### Repaso: función cons con listas

- La función `cons` crea una lista nueva resultante de añadir un elemento
al comienzo de la lista:

```racket
(cons 1 '(1 2 3 4)) ⇒ (1 1 2 3 4)
(cons 'hola '(como estás)) ⇒ (hola como estás)
(cons '(1 2) '(1 2 3 4))  ⇒ ((1 2) 1 2 3 4)
```

### Relación entre listas y parejas en Lisp y Scheme

- Hagamos algunas pruebas.

¿Una pareja es una lista?
Lo probamos ...

```racket
(define p1 (cons 1 2))
(pair? p1) 
(list? p1) 
```

<p style="margin-bottom:2cm;"></p>

¿Una lista es una pareja?
Lo probamos ...

```racket
(define lista '(1 2 3))
(list? lista)
(pair? lista)
```

<p style="margin-bottom:2cm;"></p>

Como hemos dicho, una lista es una pareja. ¿Qué devuelven las
funciones `car` y `cdr` aplicadas sobre una lista?

```racket
(define lista '(1 2 3))
(car lista) -> ?
(cdr lista) -> ?
```

<p style="margin-bottom:2cm;"></p>

Y el resultado de construir una nueva pareja con un dato y otra lista
también es otra lista:

```racket
(define lista '(1 2 3))
(define p1 (cons 1 lista))
(list? p1)
```

<p style="margin-bottom:2cm;"></p>

¿Una pareja con una lista vacía como parte derecha es una lista?
Lo probamos ...

```racket
(define p1 (cons 1 '()))
(pair? p1)
(list? p1)
```
<p style="margin-bottom:2cm;"></p>

¿Una lista vacía es una lista? ¿Es una pareja?
Lo probamos ...

```racket
(list? '())
(pair? '())
```

<p style="margin-bottom:2cm;"></p>

Con estos ejemplos tenemos pistas más que de sobra para deducir la
relación entre listas y parejas en Scheme (y Lisp). Vamos a
explicarlo.


### Definición de listas con parejas

Una lista es (definición recursiva):

* Una **pareja** que contiene:
    * *En su parte izquierda*: el primer elemento de la lista
    * *En su parte derecha*: el resto de la lista (volvemos a aplicar la definición)
* Un **símbolo especial** `'()` que denota la lista vacía.


### Ejemplo más sencillo: `(1)`

```racket
(cons 1 '())
```
	
La pareja cumple las condiciones anteriores: 

* La parte izquierda de la pareja es el primer elemento de la lista (el número 1)
* La parte derecha es el resto de la lista (la lista vacía)

<img src="./imagenes/pareja-lista.png" width="150px"/>


- Es al mismo tiempo una pareja y una lista:

```racket
(define l (cons 1 '()))
(pair? l)
(list? l)
```


### Otro ejemplo: `(1 2 3)`

```racket
(cons 1
      (cons 2
            (cons 3
                  '())))
```

- La primera pareja cumple las condiciones de ser una lista:

* Su primer elemento es el 1
* Su parte derecha es la lista '(2 3)

<img src="./imagenes/lista.png" width="400px"/>


### Lista vacía

La lista vacía es una lista:

```racket
(list? '())
```

No es un símbolo ni una pareja:

```racket
(symbol? '())
(pair? '())
```

Función `null?`:

```racket
(null? '())
```	

El símbolo `null` está definido en Racket y contiene la lista vacía:

```racket
null ; ⇒ '()
```

### Listas con elementos compuestos

- *Lista de asociación*, listas cuyos elementos son parejas (*clave*, *valor*):

```racket
(list (cons 'a 1)
      (cons 'b 2)
      (cons 'c 3))
```

¿Cuál sería el diagrama *box and pointer* de la estructura anterior?

<p style="margin-bottom:4cm;"></p>

- Expresión equivalente utilizando *conses* es:

```racket
(cons (cons 'a 1)
      (cons (cons 'b 2)
            (cons (cons 'c 3)
                  '())))
```


### Listas de listas

```racket
(define lista (list 1 (list 1 2 3) 3))
```

Definición con `quote`:

```racket
(define lista '(1 (1 2 3) 3))
```

¿Cuál sería el diagrama *box and pointer* de la estructura anterior?

<p style="margin-bottom:4cm;"></p>


### Ejemplo inverso  ###

Un último ejemplo. Supongamos el siguiente diagrama caja y puntero:

<img src="imagenes/lista-complicada.png" width="500px"/>


¿Cuál sería la expresión en Scheme (usando llamadas a `list` y `cons`) que lo
construye?

<p style="margin-bottom:4cm;"></p>

Solución: 

```racket
(define p1 (list (cons (cons 1 2)
                       (cons 3 4))
                 (list 5 6 (cons 7
                                 (cons 8 9)))
                 10))
```



### Impresión de listas y parejas por el intérprete de Scheme

El intérprete de Scheme siempre intenta mostrar una lista cuando
encuentra una pareja cuyo siguiente elemento es otra pareja.

Por ejemplo, si tenemos la siguiente estructura:

```racket
(define p (cons 1 (cons 2 3)))
```

Cuando se evalúe `p` el intérprete imprimirá por pantalla lo
siguiente:

```racket
(1 2 . 3)
```

Si queremos comprobar la estructura de parejas podemos utilizar la
función `print-pareja` definida en los apuntes, que imprimiría lo
siguiente:

```racket
(print-pareja p) ; ⇒ (1 . (2 . 3))
```


### Distintos niveles de abstracción

- Una vez que conocemos la implementación de listas con parejas, no va
  a a ser necesario casi nunca *bajar* a este nivel de implementación
  ni usar las funciones `car` y `cdr` para trabajar con ellas.
- Podemos volver a la *abstracción* inicial en la usamos las funciones `first` y `rest`:
    - `(first lista)`: devuelve el primer elemento de la lista
    - `(rest lista)`: devuelve el resto de la lista
    - `(list-ref lista n)`: devuelve la posición `n` de la lista
    - `(cons dato lista)`: devuelve una nueva lista con `dato` en su primera posición y `lista` como su resto

<p style="margin-bottom:4cm;"></p>


# Teoría práctica 4

## Tema 2: Programación funcional

### Veremos hoy


- 1. El paradigma de Programación Funcional
- 2. Scheme como lenguaje de programación funcional
- 3. Tipos de datos compuestos en Scheme
- 4. Listas en Scheme
    - 4.1 Implementación de listas en Scheme
    - 4.2 Listas con elementos compuestos
    - **4.3. Funciones recursivas para construir listas**
    - **4.4. Funciones con número variable de argumentos**
- **5. Funciones como tipos de datos de primera clase**
    - **5.1. Forma especial `lambda`**
    - **5.2. Funciones como argumentos de otras funciones**
    - 5.3. Funciones que devuelven otras funciones
    - 5.4. Funciones en estructuras de datos
    - 5.5. Generalización
    - 5.6. Funciones de orden superior

### Funciones recursivas para construir listas

Vamos a ver cómo se implementan de forma recursiva:

- Funciones de Scheme que trabajan con listas (para no solapar con las
  definiciones de Scheme pondremos el prefijo `mi-` en todas ellas):
    - Función `mi-append`
    - Función `mi-reverse`
- Otras funciones recursivas
    - Función `lista-desde`
    - Función `filtra-pares`
- Ejemplo completo: usamos las funciones anteriores para comprobar si
  un número es primo
    - Función `primo?`


### Recordatorio: Diseño de funciones recursivas

¿Cómo diseñamos una *definición recursiva* de una función? 

- Es recomendable comenzar por el **caso general**.
- Debemos buscar una forma de resolver el problema principal haciendo
  una llamada a la recursión con una versión más pequeña del problema,
  **confiar en que la recursión funciona correctamente** devolviendo
  lo que tiene que devolver y obtener con este valor devuelto la
  solución al problema principal. Es recomendable probar con un
  **ejemplo concreto**.
- Una vez formulado el caso general, buscamos el **caso base de la
  recursión**: el caso más sencillo posible en el que no es necesario
  hacer una llamada recursiva para devolver la solución.


### Función `mi-append` 

- Queremos conseguir una implementación recursiva de la función
  `append` que construye una lista resultante de la unión de dos. Por
  ejemplo:

    ```racket
    (mi-append '(a b c) '(d e f)) ; ⇒ (a b c d e f)
    ```

- ¿Cómo formulamos el ejemplo de forma recursiva? 

<p style="margin-bottom: 1cm;"></p>

- ¿Funcionaría si llamamos a la recursión con el resto de la primera
lista y el resto de la segunda lista? ¿Podríamos conseguir a partir de
la lista a resultante de esa llamada recursiva la lista que queremos?
Vamos a probarlo:

    <p style="margin-bottom: 1cm;"></p>

    ```racket
    (mi-append '(b c) '(e f)) => '(b c e f)
    ```
    
    <p style="margin-bottom: 1cm;"></p>

    ¿Podemos conseguir la lista `(a b c d e f)` a partir de la lista `(b c
    e f)` y de `a` y `d`? No, no hay una forma fácil de hacerlo.

<p style="margin-bottom: 1cm;"></p>

- ¿Funcionaría si llamamos a la recursión con la primera lista y el
  resto de la segunda? 

    <p style="margin-bottom: 1cm;"></p>
  
    Vamos a probarlo:

    ```text
    (mi-append '(a b c) '(e f)) => '(a b c e f)
    ```
    
    <p style="margin-bottom: 1cm;"></p>

    ¿Podemos conseguir la lista `(a b c d e f)` a partir de la lista `(a
    b c e f)` y `d`? No, no hay una forma fácil de hacerlo.

<p style="margin-bottom: 1cm;"></p>

- ¿Cuál es la forma correcta de hacerlo? 

    <p style="margin-bottom: 1cm;"></p>

    ```text
    (mi-append '(b c) '(d e f)) => '(b c d e f)
    ```
    
    <p style="margin-bottom: 1cm;"></p>

    Y después hacer un `cons` de `a` y la lista resultante de la llamada a
    la recursión:

    ```text
    (cons 'a (mi-append '(b c) '(d e f))) = 
    (cons 'a (b c d e f)) = 
    (a b c d e f)
    ```
<p style="margin-bottom: 1cm;"></p>

- En general:

    ```racket
    (define (mi-append lista1 lista2) 
        (cons (first lista1) (mi-append (rest lista1) lista2)))
    ```

- El caso base es aquel en el que `lista1` es `null?`. En ese caso
  devolvemos `lista2`:

    ```racket
    (mi-append '() '(a b c)) ;⇒ '(a b c)
    ```

- La formulación recursiva completa queda como sigue:

    ```racket
    (define (mi-append l1 l2)
        (if (null? l1)
            l2
            (cons (first l1)
                  (mi-append (rest l1) l2))))
    ```


### Función `mi-reverse`

- Ejemplo

    ```racket
    (mi-reverse '(1 2 3 4 5 6)) ; ⇒ (6 5 4 3 2 1)
    ```

- La idea es sencilla: llamamos a la recursión para hacer la inversa
  del `rest` de la lista y añadimos el primer elemento a la lista
  resultante.

- Podemos definir una función auxiliar `(añade-al-final dato lista)`
  que añade un dato al final de una lista usando `append`:

    ```racket
    (define (añade-al-final dato lista)
        (append lista (list dato)))
    ```

- La función `mi-reverse` quedaría entonces como sigue:

    ```racket
    (define (mi-reverse lista)
        (if (null? lista) '()
            (añade-al-final (first lista) (mi-reverse (rest lista)))))
    ```


### Función `lista-desde`

- La función `(lista-desde x)` devuelve una lista con los
  números desde x hasta 1:

    ```racket
    (lista-desde 5) ; ⇒ (5 4 3 2 1)
    ```

- ¿Cómo formulamos el ejemplo de forma recursiva?

<p style="margin-bottom: 3cm;"></p>

- Solución:

    ```text
    (lista-desde 5) = 
    (cons 5 (lista-desde 4) =
    (cons 5 (4 3 2 1)) = 
    (5 4 3 2 1)
    ```

- En general:

    ```text
    Para construir una lista desde x hasta 1:
       construyo la lista desde x-1 hasta 1 y le añado 
       en cabeza el número x
    ```

- El caso base de la recursión es el caso en el que x es 1, entonces
  devolvemos '(1)

- Ya podemos realizar la definición Scheme:

    ```racket
    (define (lista-desde x)
        (if (= x 1)
            '(1)
            (cons x
                  (lista-desde (- x 1)))))
    ```


### Función `filtra-pares`

- Es muy habitual recorrer una lista y comprobar condiciones de sus
  elementos, construyendo una lista con los que cumplan una
  determinada condición.

- La función `filtra-pares` construye una lista con los números pares
  de la lista que le pasamos como parámetro:

    ```racket
    (filtra-pares '(1 2 3 4 5 6)) ;⇒ (2 4 6)
    ```

- ¿Cómo la definimos de forma recursiva?

<p style="margin-bottom:3cm;"></p>


- Solución en Scheme

    ```racket
    (define (filtra-pares lista)
        (cond
            ((null? lista) '())
            ((even? (first lista))
                (cons (first lista) (filtra-pares (rest lista))))
            (else (filtra-pares (rest lista)))))
    ```


### Ejemplo final: Función `primo?`

- El uso de listas es uno de los elementos fundamentales de la
  programación funcional.

- Veamos un algoritmo sencillo que permite calcular si un número es
  primo, usando alguna de las funciones anteriores sobre
  listas. Calcularemos la lista de divisores del número y
  comprobaremos si su longitud es dos:

    ```racket
    (divisores 8) ;⇒ (1 2 4 8) longitud = 4, no primo
    (divisores 9) ;⇒ (1 3 9) longitud = 3, no primo
    (divisores 11) ;⇒ (1 11) longitud = 2, primo
    ```

- En Scheme:

    ```racket
    (define (primo? x)
        (=  2 
        (length (divisores x))))
    ```


### Función `(divisor? x y)`

```racket
(define (divisor? x y)
      (= 0 (remainder y x)))
```


### Función recursiva `(filtra-divisores lista x)`

- Función que filtra aquellos números `lista` que son divisores del número `x`

    ```racket
    (define (filtra-divisores lista x)
       (cond
          ((null? lista) '())
          ((divisor? (first lista) x)
             (cons (first lista)
                   (filtra-divisores (rest lista) x)))
          (else (filtra-divisores (rest lista) x))))
    ```


### Función `(divisores x)` 

- Una vez definidas las funciones auxiliares anteriores, se puede
  implementar de una forma muy sencilla una función `(divisores x)`
  que devuelve una lista de todos los divisores del número `x`:

    ```racket
    (define (divisores x)
        (filtra-divisores (lista-desde x) x))
    ```

- Por ejemplo, para calcular los divisores de 10:

    ```racket
    (filtra-divisores '(10 9 8 7 6 5 4 3 2 1) 10) ;⇒ (10 5 2 1)
    ```

- Y, una vez definida esta función, ya funciona correctamente la
  función `primo?` con la primera definición que vimos:

    ```racket
    (define (primo? x)
        (=  2 
        (length (divisores x))))
    ```


<p style="margin-bottom:1cm;"></p>

----
<p style="margin-bottom:1cm;"></p>


### Funciones con número variable de argumentos

- Definición de número variable de argumentos con la notación de
  punto:

    ```racket
    (define (funcion-dos-o-mas-args x y . lista-args) 
        <cuerpo>)
    ```

- Podemos llamar a la función anterior con dos o más argumentos:

    ```racket
    (funcion-dos-o-mas-args 1 2 3 4 5 6)
    ```
	
- En la llamada, los parámetros `x` e `y` tomarán los valores 1 y 2.
- El parámetro `lista-args` tomará como valor una lista con los
  argumentos restantes `(3 4 5 6)`.
- También es posible permitir que todos los argumentos sean opcionales
  no poniendo ningún argumento antes del punto:

    ```racket
    (define (funcion-cualquier-numero-args . lista-args) 
        <cuerpo>)
    ```
	
- Ejemplo:

    ```racket
    (define (mi-suma x y . lista-nums)
        (if (null? lista-nums)
            (+ x y)
            (+ x (+ y (suma-lista lista-nums)))))
    ```
¿Las funciones con número variable de argumentos pueden ser recursivas? 

<p style="margin-bottom:1cm;"></p>
----
<p style="margin-bottom:1cm;"></p>


### Funciones como tipos de datos de primera clase

Recordemos que un tipo de primera clase es aquel que:

1. Puede ser asignado a una variable
2. Puede ser pasado como argumento a una función
3. Puede ser devuelto como resultado de una invocación a una función
4. Puede ser parte de un tipo mayor

Con funciones:

1. Una función se puede asignar a una variable
2. Una función se puede pasar como parámetro de otras funciones 
3. Una función se puede devolver como resultado de una invocación a otra función
4. Una función se puede guardar en tipos de datos compuestos como listas

- Las funciones son objetos de primera clase en lenguajes funcionales
  y en muchos lenguajes multi-paradigma con características funcionales como
  [JavaScript](http://helephant.com/2008/08/19/functions-are-first-class-objects-in-javascript/),
  [Python](https://thenewcircle.com/static/bookshelf/python_fundamentals_tutorial/functional_programming.html),
  [Swift](https://developer.apple.com/library/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Closures.html)
  o incluso en la última versión de Java, [Java
  8](http://docs.oracle.com/javase/tutorial/java/javaOO/lambdaexpressions.html),
  (donde se denominan *expresiones lambda*).

### Forma especial `lambda`

- Cualquier objeto de primera clase de un lenguaje debe poderse
  crear de forma anónima, sin asignarle un nombre. Por ejemplo, en la
  expresión:
  
    ```racket
    (string-append "hola" "adiós")
    ```

    las cadenas `"hola"` y `"adiós"` se han creado directamente,
    sin darles nombre, y se han pasado como parámetros a la función
    `string-append`.

- La forma especial `lambda` permite hacer lo mismo con las funciones:
  crear funciones anónimas en tiempo de ejecución.


### Sintaxis de la forma especial `lambda`

- La sintaxis de la forma especial `lambda` es:

    ```text
    (lambda (<arg1> ... <argn>) 
        <cuerpo>)
    ```

- El cuerpo del lambda define un *bloque de código* y sus argumentos
  son los parámetros necesarios para ejecutar ese bloque de
  código. Llamamos a la función resultante una *función anónima*.

- Una función anónima que suma dos parejas:

    ```racket
    (lambda (p1 p2)
        (cons (+ (car p1) (car p2))
              (+ (cdr p1) (cdr p2))))
    ```

- Una función anónima que devuelve el mayor de dos números:

    ```racket
    (lambda (a b)
        (if (> a b)
            a
            b))
    ```


### Semántica de la forma especial `lambda`

- La invocación a la forma especial `lambda` construye una función
  anónima en tiempo de ejecución.

    ```racket
    (lambda (x) (* x x)) ; ⇒ #<procedure>
    ```

- El procedimiento construido es un bloque de código que devuelve el
  cuadrado de un número.

- ¿Qué podemos hacer con este procedimiento? 


### Podemos asignar el procedimiento a un identificador (símbolo)

```racket
(define f (lambda (x) (* x x)))
```

- Se evalúa la expresión lambda y el resultado (un procedimiento) se
  guarda en `f`
- Si escribimos `f` en el intérprete, Scheme lo evalúa y muestra el
  procedimiento:

    ```racket
    f ; ⇒ #<procedure:f>
    ```

- Podemos usar el identificador `f` de la forma que habitualmente
  invocamos a una función:

    ```racket
    (f 3) ; ⇒ 9
    ```


### Podemos invocar a la función anónima directamente


```racket
((lambda (x) (* x x)) 3) ; ⇒ 9
```

- La llamada a `lambda` crea un procedimiento y el paréntesis a su
izquierda lo invoca con el parámetro 3:

    ```racket
    ((lambda (x) (* x x)) 3) ; => (#<procedure> 3) ⇒ 9
    ```

- Es importante remarcar que con `lambda` estamos creando una función
  en *tiempo de ejecución*.


### Expresiones lambda en distintos lenguajes de programación

**Java 8**

```java
Integer x -> {x*x}
```

**Scala**

```scala
(x:Int) => {x*x}
```

**Objective C**

```objective-c
^int (int x)
{
   x*x
};
```

**Swift**

```swift
{ (x: Int) -> Int in return x*x }
```


### Identificadores y funciones

- En Scheme una función está ligada al símbolo que define su nombre:

    ```racket
    + ; ⇒ <procedure:+>
    ```

- Podemos asignar funciones ya existentes a nuevos identificadores
  usando `define`, como en el ejemplo siguiente:

    ```racket
    + ;⇒ <procedure:+>
    (define suma +)
    (suma 1 2 3 4) ; ⇒ 10
    ```

<img src="./imagenes/suma.png" style="width:100px;"/>


### La forma especial `define` para definir una función no es más que azucar sintáctico

- La forma especial `define` para definir funciones siempre se
  convierte internamente en una llamada a `lambda` y una asociación de
  la función a su nombre:

    ```text
    (define (<nombre> <args>)
        <cuerpo>)
    ```

    ```text
    (define <nombre> 
        (lambda (<args>)
            <cuerpo>))
    ```

- Ejemplo:

    ```racket
    (define (cuadrado x)
        (* x x))
    ```

    ```racket
    (define cuadrado 
        (lambda (x) (* x x)))
    ```


### Predicado `procedure?`

- Podemos comprobar si algo es una función utilizando el predicado de
  Scheme `procedure?`.

    ```racket
    (procedure? (lambda (x) (* x x)))
    ; ⇒ #t
    (define suma +)
    (procedure? suma)
    ; ⇒ #t
    (procedure? '+)
    ; ⇒ #f
    ```


### Funciones argumentos de otras funciones

- Ya hemos visto que una función se pueda asignar a una variable. Para
  seguir comprobando que es un objeto de primera clase, vamos a
  comprobar que se puede pasar como parámetro de otra función.


### Función `(aplica f x y)`

- La función `(aplica f x y)` recibe una función como argumento y dos
  parámetros. Devuelve el resultado de evaluar la función `f` con los
  argumentos `x` e `y`
  
    ```racket
    (define (aplica f x y)
       (f x y))
    ```

- Ejemplos:

    ```racket
    (aplica + 2 3) ; ⇒ 5
    (aplica * 4 5) ; ⇒ 10
    (aplica string-append "hola" "adios") ; ⇒ "holaadios"

    (define (string-append-con-guion s1 s2)
        (string-append s1 "-" s2))

    (aplica string-append-con-guion "hola" "adios") ; ⇒ "hola-adios"
    ```

- Podemos pasar la función creándola con una expresión lambda:

    ```racket
    (aplica (lambda (x y) (sqrt (+ (* x x) (* y y)))) 3 4) ; ⇒ 5
    ```

### Función `aplica-2` 

- La función `aplica-2` toma dos funciones `f` y `g` y un argumento
  `x` y devuelve el resultado de aplicar `f` a lo que devuelve la
  invocación de `g` con `x`:

    ```racket
    (define (aplica-2 f g x)
       (f (g x)))
    ```

- Ejemplos de invocación

    ```racket
    (define (suma-5 x)
       (+ x 5))
    (define (doble x)
       (+ x x))
    (aplica-2 suma-5 doble 3) ; ⇒ 11
    
    (aplica-2 (lambda (x) (* x 2))
              (lambda (x) (+ x 5)) 10) ; ⇒ 30
    ```

### Función `apply` ###

La función `(apply funcion lista)` de Scheme permite aplicar una función de
aridad `n` a una lista de datos de n datos, haciendo que cada uno de
los datos se pasen a la función en orden como parámetros.

La función `apply` recibe una función y una lista y devuelve el
resultado de aplicar la función a los datos de la lista, tomándolos
como parámetros.

Ejemplo:

```racket
(apply + '(1 2 3 4)) ; ⇒ 10
```

Podemos pasar a `apply` una expresión lambda:

```racket
(apply (lambda (x y) (+ x (* 2 y))) '(2 5)) ; ⇒ 12
```

La lista que pasamos como argumento de `apply` debe tener tantos
elementos como parámetros tenga la función que aplicamos. En caso
contrario, se produce un error:

```racket
(apply cons '(a b c)) ; ⇒ error
cons: arity mismatch;
 the expected number of arguments does not match the given number
  expected: 2
  given: 3
  arguments...:
```

La forma correcta de hacerlo:

```racket
(apply cons '(a b)) ; ⇒ (a . b)
```

### Función `apply` y funciones recursivas ###

Usando `apply` podemos definir funciones recursivas con número
variable de argumentos.

Por ejemplo, supongamos que queremos definir la función `suma-parejas`
que suma un número variable de parejas:

```racket
(suma-parejas '(1 . 2) '(3 . 4) '(5 . 6)) ; ⇒ '(9 . 12)
```

Recordemos la definición de la función que suma dos parejas:

```racket
(define (suma-pareja p1 p2)
  (cons (+ (car p1) (car p2))
        (+ (cdr p1) (cdr p2))))
```

¿Cómo podríamos, usando `apply`, resolver el problema de sumar un
número variable de parejas?

```racket
(define (suma-parejas . parejas)
  (if (null? parejas)
      '(0 . 0)
      (suma-pareja ???  (apply ???))))
```

<p style="margin-bottom:3cm;"></p>

Solución:

```racket
(define (suma-parejas . parejas)
  (if (null? parejas)
      '(0 . 0)
      (suma-pareja (first parejas) (apply suma-parejas (rest parejas)))))
```

Una representación gráfica de cómo funciona la recursión:

<img src="imagenes/suma-parejas-apply.png" width="600px"/>



## Teoría práctica 5


## Tema 2: Programación funcional 

### Veremos hoy

- 1 El paradigma de Programación Funcional
- 2 Scheme como lenguaje de programación funcional
- 3 Tipos de datos compuestos en Scheme
- 4 Listas en Scheme
- 5 **Funciones como tipos de datos de primera clase**
    - 5.1 Forma especial `lambda`
    - 5.2 **Funciones como argumentos de otras funciones**
	- 5.3 **Funciones que devuelven funciones**
    - 5.4 **Funciones en estructuras de datos**
    - 5.5 **Funciones de orden superior**

----

### Ejemplo de uso de parámetros de tipo función para generalizar

- La posibilidad de pasar funciones como parámetros de otras es una
  poderosa herramienta de abstracción. Veamos un ejemplo.

- Supongamos que queremos calcular el sumatorio de `a` hasta
  `b`. ¿Cómo lo haríamos de forma recursiva?

<p style="margin-bottom:3cm;"></p>

- Solución:

    ```racket
    (define (sum-x a b)
        (if (> a b)
            0
            (+ a (sum-x (+ a 1) b))))

    (sum-x 1 10) ; ⇒ 55
    ```

- Supongamos ahora que queremos calcular el sumatorio de `a` hasta `b`
  **sumando los números al cuadrado**. ¿Cómo lo haríamos?


<p style="margin-bottom:3cm;"></p>

- Solución:

    ```racket
    (define (sum-cuadrado-x a b)
        (if (> a b)
            0
            (+ (* a a) (sum-cuadrado-x (+ a 1) b))))

    (sum-cuadrado-x 1 10) ; ⇒ 385
    ```

- ¿Y el sumatorio de `a` hasta `b` **sumando los cubos**?

<p style="margin-bottom:3cm;"></p>

- Solución:

    ```racket
    (define (sum-cubo-x a b)
        (if (> a b)
            0
            (+ (* a a a) (sum-cubo-x (+ a 1) b))))

    (sum-cubo-x 1 10) ; ⇒ 3025
    ```

- El código de las tres funciones anteriores es muy similar.
- Podemos generalizarlo definiendo una función que haga la recursión y
  que reciba como parámetro otra función que se aplica a los números.
- Podemos definir una función genérica `sum-f-x` que generaliza las
  tres funciones anteriores: el sumatorio desde `a` hasta `b` de
  `f(x)`:

    ```racket
    (define (sum-f-x f a b)
        (if (> a b)
            0
            (+ (f a) (sum-f-x f (+ a 1) b))))
    ```

- Las funciones anteriores son casos particulares de esta función que
  las generaliza. Por ejemplo, para calcular el sumatorio desde 1
  hasta 10 de `x` al cubo:

    ```racket
    (define (cubo x)
        (* x x x))

    (sum-f-x cubo 1 10) ; ⇒ 3025
    ```

- O podemos sumar la expresión (n/(n-1)) para todos los números del 2
  al 100. Usamos una expresión lambda:
  
    ```racket
    (sum-f-x (lambda (n) (/ n (- n 1))) 2 100)
    ```

----

### Funciones que devuelven funciones

- Un objeto de primera clase puede ser devuelto por una función: es
  posible definir funciones que devuelvan otras funciones.
- Característica fundamental del paradigma funcional, no presente en
  lenguajes que no son funcionales (como C, C++ o Java (antes de Java
  8)).
- La función devuelta se crea en tiempo de ejecución, durante la
  invocación a la función principal.
- La función devuelta se denomina **clausura** (_closure_ en inglés).

----

### Ejemplo: función `construye-sumador`

- Definimos una función constructora `(construye-sumador k)` que crea
  en su ejecución una función sumadora:


    ```racket
    (define (construye-sumador k)
       (lambda (x)
           (+ x k)))
    ```

- La función constructora `construye-sumador` devuelve un procedimiento: 

    ```racket
    (construye-sumador 10) ; ⇒ #<procedure>
    ```

- Por ejemplo, si le pasamos 10, como parámetro devolverá una función
de un argumento que sumará 10 a ese argumento:


    ```racket
    (define f (construye-sumador 10))
    (f 3) ; ⇒ 13
    ```

- También:

    ```racket
    ((construye-sumador 10) 3) ; ⇒ 13
    ```

- Dependiendo del parámetro que le pasemos a la función constructora
  obtendremos una función sumadora que sume un número u otro. Por
  ejemplo para obtener una función sumadora que suma 100:
  
    ```racket
    (define g (construye-sumador 100))
    (g 3) ; ⇒ 103
    ```

- ¿Cómo funciona la clausura?

    ```racket
    (define k 10)
    (define (construye-sumador k)
       (lambda (x)
           (+ x k)))
    (define g (construye-sumador 100))
    (define f (construye-sumador 50))
    (g 3) ; ⇒ ???
    (f 6) ; ⇒ ???
    ```

- Cuando invocamos a `construye-sumador` con un valor concreto para
  `k` (por  ejemplo 100), queda vinculado el valor de 100 al parámetro
  `k` en el ámbito local de la función.
- En este ámbito local la expresión lambda crea una función. Esta
  función creada en el ámbito local **captura** este ámbito local, con
  sus variables y sus valores (en este caso la variable `k` y su valor
  100).
- Cuando se invoca a la función desde fuera (cuando llamamos a `g` en
  el ejemplo) se ejecuta el cuerpo de la función `(+ x k)` con `x`
  valiendo el parámetro (3) y el valor de `k` se obtiene del ámbito
  capturado (100).

- La siguiente imagen muestra gráficamente cómo se evalúan estas
  expresiones y qué variables se crean en memoria. Se pueden ver
  también los distintos ámbitos locales creados en las distintas
  invocaciones a las funciones.

<img src="imagenes/clausuras.png" width="700px">


### Funciones en estructuras de datos

- Vamos a ver ejemplos que muestran que las funciones cumplen la
última condición de los objetos de primera clase: podemos incluirlas
en estructuras de datos.

----

### Construcción de listas de funciones

- Para construir una lista de funciones debemos llamar a `list` con
las funciones como parámetros

    ```racket
    (define (doble x) (+ x x))
    (define (cuadrado x) (* x x))
    (define (suma-1 x) (+ x 1))
    
    (define lista (list cuadrado suma-1 doble))
    lista
    ; ⇒ (#<procedure:cuadrado>  #<procedure:suma-1>  #<procedure:doble>)
    ```

- También podemos usar expresiones `lambda` para crear la función que
  se incluye en la lista. Por ejemplo, podemos añadir una función que
  suma 5 a un número:

    ```racket
    (define lista2 (cons (lambda (x) (+ x 5)) lista))
    lista2
    ; ⇒ (#<procedure> #<procedure:cuadrado> #<procedure:suma-1> #<procedure:doble>)
    ```

----

### Invocación a funciones de una lista

- Una vez creada una lista con funciones, ¿cómo podemos invocar a
  alguna de ellas?.
- Debemos tratarlas de la misma forma que tratamos cualquier otro dato
  guardado en la lista, las recuperamos con las funciones `first` o
  `list-ref` y las invocamos.

- Por ejemplo, para invocar a la primera función de `lista2`:

    ```racket
    ((first lista2) 10) ; ⇒ 15
    ```

----

### Ejemplo de función que trabaja con listas de funciones: `aplica-funcs`

- Veamos un ejemplo de una función `(aplica-funcs lista-funcs x)` que
  recibe una lista de funciones en el parámetro `lista-funcs` y las
  aplica todas **de derecha a izquierda** al número que pasamos en el
  parámetro `x`.

- Por ejemplo, la lista anterior con las funciones `cuadrado`, `cubo`
  y `suma-1`:

    ```racket
    (define lista (list cuadrado cubo suma-1))
    ```

    la llamada a `(aplica-funcs lista 5)` devolverá :

    ```racket
    (cuadrado (cubo (suma-1 5)) ; ⇒ 46656
    ```

- Implementación:

    ```racket
    (define (aplica-funcs lista-funcs x)
        (if (null? lista-funcs)
            x
            ((first lista-funcs)
                (aplica-funcs (rest lista-funcs) x))))
    ```

- Un ejemplo de uso:

    ```racket
    (define lista-funcs (list (lambda (x) (* x x))
                              (lambda (x) (* x x x))
                              (lambda (x) (+ x 1))))
    (aplica-funcs lista-funcs 5)
    ⇒ 46656
    ```

----

### Funciones de orden superior

!!! Hint "Definición"
    Las funciones de orden superior (*higher order functions* en inglés)
    son funciones que reciben como parámetro otras funciones.


- Llamamos funciones de orden superior (*higher order functions* en
  inglés) a las funciones que toman otras como parámetro o devuelven
  otra función. Permiten generalizar soluciones con un alto grado de
  abstracción.

- Los lenguajes de programación funcional como Scheme, Scala o Java 8
  tienen ya predefinidas algunas funciones de orden superior que
  permiten tratar listas o *streams* de una forma muy concisa y
  compacta. 
  
- Si alguna función no existe en el lenguaje, es posible
  implementarlas nosotros mismos

- Veremos:
    - `map`
    - `filter`
    - `exists?` (implementada por nosotros)
    - `for-all?` (implementada por nosotros)
    - `foldr` y `foldl`

- De alguna de las funciones veremos también su implementación
recursiva.

- Terminaremos viendo cómo la utilización de funciones de orden
superior es una excelente herramienta de la programación funcional
que permite hacer código muy conciso y expresivo.


----

### Función `map`

- La función `map` recibe otra función y una
  lista. Devuelve la lista resultante de aplicar la función
  `transforma` a todos los elementos de la lista.

    ```text
    (map transforma lista) -> lista
    ```

- La función `(transforma dato)` que usa `map` recibe como argumento
  elementos de la lista y devuelve el resultado de transformar ese
  elemento.

    ```text
    (transforma elemento) -> elemento
    ```

- Ejemplos:

    ```racket
    (map cuadrado '(1 2 3 4 5))
    ; ⇒ (1 4 9 16 25)

    (map (lambda (str) (string-append "Hola-" str)) '("me" "llamo" "Ana"))
    ; ⇒ ("Hola-me" "Hola-llamo" "Hola-Ana")

    (map (lambda (s) 
            (string-length (symbol->string s))) '(Esta es una lista de símbolos))
    ; ⇒ (4 2 3 5 2 8)
    ```

- Veamos cómo se implementa `map` de forma recursiva. Llamamos a la
  función `mi-map`.

    ```racket
    (define (mi-map f lista)
        (if (null? lista)
            '()
            (cons (f (first lista))
                  (mi-map f (rest lista)))))
    ```

- La función `map` puede recibir un número variable de listas, todas
  ellas de la misma longitud:

    ```text
    (map transforma lista_1 ... lista_n) -> lista
    ```

- En este caso la función de transforma debe recibir tantos argumentos
  como listas recibe `map`:
  
    ```text
    (transforma dato_1 ... dato_n) -> dato
    ```

- La función `map` aplica `transforma` a los elementos cogidos de las
  n listas y construye así la lista resultante:
  
    ```racket
    (map + '(1 2 3) '(10 20 30)) ; ⇒ (11 22 33)
    (map cons '(1 2 3) '(10 20 30)) ; ⇒ ((1 . 10) (2 . 20) (3 . 30))
    (map > '(12 3 40) '(20 0 10)) ; ⇒ (#f #t #t)
  
    (define (mayor a b) (if (> a b) a b))
    (define (mayor-de-tres a b c)
        (mayor a (mayor b c)))

    (map mayor-de-tres '(10 2 20 -1 34) 
                       '(2 3 12 89 0) 
                       '(100 -10 23 45 8))
    ; ⇒ (100 3 23 89 34)
    ```

!!! Hint "Consejo"
    La función `map` recibe una o más listas de *n* elementos y devuelve otra
    de *n* elementos transformados.

----

### Función `filter`

- La función `(filter predicado lista)` toma como parámetro un
  predicado y una lista y devuelve como resultado los elementos de la
  lista que cumplen el `predicado`.
  
  ```text
  (filter predicado lista) -> lista
  ```

- La función `(predicado elem)` que usa `filter` recibe elementos de
  la lista y devuelve `#t` o `#f`.

    ```text
    (predicado elem) -> boolean
    ```

- Ejemplos:

    ```racket
    (filter even? '(1 2 3 4 5 6 7 8))
    ; ⇒ (2 4 6 8)

    (filter (lambda (s) 
               (>= (string-length (symbol->string s)) 4))
               '(Esta es una lista de símbolos))
    ; ⇒ (Esta lista símbolos)

    (filter (lambda (pareja)
                (>= (car pareja) (cdr pareja))) 
                '((10 . 4) (2 . 4) (8 . 8) (10 . 20)))
    ; ⇒ ((10 . 4) (8 . 8))
    ```

- Podemos implementar `filter` de forma recursiva. Llamamos a la
  función `mi-filter`.

    ```racket
    (define (mi-filter pred lista)
      (cond
        ((null? lista) '())
        ((pred (first lista)) (cons (first lista)
                                  (mi-filter pred (rest lista))))
        (else (mi-filter pred (rest lista)))))
    ```


!!! Hint "Consejo" 
    La función `filter` recibe una lista de *n*
    elementos y una condición y devuelve otra de de *n* o menos
    elementos originales filtrados por la condición.

----

### Función `exists?` (implementada por nosotros)

- La función de orden superior `(exists? predicado lista)` recibe un
  predicado y una lista y comprueba si algún elemento de la lista
  cumple ese predicado.
  
    ```text
    (exists? predicado lista) -> boolean
    ```
  
- Igual que en `filter` el `predicado` recibe elementos de la lista y
  devuelve `#t` o `#f`.

    ```text
    (predicado elem) -> boolean
    ```

- Implementación:

    ```racket
    (define (exists? predicado lista)
      (if (null? lista)
          #f
          (or (predicado (first lista))
              (exists? predicado (rest lista)))))
    ```

- Ejemplos:

    ```racket
    (exists? even? '(1 2 3 4 5 6)) ; ⇒ #t

    (exists? (lambda (x)
                 (> x 10)) '(1 3 5 8)) ; ⇒ #f
    ```

----

### Función `for-all?` (implementada por nosotros)

- La función de orden superior `(for-all? predicado lista)` recibe un
  predicado y una lista y comprueba que todos los elementos de la
  lista cumplen ese predicado.

- Implementación:

    ```racket
    (define (for-all? predicado lista)
      (or (null? lista)
          (and (predicado (first lista))
               (for-all? predicado (rest lista)))))
    ```

- Ejemplos:

    ```racket
    (for-all? even? '(2 4 6)) ; ⇒ #t

    (for-all? (lambda (x)
                 (> x 10)) '(12 30 50 80)) ; ⇒ #t
    ```

----

### Función `foldr`

- El nombre `fold` significa *plegado*. La función `foldr`
  recorre una lista y la va "plegando", devolviendo un único valor
  como resultado.
  
    ```text
    (foldr combina base lista) -> valor
    ```
  
- El plegado lo realiza la **función de plegado** `(combina dato
  resultado)`, que recibe un dato de la lista y lo acumula con el otro
  parámetro `resultado` (al que debemos dar un valor inicial y es el
  parámetro `base` de la función `foldr`).
  
    ```text
    (combina dato resultado) -> resultado
    ```

- La función `combina` se aplica a los elementos de la lista **de
  derecha a izquierda**, empezando por el último elemento de la lista
  y el valor inicial `base` y aplicándose sucesivamente a los
  resultados que se van obteniendo.

- Veamos un ejemplo. Supongamos que la función de plegado es una
  función que suma el dato que viene de la lista con el valor
  acumulado:

    ```racket
    (define (suma dato resultado)
        (+ dato resultado))
    ```

- Llamamos a los parámetros `dato` y `resultado` para remarcar que el
  primer parámetro se va a coger de la lista y el segundo del
  resultado calculado.

- Veamos qué pasa cuando hacemos un `foldr` con esta función
  `suma` y la lista `(1 2 3)` y con el número 0 como base:
  
    ```racket
    (foldr suma 0 '(1 2 3)) ; ⇒ 6
    ```

- La función `suma` se va a ir aplicando a todos los elementos de la
  lista de **derecha a izquierda**, empezando por el valor base (0) y
  el último elemento de la lista (3) y cogiendo el resultado obtenido
  y utilizándolo como nuevo parámetro `resultado` en la siguiente
  llamada.

- En concreto, la secuencia de llamadas a la función `suma` serán las
  siguientes:

    ```racket
    (suma 3 0) ; ⇒ 3
    (suma 2 3) ; ⇒ 5
    (suma 1 5) ; ⇒ 6
    ```

- Otro ejemplo de uso:

    ```racket
    (foldr string-append "****" '("hola" "que" "tal")) 
    ; ⇒ "holaquetal****"
    ```

- En este caso la secuencia de llamadas a `string-append` que se van a
  producir son:
  
    ```racket
    (string-append "tal" "****") ; ⇒ "tal****"
    (string-append "que" "tal****") ; ⇒ "quetal****"
    (string-append "hola" "quetal****") ; ⇒ "holaquetal****"
    ```

- Otros ejemplos:

    ```racket
    (foldr (lambda (x y) (* x y)) 1 '(1 2 3 4 5 6 7 8)) ; ⇒ 40320
    (foldr cons '() '(1 2 3 4)) ; ⇒ (1 2 3 4)
    ```

- La **implementación recursiva** en Scheme de la función `foldr` es
  la siguiente:

    ```racket
    (define (mi-foldr combina base lista)
      (if (null? lista)
          base
          (combina (first lista) (mi-foldr combina base (rest lista)))))
    ```


### Función `foldl` ###

- La función `(foldl combina base lista)` (_fold left_) es similar a
`foldr` con la diferencia de que la secuencia de aplicaciones de la
función de plegado se hace **de izquierda a derecha** en lugar de
derecha a izquierda.

- El perfil de la función de plegado es el mismo que en `foldr`:

    ```text
    (combina dato resultado) -> resultado
    ```

- Por ejemplo, si la función de combinación es `string-append`:

    ```racket
    (foldl string-append "****" '("hola" "que" "tal")) 
    ; ⇒ "talquehola****"
    ```

- La secuencia de llamadas a `string-append` es:

    ```racket
    (string-append "hola" "****") ; ⇒ "hola****"
    (string-append "que" "hola****") ; ⇒ "quehola****"
    (string-append "tal" "quehola****") ; ⇒ "talquehola****"
    ```

- Otro ejemplo:

    ```racket
    (foldl cons '() '(1 2 3 4)) ; ⇒ (4 3 2 1)
    ```


- La implementación de `foldl` la veremos cuando hablemos de
  recursión por la cola (_tail recursion_) en el próximo tema.

!!! Hint "Consejo"
    Las funciones `foldr` o `foldl` reciben una lista de
    datos y devuelven un único resultado 

----

### Funciones con FOS y expresiones lambda

- Veamos por último unos ejemplos en los que definimos funciones
  que iteran sobre listas usando funciones de orden superior (FOS) y expresiones
  lambda.
  
- La iteración no se realizará mediante recursividad, sino que serán
  las FOS las que la implementen.

!!! Hint "Combinación de funciones de orden superior"
    La combinación de funciones de orden superior y expresiones lamba
    para definir funciones iterativas sobre listas es una de
    las características más potentes de la programación funcional.

----

### Función `(suma-n n lista)`

- Supongamos que queremos definir una función `(suma-n n lista)` que
  devuelve la lista resultante el resultado de sumar un número `n` a
  todos los elementos de una lista.

- Podemos hacerlo de forma recursiva:

    ```racket
    (define (suma-n n lista)
        (if (null? lista)
            '()
            (cons (+ (first lista) n)
                  (suma-n n (rest lista)))))
    ```

- Funciona de la siguiente manera:

    ```racket
    (suma-n 10 '(1 2 3 4))
    ; ⇒ (11 12 13 14)
    ```

- ¿Podemos implementar `suma-n` usando una llamada a `map`?

<p style="margin-bottom:3cm;"></p>

- Sí, pasándole a map una función construida con una expresión lambda
  en la que se usa el parámetro `n`:

    ```racket
    (define (suma-n n lista)
        (map (lambda (x) (+ x n)) lista))
    ```

- Otro ejemplo, la función `suma-parejas`:

    ```racket
    (define (suma-parejas lista-parejas)
        (foldr (lambda (pareja resultado)
                   (+ (car pareja) (cdr pareja) resultado)) 0 lista-parejas))

    (suma-parejas (list (cons 3 6) (cons 2 9) (cons -1 8) (cons 9 3))) ; ⇒ 39
    ```

----


### Composición de funciones de orden superior

- En la composición de funciones de orden superior, la lista 
resultante de la salida de una función se utiliza como entrada de la
siguiente. 


- Supongamos que queremos implementar una función que sume un número
`n` a todos los elementos de una lista (igual que la anterior) y
después que sume todos los elementos resultantes.

- ¿Cómo lo haríamos? (podemos reutilizar el código del ejemplo anterior)

<p style="margin-bottom:3cm;"></p>

- Solución:

    ```racket
    (define (suma-n-total n lista)
       (foldr + 0
           (map (lambda (x) (+ x n)) lista)))
    ```

    ```racket
    (suma-n-total 100 '(1 2 3 4)) ; ⇒ 410
    ```

- Otro ejemplo: queremos contar aquellas parejas cuya suma de ambos números
es mayor que un umbral (por ejemplo, 10).

    ```racket
    (define lista-parejas (list (cons 1 2) 
                                (cons 3 8) 
                                (cons 2 3) 
                                (cons 9 6)))
    (cuenta-mayores-que 10 lista-parejas) ; ⇒ 2
    ```

- ¿Cómo se implementaría componiendo funciones de orden superior?:

<p style="margin-bottom:3cm;"></p>

- Solución:

    ```racket
    (define (cuenta-mayores-que n lista-parejas)
      (length
       (filter (lambda (x)
                 (> x n)) (map (lambda (pareja)
                                 (+ (car pareja) (cdr pareja))) lista-parejas))))
    ```								 

----

### Función `(contienen-letra caracter lista-pal)`

- Queremos definir la función `(contienen-letra
  caracter lista-pal)` que devuelve las palabras de una lista que
  contienen un determinado carácter, usando la función `filter` y
  alguna función auxiliar

- Por ejemplo:

    ```racket
    (contienen-letra #\a '("En" "un" "lugar" "de" "la" "Mancha"))
    ; ⇒ ("lugar" "la" "Mancha")
    ```

- Necesitamos el predicado auxiliar `(letra-en-pal? caracter pal)` que
  comprueba si una cadena contiene un carácter. Por ejemplo:

    ```racket
    (letra-en-pal? #\a "Hola") ; ⇒ #t
    (letra-en-pal? #\a "Pepe") ; ⇒ #f
    ```

- ¿Lo podemos implementar obteniendo una lista de caracteres a partir
  de la cadena y usando la función `exists?`?

<p style="margin-bottom:3cm;"></p>

- Solución:

    ```racket
    (define (letra-en-pal? caracter palabra)
        (exists? (lambda (c) 
                    (equal? c caracter)) (string->list palabra)))
    ```

- Ahora ya podemos implementar `contienen-letra` usando otra vez la
  función de orden superior `filter` y la función anterior en la
  expresión lambda que hace el filtrado:

    ```racket
    (define (contienen-letra caracter lista-pal)
       (filter (lambda (pal)
                  (letra-en-pal? caracter pal)) lista-pal))
    ```


