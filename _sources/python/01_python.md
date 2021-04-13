---
jupytext:
  cell_metadata_filter: hide-input, hide-output, hide-cell
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.10.3
kernelspec:
  display_name: book
  language: python
  name: book
---

# Parte 1

## Operadores

### Operadores aritméticos

Una forma fácil de empezar es [usando Python como una calculadora](https://docs.python.org/3/tutorial/introduction.html#using-python-as-a-calculator).

A excepción de la exponenciación, que en otros lenguajes se usa el símbolo `^`, los operadores aritméticos son los estándar que se usan en otros lenguajes de progración, o fórmulas de Excel:

```python
+: suma
-: resta
*: multiplicación
/: división
**: exponenciación
```

Por ejemplo:

```{code-cell}
:tags: []

7 / 2
```

Otros operadores aritméticos que pueden ser de utilidad son:

```python
//: división entera
%: módulo ó resto de la división entera
@: multiplicación matricial
```

Por ejemplo, "7 dividido 2 es 3 y el resto es 1":

```{code-cell}
:tags: []

7 // 2
```

```{code-cell}
:tags: []

7 % 2
```

En particular, el módulo es útil para chequear si un número es divisible por otro, ya que su módulo tiene que ser 0.

+++

### Operadores de comparación

Los operadores de comparación son:

```python
>: mayor
<: menor
>=: mayor o igual
<=: menor o igual
==: igual
!=: distinto
```

y devuelven `True` o `False`, un tipo de dato llamado `bool`eano.

```{code-cell}
:tags: []

5 > 3
```

```{code-cell}
:tags: []

2 + 2 == 5  # Es equivalente a (2 + 2) == 5
```

Noten que para chequear igualdad hay que poner doble `=`.

Si ponemos un único igual, nos va a *arrojar* un error:

```{code-cell}
:tags: [raises-exception]

4 = 5
```

Es importante aprender a leer el error, porque nos da pistas de como resolverlo. O, al menos, para pedir ayuda si no lo podemos resolver.

Nos dice que es un `SyntaxError` (error de sintaxis), porque no se puede *asignar* a un *literal*, y nos marca en qué línea sucedió el error.

Al escribir `4 = 5`, estamos tratando de redefinir el `4` como `5`, porque el `=` se utiliza para realizar asignaciones.

+++

## Asignación de variables

En Python, **todo es un objeto**. Objeto no es sinónimo de "cosa", sino que tiene un significado particular en computación, en el cual no vamos a profundizar en esta introducción. Como veremos más adelante, hay distintos tipos de objetos, con distintas propiedades y funcionalidades. Por ahora, sigamos pensando en números, que son los únicos objetos que vimos.

Como bien explica [esta presentación](https://www.youtube.com/watch?v=_AEJHKGk9ns), asignar una variable es simplemente **darle un nombre a un objeto**. Generalmente, se dice (y diremos) que se *guarda* un objeto en una variable.

Casi cualquier palabra es un [nombre válido para una variable](https://docs.python.org/3/reference/lexical_analysis.html#identifiers), aunque hay [ciertas palabras que están reservadas](https://docs.python.org/3/reference/lexical_analysis.html#keywords) ya que corresponden a *comandos*. Lo ideal es ponerle un nombre bien descriptivo, que *documente* que es lo que está *guardado* ahí. Por ejemplo, si la variable guarda una longitud, llámenla `longitud` y no `x`. Es importante para que se pueda entender más fácilmente qué está haciendo el código, sobretodo al leerlo más adelante.

Por ahora, vamos a ignorar nuestro consejo y usar `x`:

```{code-cell}
:tags: [raises-exception]

x
```

Nos *arrojó* un error. Claro, no *guardamos* nada en `x` aún:

```{code-cell}
:tags: []

x = 3
```

Noten que al asignar una variable, no *devuelve* nada. Si queremos ver que está guardado en `x`, podemos poner simplemente `x` en una celda:

```{code-cell}
:tags: []

x
```

o, también, podemos usar la función `print`:

```{code-cell}
:tags: []

print(x)
```

Para hacer más *legible* el código, es importante ir guardando resultados intermedios en distintas variables.

Por ejemplo, ahora podemos usar este *resultado intermedio* en otras operaciones:

```{code-cell}
2 * x
```

que, a su vez, podriamos guardarlo en otra variable:

```{code-cell}
:tags: []

y = 2 * x

y
```

Al principio, algo potencialmente confuso es que se puede hacer esto:

```{code-cell}
x = x + 1
```

¿Cuánto vale `x` ahora?

```{code-cell}
:tags: []

x
```

Si corrimos la celda una única vez, lo que pasó fue lo siguiente:

1. Al empezar, `x` es 3
2. Le pedimos que *corra*: `x = x + 1`
3. Se reemplazan las variables a la derecha del `=`: `x + 1` -> `3 + 1`
4. Se calcula el resultado: `3 + 1` -> `4`
4. Se *guarda* el resultado: `x = 4`

Reiterando, el `=` no representa una igualdad, sino una asignación.

### Asignación multiple

Para asignar multiples variables a la vez, se puede hacer una asignación por linea:

```{code-cell}
:tags: []

x = 1
y = 2
```

o, todo en una línea, separandolas por comas:

```{code-cell}
:tags: []

x, y = 1, 2
```

- A la derecha del igual, se esta usando una tupla (`tuple`), un conjunto ordenado de objetos, que introduciremos más adelante.
- A la izquierda del igual, se usa lo que se llama `tuple unpacking`, que no vamos a entrar en detalle en esta introducción a Python, pero sí lo vamos a usar.

En principio, ambas maneras son equivalentes. Pero, desde el punto de hacer más legible el código, la segunda da a entender que `x` e `y` están relacionados, por ejemplo, que son las coordenadas de un punto $(x, y)$.

+++ {"tags": []}

De la misma manera, se puede mostrar el resultado de más de una variable con una tupla:

```{code-cell}
:tags: []

x, y
```

pero no poniéndolas en distintas lineas:

```{code-cell}
:tags: []

x
y
```

ya que solo se nos muestra el resultado de la última linea, si no es una asignación.

En cambio, sí funciona con `print`:

```{code-cell}
:tags: []

print(x)
print(y)
```

## Ejercicio 1

Calcule las raíces del polinomio $2x^2 - 10x + 8$.

**Ayuda:**

- Para un polinomio de la forma $ax^2 + bx + c$, las raices $x_1$ y $x_2$ vienen dadas por:

$$ x_{1, 2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}$$

- Para calcular la raiz, se puede hacer una exponenciación: $\sqrt{x} = x^{1/2}$

- Las raíces son $x=1$ y $x=4$.

```{code-cell}
# Complete el código aquí
```

### Solución

```{code-cell}
---
jupyter:
  source_hidden: true
tags: [hide-input]
---
a, b, c = 2, -10, 8

disc = (b ** 2 - 4 * a * c) ** (1 / 2)
raiz_1 = (-b + disc) / (2 * a)
raiz_2 = (-b - disc) / (2 * a)

raiz_1, raiz_2
```

Aunque hay distintas formas de escribir la solución, pero quiero resaltar lo siguiente de esta solución:

1. Por empezar, se asignaron los coeficientes del polinomio a distintas variables. Una mala práctica en programación es *[hardcodear](https://en.wikipedia.org/wiki/Hard_coding)* valores en el código. Por ejemplo, si hubiesemos puesto directamente los coeficientes en la fórmula de las raíces. Si después quisieramos usar el código para otro polinomio, tendríamos que cambiar todos los lugares donde aparecen `a`, `b` y `c`, en lugar de cambiarlos en un único lugar al inicio.

1. Las variables de entrada (`a`, `b` y `c`) se podrían haber asignado en lineas separadas. Pero asignarlas en una sola linea da a entender que *están relacionadas*. En este caso, son los coeficientes del mismo polinomio.

1. En lugar de llamar a las raices del polinomio `x1` y `x2`, las llamamos con un nombre más descriptivo `raiz_1` y `raiz_2`.

1. El uso de la variable intermedia `disc`, el *discriminante* de la cuadrática, que hace el código más legible. Pero no solo eso: si el *choclo* que es `disc` se repitiera dos veces, en `raiz_1` y `raiz_2`, también podría dar lugar a errores, por ejemplo, al poner mal un signo en una de las fórmulas.

+++

## Tipos de objetos

Como mencionamos antes, en Python, **todo es un objeto**. Por ahora, solo nos va a importar que hay distintos tipos de objetos, y que se comportan de manera diferente.

Para saber el tipo de un objeto, hay que usar la función `type`. Por ejemplo, el tipo del número `2` es:

```{code-cell}
:tags: []

type(2)
```

Algunos tipos de objetos básicos son estos:

| Tipo de objeto | Significado | Ejemplo |
| :-: | :-: | :-: |
| int | número entero | `2` |
| float | número de punto flotante | `1.5` |
| str | cadena de texto | `"hola"` |
| bool | booleano | `True` |
| NoneType | ? | `None` |
| tuple | tupla | `(1.0, "dos", 42, True)` |
| list | lista | `[1.0, "dos", 42, True]` |
| dict | diccionario | `{"uno": 1, "dos": 2}` |

Pueden notar que hay dos tipos de números: los enteros (`int`) y los de [punto flotante](https://en.wikipedia.org/wiki/Floating-point_arithmetic) (`float`), que permiten representar números no enteros, un "número con decimales".

Por ejemplo, si sumamos dos `int`, obtenemos otro `int`:

```{code-cell}
:tags: []

x = 2 + 2

x, type(x)
```

Pero si dividimos dos `int`, obtenemos un `float`:

```{code-cell}
x = 8 / 2

x, type(x)
```

Incluso si el resultado pudiese ser representado por un entero. Python no sabe a priori que va a dar, así que convierte los números a `float` antes de hacer la división.

Por ahora, los usamos indistintamente, pero la diferencia es importante por (al menos) dos razones:

1. Hay ciertos lugares donde Python requiere que se utilize un `int`. Siempre podemos convertir un `float` en un `int` de la siguiente manera:

```{code-cell}
:tags: []

int(4.0)
```

2. Hay que tener cuidado al comparar `float`s:

```{code-cell}
:tags: []

x = 0.1 + 0.2

x == 0.3
```

porque `x` es:

```{code-cell}
:tags: []

x
```

*Extra: [cómic al respecto en SMBC Comics](https://www.smbc-comics.com/comic/2013-06-05).*

Para comparar `float`s, hay que elegir una tolerancia, por ejemplo, $10^{-15}$, chequear si se encuentran a menos de esa distancia: $|x-y| < 10^{-15}$

```{code-cell}
:tags: []

abs(x - 0.3) < 1e-15
```

## Cadenas de texto

Las cadenas de texto, o *strings*, son el tipo de objeto que Python usa para texto. Nos van a servir para decirle a Python, por ejemplo, el nombre de un archivo, o darle el texto para poner en los ejes de un gráfico.

Se pueden definir tanto comillas simples como dobles: `'hola'` o `"hola"`. También esta la opción de triple comilla, que sirve para texto de multiples renglones:

```{code-cell}
:tags: []

"""Este es un
string de
multiples
renglones."""
```

Noten que divide los renglones con un `\n`, que es el código que se usa para señalar que comienza una nueva linea.

Python interpreta la suma entre `str` como concatenación:

```{code-cell}
"hola" + "mundo"
```

Incluso si son números:

```{code-cell}
"2" + "2"
```

A diferencia de *cierto otro lenguaje que no vamos a nombrar*, Python arroja un error de tipo (`TypeError`) cuando se quieren sumar números y *strings*:

```{code-cell}
:tags: [raises-exception]

2 + "2"
```

porque no sabe si queremos de resultado `4` o `"22"` y, ante la duda, prefiere no adivinar.

+++

### f-strings

Hay diversas maneras de insertar variables dentro de *strings*, pero la más legible (y por lo tanto, recomendada) es la de los `f-strings`, que consiste en poner una `f` antes de abrir comillas y poner las variables encerradas en llaves `{}`. Por ejemplo:

```{code-cell}
x = 42
```

```{code-cell}
"La respuesta es x"
```

```{code-cell}
:tags: []

f"La respuesta es {x}"
```

Se puede especificar el formato en el que convierte la variable a texto, por ejemplo, para redondear hasta determinado número de decimales:

```{code-cell}
:tags: []

pi = 3.141592

f"Pi = {pi:.2f}"
```

Pueden ver en la [documentación](https://docs.python.org/3/library/string.html#formatspec), si quieren ver todas las opciones disponibles.

+++

## Funciones

Las funciones son bloques de código que reciben párametros, realizan una serie de acciones, y devuelven un resultado.

Es más fácil entenderlo con un ejemplo simple. Definamos una función para calcular el largo de un vector:

```{code-cell}
:tags: []

def norma_vector(x, y):
    """Calcula la norma euclídea del vector (x, y)"""
    r2 = x ** 2 + y ** 2
    return r2 ** (1 / 2)
```

Ahora tenemos una variable llamada `norma_vector` que *apunta* a la función:

```{code-cell}
:tags: []

norma_vector
```

Y podemos *llamar* a la función pasandole los argumentos entre paréntesis:

```{code-cell}
:tags: []

norma_vector(3, 4)
```

Sobre la definición de una función, hay varios puntos a resaltar:

1. La *indentación*, es decir, el espacio en blanco que hay al principio de cada linea dentro del bloque que define la función. Python utiliza este espacio en blanco para delimitar bloques y saber dónde termina la función. Por convención, se usan 4 espacios en blanco, y las IDEs, como Jupyter, insertan 4 espacios al presionar `Tab`.

2. El `return`, que es lo que va a devolver la función. Esta termina cuando llega a un `return`. Si no hay ninguno, termina cuando llega al final del bloque y devuelve implicitamente un `None`.

3. El nombre, al igual que las variables, tiene que ser descriptivo, para poder saber que hace la función sin tener que ir a leer su código.

4. El *docstring*, o *string* de documentación, que es la primer linea dentro del bloque de la función. Describe brevemente que hace la función, que parámetros toma y que devuelve. Se puede acceder a ellas con la función `help`:

```{code-cell}
:tags: []

help(norma_vector)
```

También, según que IDE estén usando, hay otras maneras de mostrar la ayuda. Por ejemplo, en Jupyter es `Shift + Tab`.

+++

### Formas de llamar funciones

+++

Hay diferentes maneras de llamar a la función. En general, se puede pasar los argumentos por posición (como hicimos antes), por nombre, o una mezcla de ambos:

```python
norma_vector(3, 4)      # por posición

norma_vector(x=3, y=4)  # por nombre o keyword
norma_vector(y=4, x=3)  # no hace falta respetar el orden

norma_vector(3, y=4)    # mixto
```

Todas estas formas de llamar la función son válidas y dan el mismo resultado.

En cambio, nos va a tirar un error si nos olvidamos de un parametro:

```{code-cell}
:tags: [raises-exception]

norma_vector(1)
```

O si ponemos argumentos posicionales despues de los que son por nombre:

```{code-cell}
:tags: [raises-exception]

norma_vector(y=2, 1)
```

### Más formas de definir funciones

Hay más formas de definir funciones:

- funciones con valores por defecto para ciertos paramétros
- que acepten una cantidad variable de parámetros (posicionales, por nombre, o ambos)
- que limiten ciertos parárametros a ser solo posicionales, o solo por nombre
- funciones "anónimas", con el comando `lambda`

Para definir parámetros por defecto, se *asigna* un valor en la definición de la función:

```python
def funcion(x, y=1):
    ...
```

Veamos una función que ya usamos y define variables por defecto:

```{code-cell}
:tags: []

help(print)
```

`print` tiene ciertos parametros que controlan cómo y a dónde *imprime*. Por defecto, agrega una nueva linea, `"\n"`, al final de lo que imprime:

```{code-cell}
:tags: []

print(1)
print(2)
```

Pero si queremos poner otro valor, solo tenemos que pasarle ese parámetro por nombre, sin tener que pasarle el resto de los parámetros:

```{code-cell}
:tags: []

print(1, end=" -> ")
print(2)
```

### Ejercicio 2

Encapsule en una función el código para calcular las raices de la cuadrática y vuelva a calcular las raíces del polinomio $2x^2 - 10x + 8$.

```{code-cell}
:tags: []

# Complete el código aquí
```

#### Solución

```{code-cell}
---
jupyter:
  source_hidden: true
tags: [hide-input]
---
def raices_cuadratica(a, b, c):
    """Calcula las raices de un polinomio cuadratico ax^2 + bx + c."""
    disc = (b ** 2 - 4 * a * c) ** (1 / 2)
    raiz_1 = (-b + disc) / (2 * a)
    raiz_2 = (-b - disc) / (2 * a)
    return raiz_1, raiz_2


raices_cuadratica(2, -10, 8)
```

+++ {"tags": []}

Fijense la importancia del *docstring*, que nos dice cuál es la relación entre los parámetros y el polinomio. Si no, cada vez que quisieramos usar la función tendriamos que ir a ver el código de la función (y entenderlo) para ver si `a` corresponde al término cuadrático o constante.

### ¿Cuándo definir funciones?

Definir funciones tiene múltiples ventajas en términos de estructurar nuestro código de manera que sea fácil de usar y entender. Sin embargo, puede no estar tan claro que código debería estar definido en una función. Para ello, sirve discutir algunos conceptos importantes en computación: reusabilidad, mantenibilidad, modularidad y abstracción.

Para empezar, las funciones nos permiten *reusar* código. Si un bloque de código se repite múltiples veces, podemos "sacar factor común" y definir una función en su lugar. Por ejemplo, si queremos calcular las raices de multiples polinomios, podemos reusar la función que ya definimos:

```{code-cell}
:tags: []

raices_1 = raices_cuadratica(1, 0, -1)
raices_2 = raices_cuadratica(1, 0, -4)
```

Pero no repetir código no es (solo) de *vago*, sino que también ayuda en el *mantenimiento* del código. Por ejemplo, si encontramos un error en nuestra función, solo tenemos que arreglarlo en un lugar.

Por otro lado, las funciones nos permiten *abstraer* el código al reemplazar múltiples lineas de código por un *llamado* a la función. Por ejemplo, nos abstraen del detalle de cómo se calculan las raíces de un polinomio. Esto nos permite **razonar más fácilmente** sobre que hace el programa, ya que no vemos el detalle paso a paso, sino lo que entra y lo que sale.

+++ {"tags": []}

![](bart.png)

+++

¿Pero cuál es el nivel de abstracción *correcta*?

Supongamos que queremos hacer un programa que calcule las raíces de un polinomio y las grafique. Podríamos dividir dicho programa en 3 pasos:

1. Calcular el discriminante.
2. Calcular las raíces.
3. Graficar las raíces.

En un extremo, podríamos encapsular todo en una única función. Pero si alguien quisiera graficar las raíces de una manera distinta, no podría reutilizar nuestro código para calcular las raíces, porque estaría todo acoplado.

En el otro extremo, cada paso podría ser una función separada. Pero, ¿tiene algún sentido separar el cálculo del discriminante del de las raíces? ¿Tiene algún otro uso el discriminante?

En este ejemplo, el nivel de abstracción correcto parecería ser agrupar los pasos 1 y 2 en una función, y el paso 3 en otra función.

+++

Otro beneficio de las funciones es que encapsulan código y nos salvan de *pisar* o sobreeescribir variables que definimos previamente. Mientras que una función puede acceder a una variable externa a la función:

```{code-cell}
:tags: []

variable_externa = 1
dos = 2


def suma_variable_externa_a(parametro_interno):
    dos = 10
    variable_interna = 42
    return parametro_interno + variable_externa


suma_variable_externa_a(10)
```

no modifica las variables externas:

```{code-cell}
:tags: []

dos
```

Además, las variables internas y los parámetros de la función no son accesibles desde el exterior:

```{code-cell}
:tags: [raises-exception]

variable_interna
```

Sin embargo, este tipo de funciones que utilizan **variables externas o *globales* hacen más dificil razonar sobre el código**. Si volvemos a usar la función `suma_variable_externa_a(10)`, no es claro si va a dar el mismo resultado que antes, a pesar de que le estamos pasando el mismo argumento: alguien podría haber modificado el valor de `variable_externa` en el medio.

Un paradigma de programación, llamado [programación funcional](https://en.wikipedia.org/wiki/Functional_programming), propone diferenciar *procedimientos* o *subrutinas* de *funciones puras o determinísticas*, siendo estas últimas las **funciones cuyo resultado sólo depende de los parámetros de entrada**.

+++

### Métodos

Los métodos son funciones que están asociadas a un objeto. La sintaxis para acceder a ellos es poner un punto después del objeto. Por ejemplo, el método `str.upper` sirve para convertir un *string* en mayúsculas o *uppercase*:

```{code-cell}
:tags: []

x = "hola"

x.upper()
```

La ventaja frente a funciones es que, al estar asociadas a un (tipo de) objeto, no podemos usarlas para un tipo de dato.

Por ejemplo, imaginemos que definimos una función que transforma un número decimal en una fracción:

```python
def numero_a_fraccion(x):
    # MAGIA
    return fraccion
```

tal que si le pasamos `0.25`, nos devuelve `1/4`.

¿Pero que pasa si le pasamos un string: `numero_a_fraccion("hola")`?

Tendría que arrojar un error. Pero, dependiendo de como la hayamos programado, podría dar un resultado (equivocado).

En cambio, si fuese un método de los números, no podríamos equivocarnos y pasarle un tipo de dato equivocado. La función ya está asociada a un número.

En particular, esa método ya existe, y se llama `as_integer_ratio`:

```{code-cell}
(0.25).as_integer_ratio()
```

Pero si tratamos de usarlo en un `str`, nos dice que no existe:

```{code-cell}
:tags: [raises-exception]

"hola".as_integer_ratio()
```

## Estructuras de datos: tuplas y listas

En Python, hay diversas estructuras de datos que nos permiten manejar conjuntos de objetos de manera más cómoda. Las más fundamentales son las tuplas (`tuple`), listas (`list`) y diccionarios (`dict`).

La tupla y la lista son similares entre sí: ambas *guardan* una secuencia de objetos, es decir, un conjunto ordenado de objetos. La sintaxis para definirlas también es similar: se separa un grupo de objetos por comas, y se los encierra entre paréntesis (tuplas) o corchetes (listas).

```{code-cell}
:tags: []

mi_tupla = ("hola", 42, True, "último")
mi_lista = ["hola", 42, True, "último"]
```

Como vimos antes, en la tupla se puede omitir el uso de paréntesis.

Conceptualmente, es como haber definido 4 variables, $\{x_0, x_1, x_2, x_3\}$:

```python
x_0 = "hola"
x_1 = 42
x_2 = True
x_3 = "último"
```

Pero, en lugar de tener 4 nombres distintos, tenemos un único nombre con una notación especial para acceder a cada variable.

+++

### Indexing

+++

En ambos casos, podemos acceder a los elementos por su ubicación o índice. Siguendo la práctica de muchos lenguajes, Python empieza a [contar desde el 0](https://www.cs.utexas.edu/users/EWD/transcriptions/EWD08xx/EWD831.html):

```{code-cell}
:tags: []

mi_tupla[0]  # El primer elemento
```

```{code-cell}
:tags: []

mi_tupla[1]  # El segundo elemento
```

Como mencionamos antes, hay ciertos lugares donde Python requiere el uso de números enteros (`int`). Este es uno de esos lugares, porque no tendría sentido pedir el elemento 0.5. Si usamos un `float`, nos arroja un error:

```{code-cell}
:tags: [raises-exception]

mi_tupla[1.0]
```

Para acceder al último elemento, se podría hacer lo siguiente. Primero, obtenemos el largo $N$ de una secuencia con la función `len`:

```{code-cell}
:tags: []

len(mi_tupla)
```

y, luego, usamos dicho valor como índice:

```{code-cell}
:tags: [raises-exception]

mi_tupla[len(mi_tupla)]
```

que nos arroja un `IndexError`... Claro, si Python empieza a contar desde $0$, el índice del último elemento es $N-1$, no $N$:

```{code-cell}
:tags: []

mi_tupla[len(mi_tupla) - 1]
```

Sin embargo, hacer esto es un *anti-pattern*. Hay una manera más compacta y legible de acceder a los últimos elementos: Python cuenta los elementos desde el final usando números negativos.

```{code-cell}
:tags: []

mi_tupla[-1]  # El último elemento
```

```{code-cell}
:tags: []

mi_tupla[-2]  # El anteúltimo elemento
```

### Slicing

+++

Un `slice` nos permite acceder a un subconjunto de una secuencia. La notación es

```python
x[start:stop:step]
```

que devuelve todos los elementos entre `start` (inclusivo) hasta `stop` (exclusivo) separados por `step` elementos.

```{code-cell}
:tags: []

mi_tupla[1:4:2]  # elementos del 1 al 4 cada 2
# es decir, los elementos 1 y 3
```

Si no ponemos explicitamente alguno de estos valores, por default son:

```python
start = 0
stop = -1
step = 1
```

Es decir, `x[::] == x[0:-1:1]`

Por ejemplo:

```{code-cell}
:tags: []

mi_tupla[1:]  # desde el elemento 1: indices (1, 2, 3)
```

```{code-cell}
:tags: []

mi_tupla[:3]  # hasta el tercer elemento: indices (0, 1 y 2)
```

```{code-cell}
:tags: []

mi_tupla[1::2]  # los elementos impares: indices (1, 3)
```

```{code-cell}
:tags: []

mi_tupla[::-1]  # los elementos en orden inverso: (3, 2, 1, 0)
```

### Mutabilidad

La diferencia fundamental entre tuplas y listas radica en este concepto: las tuplas son inmutables, es decir, no se pueden modificar, mientras que las listas sí.

Para modificar un elemento, accedemos a él y le asignamos un nuevo valor:

```{code-cell}
:tags: []

print("  Antes:", mi_lista)

mi_lista[1] = 84

print("Después:", mi_lista)
```

En cambio, si queremos modificar una tupla, nos arroja un `TypeError`:

```{code-cell}
:tags: [raises-exception]

mi_tupla[1] = 84
```

Además, a las listas se le pueden agregar, quitar o reordenar sus elementos. Pueden ver los métodos de una lista en la [documentación](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists). Por ejemplo, para agregar un elemento al final de la lista, podemos usar el método `append`:

```{code-cell}
mi_lista.append(35)
```

que no devuelve nada (o, técnicamente, devuelve `None`). Como vemos, agregó el elemento `35` al final:

```{code-cell}
:tags: []

mi_lista
```

### Ejercicio 3

Corrija el siguiente código para que imprima lo que especifica cada *string*:

```{code-cell}
:tags: []

x = [0, 1, 2, 3, 4, 5, 6, 7, 8]

print("     Quinto elemento:", x)
print("Primeros 4 elementos:", x)
print(" Últimos 4 elementos:", x)
print("     Elementos pares:", x)
print("   Elementos impares:", x)
print("    En orden inverso:", x)
```

#### Solución

```{code-cell}
---
jupyter:
  source_hidden: true
tags: [hide-input]
---
x = [0, 1, 2, 3, 4, 5, 6, 7, 8]

print("     Quinto elemento:", x[4])
print("Primeros 4 elementos:", x[:4])
print(" Últimos 4 elementos:", x[-4:])
print("     Elementos pares:", x[::2])
print("   Elementos impares:", x[1::2])
print("    En orden inverso:", x[::-1])
```

## Modulos y paquetes

Así como las funciones permiten reutilizar código, el siguiente nivel son los módulos y paquetes, que permiten **reutilizar funciones y tipos de datos** en otros programas. En su versión más simple, los módulos son simplemente archivos de texto con extensión `.py`, y los paquetes son conjuntos de módulos.

Python viene con un montón de [módulos pre-incluidos](https://docs.python.org/3/py-modindex.html), por ejemplo, el módulo `math`. Para poder usar módulos, primero hay que importarlos con el comando `import` seguido del nombre del módulo:

```{code-cell}
:tags: []

import math
```

Al correr esa linea, Python busca el módulo, lo corre y lo asigna a la variable `math`:

```{code-cell}
:tags: []

math
```

Ahora, podemos acceder a las cosas que están definidas dentro de `math` usando notación de punto. Por ejemplo, `math` define la constante $\pi$:

```{code-cell}
:tags: []

math.pi
```

o funciones trigonométricas como el coseno:

```{code-cell}
:tags: []

math.cos(math.pi)
```

Sin embargo, no vamos a usar el módulo `math` para hacer cálculos matemáticos, sino que utilizaremos un paquete externo llamado NumPy.

El mundo de Python está lleno de paquetes que ya tienen la solución a casi todos nuestros problemas. Los más usados en el ambiente científico son:

- [numpy](https://numpy.org/): define el tipo de dato `ndarray`, o simplemente *array*. Representa vectores o matrices, y nos permite hacer operaciones matemáticas sobre ellos de manera rápida y simple. Es la base de (casi) todo lo que es cálculo númerico.
- [matplotlib](https://matplotlib.org): para realizar gráficos y visualizaciones de diverso tipo.
- [scipy](https://scipy.org/): compuesto de varios *subpaquetes*, cada uno especializado en diversas areas del cálculo numérico, como algebra lineal, integración numérica, optimización, estadística, análisis de imagenes, entre otros.

Otros muy conocidos son:

- **pandas y xarray**: DataFrames, o un "*Excel* avanzado".
- **seaborn**: gráficos y visualizaciones, basado en matplotlib
- **statsmodels**: estadística
- **sympy**: cálculo simbólico
- **pint**: unidades
- **PyVISA**: control de instrumentos
- **networkx**: redes o gráfos
- **scikit-image**: análisis de imagenes
- **scikit-learn**: machine learning
- **Keras**, **TensorFlow**, **PyTorch**: redes neuronales

Si instalaron Anaconda, muchos de estos paquetes externos vienen pre-instalados.

+++

## NumPy

NumPy, que viene de *Numerical Python*, es el paquete estándar en todo lo que es cálculo numérico. Para una introducción más completa a NumPy, pueden ir a la [documentación](https://numpy.org/doc/stable/user/absolute_beginners.html).

Para importar `numpy`, vamos a usar una variante del comando `import`, para asignarle un alias más corto:

```{code-cell}
:tags: []

import numpy as np
```

Ahora, tenemos una variable `np` que apunta al paquete `numpy`:

```{code-cell}
:tags: []

np
```

Es una convención muy difundida importar a `numpy` como `np`.

+++

### Array

+++

NumPy define una estructura de dato llamada `array`, que tiene similitudes a la tupla y lista. Los arrays de NumPy muestran sus ventajas cuando son utilizados para números. Permiten realizar operaciones matemáticas de manera mucho más simple y rápida, por lo que es **crucial** para lo que es cálculo numérico.

Para crear un *array*, se puede pasar una tupla o lista a la función `np.array`:

```{code-cell}
:tags: []

np.array([4, 8, 15, 16, 23, 42])  # vector o array 1D
```

Para crear *arrays* multidimensionales, como matrices, se puede pasar una lista de listas, o listas anidadas:

```{code-cell}
:tags: []

np.array([[1, 2, 3], [4, 5, 6]])  # matriz o array 2D
```

NumPy incluye algunas funciones cómodas para crear *arrays* comúnmente utilizados, como *arrays* con un mismo valor repetido:

```{code-cell}
:tags: []

np.full(5, 42)  # np.full(shape=5, fill_value=42)
```

```{code-cell}
:tags: []

np.zeros((2, 3))  # np.zeros(shape=(2, 3))
```

O de números equiespaciados:

```{code-cell}
:tags: []

np.arange(3, 11, 2)  # np.arange(start=3, stop=11, step=2)
```

```{code-cell}
:tags: []

np.linspace(0, 1, 11)  # np.linspace(start=0, stop=1, num=11)
```

### Propiedades: shape, size, ndim

Al igual que las listas, para un *array* unidimensional, podemos usar la función `len` para conocer la cantidad de elementos que contiene.

```{code-cell}
:tags: []

len(np.array([1, 2, 3]))
```

Pero, a diferencia de las listas, los *arrays* pueden ser multidimensionales. En ese caso, necesitamos más de un número para describir su forma. El `array` tiene tres atributos que describen su tamaño:

1. `shape`: tupla con la cantidad de elementos en cada dimensión
2. `size`: cantidad de elementos totales
3. `ndim`: cantidad de dimensiones

```{code-cell}
:tags: []

x = np.array([[1, 2], [3, 4], [5, 6]])

print("shape =", x.shape)
print(" size =", x.size)
print(" ndim =", x.ndim)
```

En este caso, la función `len` devuelve el largo de la primera dimensión, como si fuese una lista de listas.

```{code-cell}
:tags: []

len(x)
```

El array incluye métodos para [cambiar su forma](https://numpy.org/doc/stable/user/absolute_beginners.html#transposing-and-reshaping-a-matrix), o [aplanarse](https://numpy.org/doc/stable/user/absolute_beginners.html#reshaping-and-flattening-multidimensional-arrays).

+++

### Indexing y slicing

Al igual que las listas, se puede acceder a los elementos de un array por índice o por *slice*. Pero, se extiende la notación en el caso de *arrays* multidimensionales:

```{code-cell}
:tags: []

x = np.array([[1, 2, 3], [4, 5, 6]])
x
```

```{code-cell}
:tags: []

x[1, 2]  # Fila 1, columna 2
```

```{code-cell}
:tags: []

x[0]  # Fila 0
```

```{code-cell}
:tags: []

x[:, 0]  # Columna 0
```

### Operaciones matemáticas y broadcasting

Este es el punto donde brillan los *arrays*. Mientras que sumar dos listas las concatena:

```{code-cell}
:tags: []

[1, 2, 3] + [10, 20, 30]
```

las operaciones entre *arrays* se hacen elemento a elemento:

```{code-cell}
:tags: []

np.array([1, 2, 3]) + np.array([10, 20, 30])
```

Supongamos que queremos dividir todos los elementos de un array por 2. Es tan simple como:

```{code-cell}
:tags: []

np.array([2, 4, 6]) / 2
```

Lo que sucede se conoce como [*broadcasting*](https://numpy.org/doc/stable/user/basics.broadcasting.html#basics-broadcasting), que conceptualmente es lo siguiente:

```python
Paso 1: np.array([2, 4, 6]) / 2

Paso 2: np.array([2, 4, 6]) / np.array([2, 2, 2])

Paso 3: np.array([1, 2, 3])
```

Si los *arrays* no coinciden en alguna dimensión, nos arroja un error:

```{code-cell}
:tags: [raises-exception]

np.array([1, 1]) * np.array([3, 3, 3])
```

A diferencia de las funciones del módulo `math`, las funciones de NumPy se aplican a todos los elementos de un *array*:

```{code-cell}
:tags: []

x = np.pi * np.array([0, 0.5, 1])

np.cos(x)
```

Por otro lado, las funciones de *reducción* de *arrays*, como la suma (`np.sum`) o el máximo (`np.max`), por defecto se aplican sobre todo el *array*:

```{code-cell}
:tags: []

x = np.array([[1, 42], [2, 5]])
x
```

```{code-cell}
:tags: []

np.max(x)
```

Pero se pueden aplicar solo sobre algunas dimensiones con el parámetro `axis`:

```{code-cell}
:tags: []

np.max(x, axis=0)
```

Estas funciones también métodos de los *arrays*:

```{code-cell}
:tags: []

x.max()
```

### Advanced indexing

A diferencia de las listas, los *arrays* se pueden [indexar de otras formas](https://numpy.org/doc/stable/reference/arrays.indexing.html#advanced-indexing).

Si hacemos una comparación, creamos una máscara, o *array* de booleanos:

```{code-cell}
:tags: []

x = np.array([1, 42, 2, 5, 0])

x > 3
```

Podemos usar esta mascara para quedarnos solo con los valores donde se cumple la condición:

```{code-cell}
:tags: []

x[x > 3]
```

+++ {"tags": []}

A veces, solo nos interesa cuántos cumplen una condición. NumPy almacena la mascara como `1` y `0` para `True` y `False`, respectivamente. Entonces, podemos directamente sumar la máscara para ver cuantos `True` hay:

```{code-cell}
:tags: []

(x > 3).sum()
```

## Ejercicio 4

Para los siguientes ejercicios, vamos a importar `numpy` y el modulo `pyplot` de `matplotlib`:

```{code-cell}
import matplotlib.pyplot as plt
import numpy as np
```

La convención es llamarlos `np` y `plt`, respectivamente.

+++

### Ejercicio 4a

Genere un *array* con los primeros 10 números al cuadrado, y otro con las primeras 10 potencias de 2.

**Ayuda:** le puede ser útil la función `np.arange`.

```{code-cell}
:tags: []

# Escriba el código aquí
```

#### Solución

```{code-cell}
---
jupyter:
  source_hidden: true
tags: [hide-input]
---
x = np.arange(10)

print(x ** 2)
print(2 ** x)
```

### Ejercicio 4b

Grafique la función $f(x) = 3 \sin{(2x)} + 1$ en el intervalo $[-5, 5]$. Para graficar, use `plt.plot(x, y)`. Pruebe variar la cantidad de puntos que utiliza para graficar.

**Ayuda**: Le puede ser útil la función `np.linspace`.

```{code-cell}
:tags: []

# Escriba el código aquí
```

#### Solución

```{code-cell}
---
jupyter:
  source_hidden: true
tags: [hide-input]
---
x = np.linspace(-5, 5, 100)
y = 3 * np.sin(2 * x) + 1

plt.plot(x, y)
```

### Ejercicio 4c

A partir de un *array* $x$ con 1000 números aleatorios con distribución gaussiana, calcule el promedio $\bar{x}$, la desviación estándar $s$ y qué fracción de números se encuentran a menos de 1 desviación estándar del promedio: $\bar{x} - s < x < \bar{x} + s$ o, equivalentemente, $|x - \bar{x}| < s$.

```{code-cell}
:tags: []

# Genera 1000 números aleatorios
x = np.random.normal(loc=0, scale=1, size=1000)

# Continue aquí la solución
```

#### Solución

```{code-cell}
---
jupyter:
  source_hidden: true
tags: [hide-input]
---
x = np.random.normal(loc=0, scale=1, size=1000)

promedio = x.mean()
desv_est = x.std()

mascara = np.abs(x - promedio) < desv_est
fraccion = mascara.sum() / mascara.size  # positivos / total

print("           Promedio:", promedio)
print("Desviación estándar:", desv_est)

print(
    f"El {fraccion:.1%} de los datos se encuentran "
    "dentro de una desviación estándar del promedio."
)
```
