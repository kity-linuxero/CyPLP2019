# Conceptos 2019
## Práctica 9 - Estructuras de control y sentencias

_Objetivo:​ reconocer las diferencias entre las implementaciones de las estructuras de control de los distintos lenguajes_

#### Ejercicio 1: ​Una sentencia puede ser simple o compuesta,​ ​¿Cuál es la diferencia?

Una sentencia simplme será una sentencia de una sola línea. Una sentencia compuesta es un grupo de sentencias agrupadas por delimiadores como `begin end`en Pascal o `{...}` en C, Java.

#### Ejercicio 2: Analice como C implementa la asignación.

La asignación es una sentencia que produce cambios en los datos de la memoria. Lenguajes como C definen la _sentencia de asignación_ como una **expresión con efecto laterales**. Las sentencias de asignación _devuelven valores_. 

Evalúa de derecha a izquierda. `a=b=c=0`

La mayoría de lenguajes requieren que sobre el lado izquierdo de la asignación aparezca un l-valor. C permite _cualquier expresión_ que denote un l-valor. Por ejemplo `(i<j?x:y)=5`

#### Ejercicio 3: ¿Una expresión de asignación puede producir efectos laterales que afecten al resultado final, dependiendo de cómo se evalúe? De ejemplos.

Lenguajes como C definen la _sentencia de asignación_ como una **expresión con efecto laterales**. Las sentencias de asignación _devuelven valores_. 
 
 ```c
int x;
/* El siguiente if true siempre y cuando pueda asignarse el valor 1 a x */
if (x=1){
    printf("X es uno");
}

/* Ahora sí es una comparación */
if (x==1){
    printf("X ahora sí es uno");
}

```

#### Ejercicio 4: Que significa que un lenguaje utilice circuito corto o circuito largo para la evaluación de una expresión. De un ejemplo en el cual por un circuito de error y por el otro no.

**Circuito corto:** `(2>1 & valor)` -> al comprobar que parte de la condición es falsa, no continúa con la comprobación y el resultado será falso. Esto indica que si valor es un llamado a una función esta nunca será ejecutada.

Python para evaluar las condiciones utiliza la _evaluación con circuito corto_.

```python
estatura = 1.79
estatura = "Alto" if altura > 1.65 else "Bajo"
estatura
'Alto'
```

**Circuito largo:** Calculo que será lo opuesto. un if tradicional?.


#### Ejercicio 6: ¿Cuál es la construcción para expresar múltiples selección que implementa C? ¿Trabaja de la misma manera que la de Pascal, ADA o Python?

```c
/* en C*
switch (valor){
    case 1: sentencia1;
    case 2: sentencia2; break;
default: /* Ejecuta esto si valor no coincide con ninguno de los anteriores*/
}
```

En Pascal es con `case`. No tengo tiempo para poner los ejemplos XD

#### Ejercicio 7: ​ Sea el siguiente código:
```
.....
var i, z:integer;
    Procedure A;
    begin
        i:= i +1;
    end;

begin
    z:=5;
    for i:=1..5 do
    begin
        z:=z*5;
        A;
        z:=z + i;
    end;
end;
```

**a- Analice en las versiones estándar de ADA y Pascal, si este código puede llegar a traer problemas. Justifique la respuesta.** 

Pascal estandar no permite que se toquen ni los valores del límite inferior y superior, ni el valor de la variable de control. En ADA no debe declararse el iterador.

**b- Comente qué sucedería con las versiones de Pascal y ADA, que Ud. utilizó.**

lalala



blabla

