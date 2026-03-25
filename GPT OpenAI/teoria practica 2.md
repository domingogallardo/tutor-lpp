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
