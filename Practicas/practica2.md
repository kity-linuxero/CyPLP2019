# Conceptos
## Práctica 2

### Ejercicio 1
Cuadro completado

| BNF              | EBNF             | Diagramas sintácticos                        | Significado                           |
|------------------|------------------|----------------------------------------------|---------------------------------------|
| palabra terminal | palabra terminal | Óvalo                                        | Definición de un elemento terminal    |
| < >              | < >              | Rectángulo                                   | Definición de un elemento no terminal |
| ::=              | ::=              | diagrama con rectángulos, óvalos y flechas   | Definición de una producción          |
| `|`              | `(|)`            | flecha que se divide en dos o mas caminos   | Selección de una alternativa          |
| < p > < p1 >     | { }              | retorno de una flecha a un elemento anterior | Repetición                            |
|                  | *                |                                              | Repetición de 0 o más veces           |
|                  | +                |                                              | Repetición de 1 o más veces           |
|                  | [ ]              | con flechas de selección                     | Opcional, puede o no estar            |

### Ejercicio 2
> ¿Cuál es la importancia de la sintaxis para un lenguaje? ¿Cuáles son sus elementos?

La sintaxis es un conjunto de reglas que definen como combinar distintos caracteres para formar programas. Esto a su vez, proporciona mecanismos para que una persona o computadora para denifir si un programa es sintácticamente válido y de esta manera proporciona una forma de comunicación con el programador y el compilador u otro programador que tiene que leer el código fuente.

Elementos de la sintaxis:
- Conjunto de caracteres:
    Por ejemplo ASCII.
- Identificadores:
    Generalmente se usan una cadena de caracteres y/o dígitos que comienzan con una letra. Se usa para identificar partes de un programa como una variable.
- Operadores:
    Conjunto de caracteres utilizados o reservados para realizar operaciones. Por ejemplo la suma +, resta -. En el resto de los operadores no suele haber tanta uniformidad entre lenguajes y puede diferir o haber varias formas de realizar una operación.
- Palabras claves o reservadas:


- Comentarios y uso de blancos:
    Los comentarios ayudan a hacer el código mas legible y documentar secciones de código para dar alguna aclaración,

### Ejercicio 3
> ¿Explique a qué se denomina regla lexicográfica y regla sintáctica?

Las **reglas lexicográficas** determinan, a partir del alfabeto, las __words__ que se usarán en el lenguaje.
Las **reglas sintácticas** especifican __cómo__ combinar las __words__ para formar las expresiones y sentencias.

### Ejercicio 4
>¿En la definición de un lenguaje, a qué se llama palabra reservadas? ¿A qué son
equivalentes en la definición de una gramática? De un ejemplo de palabra reservada en el lenguaje que más conoce. (Ada,C,Ruby,Python,..)

Las palabras __reservadas__ son palabras que no pueden ser usadas como __identificadores__. Este concepto se puede confundir con el de __palabra clave__, que se refiere a palabras que tienen un cierto significado en un cierto contexto. En la definición de una gramática, las palabras reservadas serían `G`,`N`,`T`,`S` y `P`

Por ejemplo, en C o Java una palabra reservada sería __void__. La misma no puede ser usada como identificador para una rutina o variable.

### Ejercicio 5
> Dada la siguiente gramática escrita en BNF:
> ```
> G= ( N, T, S, P)
> N = {<numero_entero>, <digito> }
> T = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}
> S = <numero_entero>
> P={
> <numero_entero>::=<digito><numero_entero> | <numero_entero><digito> | <digito>
> <digito> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
>}
> ```
> 
> a. Identifique los componentes.
>
> b. Indique por qué es ambigua y corríjala.

**a.** 
Una gramática BNF está formada por una 4-tupla.
G=(N,T,S,P) (4-tupla).
- N: Conjunto de símbolos no terminales.
- T: Conjunto de símbolos terminales.
- S: Símbolo distinguido de la gramática que pertenece a N.
- P: Conjunto de producciones.

**b.**
Es ambígua porque _hay dos formas_ de armar un número entero: `<digito><numero_entero>` y `<numero_entero><digito>`. Si suprimimos uno de esos conjunto de producciones se corrije.

### Ejercicio 6
>Defina en BNF la gramática para la definición de una palabra cualquiera.
```
Partiendo que G=(N, T, S, P)
N= {<palabra>, <letra>}
T= {a-z}
S= <palabra>
P= {
    <palabra>::= <letra> | <letra><palabra>
    <letra> ::= a | b | c | d ... | z | A | B ... | Z | 
}
```
### Ejercicio 7
>Defina en EBNF la gramática para la definición de números reales. Inténtelo desarrollar para BNF y explique las diferencias con la utilización de la gramática EBNF.

```
G= (N, T, S, P)
    -N: {<real>, <signo>, <digito>, <fraccion>}
    -T: {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, ., -}
    -S: <real>
    -P: <real> ::= [ <signo> ]{<digito>}+ [ <fraccion> {<digito>}+ ]
        <signo> ::= -
        <fraccion> ::= .
        <digito> ::= ( 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 )
```

### Ejercicio 8

>Utilizando la gramática que desarrolló en los puntos 6 y 7, escriba el árbol sintáctico de:
> a. Conceptos
> b. Programación
> c. 1255869
> d. 854,26
> e. Conceptos de lenguajes

__Conceptos__
```
        <palabra>
        /       \
    <letra>     <palabra>
       |         /     \
       C     <letra>    <palabra>
                |        /      \
                o   <letra>     <palabra>
                       |        /       \
                       n    <letra>     <palabra>
                               |        /        \
                               c    <letra>     <palabra>
                                       |        /       \
                                       e    <letra>     <palabra>
                                               |        /       \
                                               p    <letra>     <palabra>
                                                       |         /      \
                                                       t    <letra> <palabra>
                                                               |        |       
                                                               o     <letra>    
                                                                        |
                                                                        s
```

__854,26__
```
                  <real>     
    /       /       |       \       \       \
<digito><digito><digito><fraccion><digito><digito>
    |       |       |        |        |       |
    8       5       4        ,        2       6
```
### Ejercicio 9
>Defina utilizando diagramas sintácticos la gramática para la definición de un identificador de un lenguaje de programación. Tenga presente como regla que un identificador no puede comenzar con números.


### Ejercicio 10
> a) ​ Defina con EBNF la gramática para una expresión numérica, dónde intervienen variables y números. Considerar los operadores +, -, * y / sin orden de prioridad. No considerar el uso de paréntesis.

```
G= (N,T,S,P)
N: {<expresion>, <operador>, <numero>, <digito>}
T: {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, -, +, /, *}
S: {<expresion>}
P: {
    <expresion>::= <numero>[{<operador><numero>}+]
    <operador>::= ( - | + | / | * )
    <numero>::= <digito>[{digito}+]
    <digito> ::= ( 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 )
}
```

>b) A la gramática definida en el ejercicio anterior agregarle prioridad de operadores.

```
G= (N,T,S,P)
N: {<expresion>, <operador>, <numero>, <digito>, <termino>, <op1>, <op2>}
T: {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, -, +, /, *}
S: {<expresion>}
P: {
    <expresion>::= <termino>[{<op1><termino>}*]
    <numero>::= <digito>[{digito}+]
    <digito> ::= ( 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 )
    <op1>::= ( - | + )
    <op2>::= ( / | * )
    <termino>::= <numero>[{<op2><numero>}*]
}
```

Arbol sintáctico para 5+3*20
```
                 <expresion>
               /      |     \
        <termino>   <op1>      <termino>
            |         |       /     |   \
        <numero>      +   <numero><op2>  <numero>
            |                |      |       |   \
        <digito>         <digito>   *   <digito> <numero>
            |                |              |       |
            5                3              2    <digito>
                                                    |
                                                    0
```

>c) Describa con sus palabras los pasos y decisiones que tomó para agregarle prioridad de
operadores al ejercicio anterior.

Se definió el no terminal `<termino>` para dividir una expresión "en términos" cuando encuentre un + o -.
Luego se dividieron los operadores en op1 para los operadores + y - y en op2 para * y /.

