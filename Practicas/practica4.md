# Conceptos 2019
## Práctica 4 - Variables

_Objetivo: Conocer el manejo de identificadores en memoria y como lo definen e implementan los diferentes lenguajes._

#### Ejercicio 1

>a) ​ Tome una de las variables de la línea 3 del siguiente código e indique y defina  cuales son sus atributos:

```Pascal {.line-numbers}
1.  Procedure Practica4();
2.  var
3.  a,i:integer
4.  p:puntero
5.  Begin
6.      a:=0;
7.      new(p);
8.      p:= ^i
9.      for i:=1 to 9 do
10.      a:=a+i;
11.     end;
12.    ...
13.     p:= ^a;
14.     ...
15.     dispose(p);
16. end;
```

Atributos de una variable:
- Nombre: string de caracteres que se usa para referenciar a la variable.
- Alcance: Rango de instrucciones en el que se conoce el nombre.
- Tipo: Valores y operaciones
- L-Value: Lugar de memoria asociado con la variable.
- R-Value: Valor codificado almacenado en la ubicación de la variable.

| Identificador | LValor     | Rvalor | Alcance | T.vida |
|---------------|------------|--------|---------|--------|
| a             | automática | indef  | 3-16    | 1-16   |
| p             | dinámica   | indef  | 4-16    | 7-15   |

T. de vida: Es el tiempo en que la variable esté alocada en memoria

>b) Compare los ​ atributos de la variable del punto a) con los atributos de la variable de la línea 4. Que dato contiene esta variable?

p es un puntero,
- En la línea 7 se aloca memoria para el puntero.
- En la línea 8 se setea con la dirección de memoria correspondiente a la variable i. 
- En la línea 13 se setea con la dirección de memoria de la variable a.
- En la línea 15 se destruye de la memoria.

La comparación con a en la tabla de arriba.

### Ejercicio 3:
>Explique los siguientes conceptos asociados al atributo l-valor de una:

>a. Variable estática.
Sensible a la historia. El lvalue se define y no cambia.

>b. Variable automática o semiestática.
Se aloca 

>c. Variable dinámica.
Punteros

>d. Variable semidinámica.


>De al menos un ejemplo de cada uno.
>Investigue sobre que tipos de variables respecto de su l-valor hay en los lenguajes C y Ada.

### Ejercicio 4:
>a. ¿A qué se denomina variable local y a qué se denomina variable global?


>b. ¿Una variable local puede ser estática respecto de su l-valor? En caso afirmativo de un ejemplo
>c. Una variable global ¿siempre es estática? Justifique la respuesta.
>d. Indique que diferencia hay entre una variable estática respecto de su l-valor y una constante


### Ejercicio 8
> Sea el siguiente ejercicio escrito en Pascal

```pascal
1- Program Uno;
2- ​ type tpuntero= ^integer;
3-​ var mipuntero: tpuntero;
4- ​ var i:integer;
5- ​ var h:integer;
6- Begin
7-  i:=3;
8-  mipuntero:=nil;
9-  new(mipuntero);
10- mipunterno^:=i;
11- h:= mipuntero^+i;
12- dispose(mipuntero);
13- write(h);
14- i:= h- mipuntero;
15- End​ .
```

>a) Indique el rango de instrucciones que representa el tiempo de vida de las variables i, h y mipuntero.

- i: 1-15
- h: 1-15
- mipuntero: 9-12 

>b) Indique el rango de instrucciones que representa el alcance de las variables i, h y mipuntero.

- i: 4-15
- h: 5-15
- mipuntero: 3-15

### Ejercicio 9:
>Elija un lenguaje y escriba un ejemplo:
>a. En el cual el tiempo de vida de un identificador sea mayor que su alcance
>b. En el cual el tiempo de vida de un identificador sea menor que su alcance
>c. En el cual el tiempo de vida de un identificador sea igual que su alcance

```c
int *puntero;
int fun1(){
    int aux=0;
    static int x;
    aux= x++;
}

int main(){
    int i=0;
    for (i=1; i< 5; i++){
        i+=fun1();
    }

}

```

a. la variable statix x de fun1.
b. puntero
c. aux de fun1.

### Ejercicio 11
>a) ​ Responda Verdadero o Falso para cada opción. ​ ​ El​ ​ tipo de dato de una variable es?:

>I) Un string de caracteres que se usa para referenciar a la variable y operaciones que se pueden realizar
sobre ella. `Falso`

>II) Conjunto de valores que puede tomar y un rango de instrucciones en el que se conoce el nombre. `Falso`

>III) Conjunto de valores que puede tomar y lugar de memoria asociado con la variable. `Falso`

>IV) Conjunto de valores que puede tomar y conjunto de operaciones que se pueden realizar sobre esos valores. `Verdadero`


b)​ Escriba la definición correcta de tipo de dato de una variable.

Antes que una variable pueda ser referenciada debe _ligárse a un tipo_.
El __tipo__ es un conjunto de valores y un conjunto de operaciones asociados a la variable.
Existen tipos:
- Predefinidos (tipos base)
- Definidos por el usuario (Constructores)
- TADs (Tipos abstractos de datos)



### Ejercicio 12

>Sea el siguiente programa en ADA, completar el cuadro siguiente indicando para cada
variable de que tipo es en cuanto al momento de ligadura de su l-valor, su r-valor al momento de alocación en memoria y para todos los identificadores cuál es su alcance y cual es su el tiempo de vida. Indicar para cada variable su r-valor al momento de alocación en memoria.


```Ada
1.  with text_io; use text_io;
2.  Procedure Main is;
3.  type​ vector is array(integer range <>);
4.  a, n, p:integer;
5.  v1:vector(1..100);
6.  c1: constant integer:=10;
7.  Procedure Uno is;
7.1      type​ puntero is access integer;
7.2      v2:vector(0..n);
7.3     c1, c2: character;
7.4     p,q: puntero;
7.5     begin
7.5.1.      n:=4;
7.5.2.      v2(n):= v2(1) + v1(5);
7.5.3.      p:= new puntero;
7.5.4.      q:= p;
7.5.5.      .......
7.5.6.      free p;
7.5.7.      ......
7.5.8.      free q;
7.5.9.      ......
7.6. ​  end​ ;
8. ​ begin
9.  n:=5;
10. .....
11. Uno;
12. a:= n + 2;
13. .....
14. end
```

| Ident          | Tipo       | R-Valor | Alcance  | T.V         |
|----------------|------------|---------|----------|-------------|
| a (línea 4)    | automática | basura  | 4-14     | 1-14        |
| n (línea 4)    | automática | basura  | 4-14     | 1-14        |
| p (linea 4)    | automática | basura  | 4-6,8-14 | 1-14        |
| v1             | explícita  | basura  | 5-14     | 1-14        |
| c1 (línea 6)   | automática       | 10      | 6,8-14   | 6-14        |
| v2             | semidinamico   | basura  | 7-7.6    | 7-7.6       |
| c1 (línea 7.3) | automática | basura  | 7.3-7.6  | 7-7.6       |
| c2 (línea 7.3) | automática | basura  | 7.3-7.6  | 7-7.6       |
| p (línea 7.4)  | automática   | basura       | 7.4-7.6  | 7.5.3-7.5.6 |
| q (línea 7.4)  | automática  | basura       | 7.4-7.6  | 7.5.4-7.6 |
| p (línea 7.5.3)  | dinámica  | basura*       | 7.5.3-7.5.8  | 7.5.3-7.5.8 |
| Main           |            |         | 2-14     | 1-14        |
| Uno            |            |         | 7.1-14   | 7-7.6       |

p cuando hace new es una variable nueva
p que apunta y q que apunta son variables nuevas

### Ejercicio 13
> El nombre de una variable puede condicionar:
> a) ​ Su tiempo de vida.
> b) ​ Su alcance.
> c) ​ Su r-valor.
> d)​ Su tipo.
> Justifique la respuesta

En un lenguaje como Ruby,
a. Sí. El tiempo de vida de una variable puede condicionarse con el nombre, por ejemplo: `@variable` es una variable de instancia que vivirá solo en la instancia de la clase a la que pertenece.
b. Sí, siguiendo en Ruby, una variable por ejemplo `$variable` será una variable global.
d. Sí?. En Ruby una constante se declara con mayúsculas. No podrá cambiar su tipo ni valor en ejecución.