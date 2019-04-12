# Conceptos 2019
## Práctica 3

####Ejercicio 1
> ¿Qué define la semántica?

La _semántica_ describe el significado de los símbolos, palabras y frases de un lenguaje ya sea lenguaje natural o lenguaje informático.

####Ejercicio 2
> a.¿Qué significa compilar un programa?

La compilación de un programa es la `traducción` del código fuente al lenguaje _"máquina"_ que puede ser interpretado (y ejecutado) por el procesador.
Por lo general, el programa suele ser lenguaje objetivo .o, aunque a veces puede ser a un lenguaje intermedio `bytecode`, como en el caso de Java.
    Lenguaje Fuente -----> Lenguaje Objeto
                      ↑Compilación

>b. Describa brevemente cada uno de los pasos necesarios para compilar un programa.

- Análisis:
    - Análisis léxico (Scanner): Ha
    - Análisis sintáctico (Parser)
    - Análisis semántico (Semántica estática)
`Generación de código intermedio`
- Síntesis
    - Optimización del código
    - Generación del código

>c. ¿En qué paso interviene la semántica y cual es su importancia dentro de la compilación?

Interviene en el `análisis semántico` de forma de `semántica estática`. Es la fase medular y por lo tanto la mas importante durante la compilación.
En el análisis semántico (semántica estática) se realizan pasos importantes como:
- Se realiza la comprobación de tipos
- Se agrega información implícita (variables no declaradas).
- Se agrega en la tabla de símbolos los descriptores de tipos, etc a la vez que se hacen consultas para realizar comprobaciones.
- Se hacen las comprobaciones de nombres. Ej.: toda variable debe estar declarada.
- Es el nexo entre el análisis y la síntesis.

####Ejercicio 3:
>Con respecto al punto anterior ¿es lo mismo compilar un programa que interpretarlo?
>Justifique su respuesta mostrando las diferencias básicas, ventajas y desventajas de cada uno.

Tanto la compilación como la interpretación son formas de interpretación de código fuente a código máquina.

NO es lo mismo _compilar e interpretar_ un programa.

| __Intérprete__                                                                                      | __Compilador__                                                      |
|-----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| Ejecuta el programa de entrada directamente                                                         | Produce un programa equivalente en lenguaje objeto                  |
| Sigue el orden lógico de ejecución                                                                  | Sigue el orden físico de las sentencias                             |
| Si la sentencia está en un loop se realizará la tarea tantas veces como sea requerido               | No repite lazos, se decodifica una vez                              |
| Más lento en ejecución                                                                              | Más rápido desde el punto de vista del hardware                     |
| Ocupa menos espacio, cada sentencia se deja en la forma original                                    | Una sentencia puede ocupar cientos de sentencias de máquina         |
| Las sentencias del código fuente pueden ser relacionadas directamente con la que se está ejecutando | Cualquier referencia al código fuente se pierde en el código objeto |
| Más rápido en el desarrollo. Se pueden probar sentencias sin compilar el programa entero.           | Necesario compilar todo el programa para probar una sentencia.      |


####Ejercicio 4
>Explique claramente la diferencia entre un error sintáctico y uno semántico. Ejemplifique cada caso.

- Sintáxis: Conjunto de _reglas_ que definen como componer letras, dígitos y otros caracteres para formar los programas.
- Semántica: Conjunto de reglas para dar _significado_ a los programas sintácticamente válidos.

Un error sintáctico se refiere a un error donde la sintaxis es incorrecta. Puede ser el uso de caracteres no válidos, error de tipeo, etc.

Un error semántico es más dificil de detectar. Ejemplo: operaciones no válidas entre variable de distinto tipo. _Los errores semánticos se refieren a la semántica estática._

```C
int main(){
   int e:=10;   //Sintáctico. La asignación NO es con :=
   if (a<10){   //Semántico. a no está declarada
    e="hola";   //Semántico. e es de tipo int
   }
   return e     //Sintáctico. Se espera ';' 
}
```
####Ejercicio 5
>Sean los siguientes ejemplos de programas. Analice y diga qué tipo de error se produce (Semántico o Sintáctico) y en qué momento se detectan dichos errores (Compilación o Ejecución).
>_Aclaración: Los valores de la ayuda pueden ser mayores._

a. Pascal
```Pascal
Program P
    var 5: integer;             {1}
    var a:char;
    Begin
    for i:=5 to 10 do begin     {2}
        write(a);
        a=a+1;                  {3}
    end;
End.                            {4}
```
_Ayuda: Sintáctico 2, Semántico 3_
1. Sintáctico. Un identificador NO puede iniciar con un número.
2. Semántico. i no está declarado
3. Semántico y sintáctico. Intenta sumar +1 a un char. El símbolo de asignación en Pascal es :=
4. Sintáctico. Se espera ; en lugar de .