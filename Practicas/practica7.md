# Conceptos 2019
## Práctica 7 - Sistemas y tipos de Datos

_Objetivo​: Comprender las nociones fundamentales sobre las diversas propiedades de los sistemas de tipos y los tipos de datos_

#### Ejercicio 1: Sistemas de tipos:
**1. ¿Qué es un sistema de tipos y cuál es su principal función?**

Conjunto de reglas que estructuran y organizan una colección de tipos. El objetivo del sistema de tipos es lograr que los programas sean tan seguros como sea posible.

**2. Definir y contrastar las definiciones de un sistema de tipos fuerte y débil (probablemente en la bibliografía se encuentren dos definiciones posibles. Volcar ambas en la respuesta). Ejemplificar con al menos 2 lenguajes para cada uno de ellos y justificar.**

> Def: Un lenguaje es fuertemente typado (type safety) si el sistema de tipos impone restricciones que aseguran que no se producirán **errores de tipo en ejecución.**

El tipado fuete especifica restricciones sobre como las operaciones que involucran valores de diferentes tipos pueden operarse. Débilmente tipado es lo opuesto.

- Python y Pascal son fuertemente tipados.
- C y PHP son débilmente tipados

**3. Además de la clasificación anterior, también es posible caracterizar el tipado como estático o dinámico. ¿Qué significa esto? Ejemplificar con al menos 2 lenguajes para cada uno de ellos y justificar.**

Se refieren al tipo de ligadura:
- Tipado estático: Ligaduras en tiempo de compilación. La entidad/variable queda ligada a su tipo en compilación, sin necesidad de ejecutar el programa. C, Java.
- Tipado dinámico: Ligaduras en tiempo de ejecución. La ligadura de la entidad/variable se produce en tiempo de ejecución. PHP, Ruby, Python.

####  Ejercicio 2: Tipos de datos:

**1. Dar una definición de tipo de dato.**

| Enfoque      	| Descripción                                                                                           	|
|--------------	|-------------------------------------------------------------------------------------------------------	|
| Denotacional 	| Conjunto de valores sobre un _dominio_                                                                	|
| Contructivo  	| **Primitivo:** provisto por el lenguaje. **Compuesto:** empleando constructores de tipo.              	|
| Abstracción  	| Una interfaz a una representación. Conjunto de operaciones con semántica bien definida y consistente. 	|

**2. ¿Qué es un tipo predefinido elemental? Dar ejemplos.**

Son tipos provistos por lo general por el lenguaje que poseén como ventajas:
- Invisibilidad de la representación
- Verificación estática
- Desambiguar operadores
- Control de precisión

**3. ¿Qué es un tipo definido por el usuario? Dar ejemplos.**

Separan la especificación de la implementación. Se definen los tipos que el problema necesita.
Pueden adaptarse mejor a un tipo de necesidad específica del programa. 

Por ejemplo,

**Tipo enumerativo:**

```
type MES is (ENERO,FEBRERO,,........,DICIEMBRE)
x: mes;
type VERANO is (ENERO,EEBRERO,MARZO)
y: verano.
```
Tiene en cuenta el orden (predecedor, sucesor). Relaciones: <, >, <=, etc


#### Ejercicio 3: Tipos compuestos:

**1. Dar una breve definición de: producto cartesiano (en la bibliografía puede aparecer también como ​ product type), correspondencia finita, uniones (en la bibliografía puede aparecer  también como sum type) y tipos recursivos.**

**Producto cartesiano. Ejemplo. Estructuras de C**

```c
typedef struct{             //Definición
    int nro_lados;
    float tamaño_lados;
}reg_poligon;

reg_poligon pol = {3,3.45}; //Instancia con valor compuesto inicial
pol.nro_lados = 4;          //Acceso
/* Operaciones de campo. Operaciones de tipo */
```

**Correspondencia finita**

Correspondencia finita en general
`f: DT -> RT`
Si DT es un subrango de enteros:
`f: [li..ls] -> RT`
_Conjunto de valores accessibles via un subindice_

- Rutina: su definición es la regla de asociación de valores del tipo DT en valores tipo RT.
- Definición intencional: que especifica una regla (la intención) en lugar de una asociación individual. `F(x)= 2x`
- Arreglos: definición _extensional_, los valores de la función son explícitamente enumerados.

**Uniones**

>Def: La unión/unión discriminada de dos o mas tipos define un tipo como la disjunción de los tipos de datos.

- Permite manipular diferentes tipos en distinto momento de la ejecución.
- Chequeo dinámico (en ejecución)

La **unión discriminada** agrega un _discriminante_. Si tenemos la unión discriminida de dos conjuntos S y T, y aplicamos el discriminante a un elemento e perteneciente a la unión discriminada devolverá S o T.

**Recursión**

Un tipo de dato recursivo T se define como una estructura que puede contener componentes del tipo T .

- Los lenguajes de programación convencionales soportan la implementación de los tipos de datos recursivos a través de los punteros.
- Los lenguajes funcionales proveen mecanismos mas abstractos que enmascaran a los punteros.


#### Ejercicio 4: Mutabilidad/Inmutabilidad:

**1. Definir mutabilidad e inmutabilidad respecto a un dato. Dar ejemplos en al menos 2 lenguajes. ​ TIP: indagar sobre los tipos de datos que ofrece Python y sobre la operación `#freeze` en los objetos de Ruby.**



**2. Dado el siguiente código:**
`a ​ = ​ ​ Dato​.new(1)`
`a ​ = ​ ​ Dato​.new(2)`
**¿Se puede afirmar entonces que el objeto “Dato.new(1)” es mutable? Justificar la respuesta sea por afirmativa o por la negativa.**


#### Ejercicio 5: Manejo de punteros:
**1. ¿Permite C tomar el l-valor de las variables? Ejemplificar.**

Un puntero es una referencia a un objeto. Una variable puntero es una variable cuyo _r-valor_ es una referencia a un objeto.

```c
int* p1;
int x=1;
p1= &x; //p1 toma el l-valor de x
printf("%d-%d", p1, &x);
```
Imprimirá: 1987430388-1987430388


**2. ¿Qué problemas existen en el manejo de punteros? Ejemplificar.**

1. Violación de tipos
2. Referencias (punteros) sueltas - referencias dangling: Una referencia suelta o dangling es un
puntero que contiene una dirección de una variable dinámica que fue desalocada. Si luego se usa el puntero producirá error.
3. Liberación de memoria: Objetos perdidos.
    - Los objetos (apuntados) que se alocan con la primitiva new son alocados en la heap.
    - La memoria en la heap puede agotarse.
    - Si los objetos dejan de ser apuntados (objeto perdido) esa memoria podría liberarse.
    - Se pueden liberar:
        - Explícitamente: Lo hace el programador. `dispose` (Pascal), `free` en C.
        - Implícitamente: Garbage collector. Java, Python
4. Punteros no inicializados:
    - Peligro de acceso descontrolado a posiciones de mamoria.
    - Solución: valor especial nulo. nil en Pascal. void en C/C++. null en Ada, Phyton.
5. Alias



#### Ejercicio 6: TAD​ ​ :
**1. ¿Qué características debe cumplir una unidad para que sea un TAD?**

TAD= Representación (datos) + Operaciones (funciones y procedimientos).
Los tipos de datos son abstractos y el proceso de construir nuevos tipos se llama abstracción de datos.

Los nuevos tipos de datos definidos por el usuario se llaman _tipo abstractos de datos_. El principio básico de la abstracción es la información oculta.

**Tipo abstracto de dato (TAD) es el que satisface:**
- Encapsulamiento: la representación del tipo y las operaciones permitidas para los objetos del tipo se describen en una única unidad sintáctica.
- Ocultamiento de la información: la representación de los objetos y la implementación del tipo permanecen ocultos.

**2. Dar algunos ejemplos de TAD en lenguajes tales como ADA, Java, Python, entre otros.**

Las unidades de programación de lenguajes que pueden implementar un TAD reciben distintos nombres:
- Modula-2 módulo
- Ada paquete
- C++ clase
- Java clase