# Conceptos 2019
## Práctica 3

#### Ejercicio 1
> ¿Qué define la semántica?

La _semántica_ describe el significado de los símbolos, palabras y frases de un lenguaje ya sea lenguaje natural o lenguaje informático.

#### Ejercicio 2
> a. ¿Qué significa compilar un programa?

La compilación de un programa es la `traducción` del código fuente al lenguaje _"máquina"_ que puede ser interpretado (y ejecutado) por el procesador.
Por lo general, el programa suele ser lenguaje objetivo .o, aunque a veces puede ser a un lenguaje intermedio `bytecode`, como en el caso de Java.
```    
    Lenguaje Fuente -----> Lenguaje Objeto
                      ^
                  Compilación
```
>b. Describa brevemente cada uno de los pasos necesarios para compilar un programa.

- Análisis:
    - Análisis léxico (Scanner)
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

#### Ejercicio 3:
>Con respecto al punto anterior ¿es lo mismo compilar un programa que interpretarlo?
Justifique su respuesta mostrando las diferencias básicas, ventajas y desventajas de cada uno.

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


#### Ejercicio 4
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
#### Ejercicio 5
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
__Todos estos errores saltan en tiempo de compilación__

b. Java
```Java
public String tabla(int numero, arrayList<Boolean> listado)
{
    String result = null;
    for(i = 1; i < 11; i--) { // 1
        result += numero + "x" + i + "=" + (i*numero) + "\n"; //2
        listado.get(listado.size()-1)=(BOOLEAN)numero>i; //3
    }
    return true; //4
}
```
_Ayuda: Sintácticos 4, Semánticos 3, Lógico 1_
1. Errores varios
1.1. Error lógico: el for nunca termina.
1.2. Error semántico: i no está declarado.

2. Errores varios
2.1 Error semántico: result es null. No puede asignarse +=.
2.2 Error semántico: número es un int. Se intenta concatenar como si fuera String.
2.3
3. Errores varios
3.1 Error semántico: Se intenta asignar un valor al retorno de una función
3.2 Error sintáctico: BOOLEAN no existe.
4. Error semántico: Retorna un true cuando la función espera devolver un String

Todos los errores se detectan en tiempo de compilación excepto el error lógico 1.1 que será en tiempo de ejecución.

c. C
```C
# include <stdio.h>
int suma; /* Esta es una variable global */
int main()
{
    int indice;
    encabezado;                                 //1
    for (indice = 1 ; indice <= 7 ; indice ++)
        cuadrado (indice);
    final(); Llama a la función final */        //2
    return 0;
}

cuadrado (numero)                               // 3
int numero;
{   int numero_cuadrado;
    numero_cuadrado == numero * numero;         //4
    suma += numero_cuadrado;                    //5
    printf("El cuadrado de %d es %d\n", numero, numero_cuadrado);
}                                               //6
```
_Ayuda: Sintácticos 2, semánticos 6_

1. Error semántico. "Encabezado no está definido".
2. Errores sintáctico y semántico:
    2.1. Error sintáctico. Se encuentra */ para cerrar comentarios pero no está abierto.
    2.2. Error semántico. final() no existe
3. Error sintáctico. Luego de declarar el encabezado de una función se espera "{"
4. Error semántico. Se hace una comparación que retorna un bool que nunca es usado.
5. Errores semánticos:
    5.1. numero_cuadrado no está inicializado.
    5.2. suma se usa sin estar inicializada.
6. Error semántico. En C una función por defecto retorna un int. Al no estar especificado, se espera que retorne un int que nunca es retornado.

Todos los errores hallados se detectan en tiempo de compilación.

---------

#### Ejercicio 6
>Explique cuál es la semántica para las variables predefinidas en lenguaje Ruby __self__ y __nil__​ . ¿Qué valor toman; cómo son usadas por el lenguaje?

Las variable predefinida __self__  se utiliza para referirse a un objeto como sí mismo.
Por ejemplo el siguiente código
```Ruby
class Main
  puts "Estamos en " + self.to_s
  module Modulo
    puts "Ahora estamos en el módulo anidado " + self.to_s
  end
  puts "Ahora volvemos a " + self.to_s
end
```
Devolverá:
```ruby
ruby 2.5.0p0 (2017-12-25 revision 61468) [x86_64-linux]
Estamos en Main
Ahora estamos en el módulo anidado Main::Modulo
Ahora volvemos a Main
```

La variable predefinida __nil__ es utilizada para indicar un valor nulo. Como en Ruby todo es un objeto, incluso __el valor nil__, perteneciente a la clase NilClass.

```ruby
> 5.nil?
=> false
```
```ruby
> nil.class
=> NilClass
```


------


#### Ejercicio 9
>Defina el concepto de ligadura y su importancia respecto de la semántica de un programa. ¿Qué diferencias hay entre ligadura estática y dinámica? Cite ejemplos (proponer casos sencillos)

#### Ligadura (binding)
- Los programas trabajan con _entidades_.
- Las entidades tienen _atributos_.
- Los atributos tienen que establecerse antes de poder usar la entidad.
__Ligadura:__ es la `asociación entre la entidad y el atributo`.

| __Entidad__ | __Atributo__                                        |
|-------------|-----------------------------------------------------|
| Variable    | Nombre, tipo, área de memoria, etc                  |
| Rutina      | nombre, parámetros formales, parámetros reales, etc |
| Sentencia   | Acción asociada                                     |

Entre los lenguajes puede variar el _momento de la ligadura_ (binding time).

Una ligadura es __estática__ si se establece antes de la ejecución y NO se puede cambiar.

Una ligadura es __dinámica__ si se establece en el momento de ejecución y puede cambiarse de acuerdo de alguna regla específica del lenguaje. _Excepción: constantes._

En lenguaje C se liga el tipo a la variable _en compilación._ Por lo tanto es un tipo de ligadura estática. La variable no podrá cambiar su tipo en tiempo de ejecución.


-----------
#### Dudas:
- ¿Están bien definidas las diferencias entre errores semánticos y estáticos?
- 