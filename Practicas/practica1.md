# Conceptos y Paradigmas de lenguajes de Programación
## Práctica 1

## Historia, evolución y caracteristicas de lenguajes de programación

### Objetivo: ​ Conocer​ ​ la evolución de los lenguajes de programación y sus características.

### Ejercicio 1
>Indique para cada uno de los períodos presentados cuales son las características nuevas que se incorporan y cual de ellos la incorpora.

#### 1951-1955
-----
**Lenguanje ensamblador:**
  No existen las estructuras de control, se simulan con saltos de linea. Es un lenguaje de bajo nivel, el paso mas cercano a lenguaje de maquina.
  Introduce el uso de subprogramas y estructuras de datos lineales.

#### 1956-1960
-----

**Fortran:** introduce la posibilidad  de escribir expresiones centificas y matemáticas casi literalmente.
  La meta de fortran era conseguir un lenguaje que incluyera estructuras de control condicionales, y enunciados de entrada/salida.
  Demostrar que aunque es un lenguaje de alto nivel, es tan eficiente como assembler. Sus creadores buscaban trasladar formulas matemáticas a codigo maquina.

**Algol:** introdujo la estructura de bloques anidados y su implementación como una pila de ejecución.
  Es un lenguaje diseñado para describir algoritmos, con una sintáxis parecida a las matemáticas tradicionales. Fue diseñado con sintaxis BNF.

**Lisp:** Tiene un objetivo basico: Atomos y listas de atomos y la llamada recursion de funciones constituye los mecanismos básicos de ejecucion. Permite ejecutar estructuras de datos como programas y programas como datos, Se descarta la fuerte dependencia de la recursion como estructura de control, en favor de la iteración.

   Los 3 lenguajes buscaban crear aplicaciones para problemas específicos de un area determinada, Fortran del calculo matemático, algol el manejo de datos de entrada salida y lisp el manejo de listas de datos simbólicos, ademas, de el manejo iterativo de estas listas en lugar del recursivo.
   
#### 1961-1965
----------
 **Cobol:** el objetivo principal de este lenguaje es obtener independencia de hardware, también muchos aspectos de lenguaje están pensados para permitir el uso de estructuras relativamente eficientes en tiempo de ejecución. Buscaba tambien escribir sentencias en inglés natural.

  La traducción de Cobol a código ejecutable eficiente es compleja, a causa del número de representaciones de datos y muchas formas de escribir lo mismo.

 Cobol brinda herramientas para separar los elementos de un programa que dependen del hardware de los que no.

**Snobol:** Su meta era  desarrollar un lenguaje de procesamiento de cadenas para manipulación de formulas y analisis de graficos, su nombre provien de StriNg Oriented syMBOlic Language.

Implementa la concordancia de patrones con base en gramática bcnf. Es un lenguaje totalmente dinamico incluyendo sus declaraciones, tipos, asignaciones de almacenamiento, hasta puntos de entrada y salida de almacenamiento.

### Ejercicio 3

>¿Qué atributos debería tener un buen lenguaje de programación? Por ejemplo,
ortogonalidad, expresividad, legibilidad, simplicidad, etc. De al menos un ejemplo de un lenguaje que cumple con las características citadas.

__Ortogonalidad:__ Constructores primitivos combinables, con estas combinaciones manteniendo un sentido.

__Expresividad:__ Un lenguaje es expresivo si sus herramientas permiten expresar la naturaleza del problema.

**Simplicidad:** Programas sencillos de leer y escribir. Lenguaje fácil de enseñar y aprender.

**Legibilidad:** es una propiedad que permite la *modificabilidad* y la *mantenibilidad* de los programas. Sus elementos son: semántica, sintáxis, extructura de datos y estructuras de control.

__Abstracción:__ Uso de estructuras u operaciones complejas de forma simple; ocultamiento de la complejidad y los detalles.

__Confiabilidad:__ Checkeo de tipos y manejo de excepciones, para corregir y gestionar errores.

__Fiabilidad:__ El lenguaje aporta el mecanismo para la comprobación de la correctitud de los programas. 




### Lenguaje ADA
-----

### Ejercicio 5

> Describa las características más relevantes de Ada, referida a:
>- Tipos de datos
>- Tipos abstractos de datos – paquetes
>- Estructuras de datos
>- Manejo de excepciones
>- Manejo de concurrencia

__Tipos de datos:__ Los tipos de datos en ADA se pueden clasificar en:
- No estructurados
    - Discreto
        -*Enteros*: Integer, natural, positive.
        - *Enumerativos*: boolean, character.
    - Real
        - *Coma flotante*
        - *Coma fija*
- Estructurados
    - Vector: *Arrays*, *strings*
    - Registros: *record*
    - Tareas: *task*
- Puntero: *access*
    - Puntero a objetos
    - Puntero a subprogramas


__Tipos abstractos de datos - Paquetes__

Formalmente un programa en Ada se estructura en unidades distribuidas en uno o varios ficheros. Las unidades pueden ser:
- __Subprogramas:__ definen algoritmos y se clasifican en procedimientos y funciones.
paquetes (package).- definen módulos que son colecciones de entidades (tipos, constantes, subprogramas, ...).
- __Tareas (task):__ definen acciones que pueden ejecutarse en paralelo con otras.
- __Unidades protegidas (protected unit):__ sirven para coordinar la compartición de datos entre tareas concurrentes.
- __Unidades genéricas:__ sirven para definir componentes reusables.

```ada
package Manejo_De_Claves is 
        type Clave is private; 
        Clavenula : constant Clave; 
        procedure Tomar_Clave(C : out Clave); 
        function "<"(X, Y : in Clave) return Boolean; 
    private 
        Max : constant := 2 ** 16 - 1; 
        type Clave is range 0 .. Max; 
        Clavenula : constant Clave := 0; 
    end Manejo_De_Claves;
```

__Manejo de excepciones:__

En el estándar de Ada existen excepciones predefinidas:
- `Constraint_error`: Ocurre cuando  se intenta asignar un valor no válido a una variable o acceder a una posición de un array fuera del rango permitido.
- `Program_error`: Cuando
- `Storage_error`: Se agota la memoria disponible.
- `Tasking_error`: Relacionado con errores en programas concurrentes.

Se pueden lanzar excepciones manualmente con la la sentencia `raise`.

Cuando ocurre una excepción podemos:
- Capturarla
- Ignorarla

Si se captura enconces cabe:
1. Controlarla e intentar que el programa continúe su ejecución.
2. Reenviarla a otra parte del programa.

```ada
exeption
    when Data_error =>  --se controla la excepción y se
                        --recupera la ejecución del programa
    put_line("Por favor, teclee correctamente");
    skip_line;
end;

```

__Task:__

En Ada un task es un proceso secuencial que _puede ser ejecutada paralelamente_. Es la representación explícita de un proceso (o tarea).

```ada
cuerpo_tarea ::=
  task body identificador is --parte declarativa

  begin
    secuencia_de_sentencias
  end identificador;
```

__Concurrencia:__
Ada es un lenguaje que soporta concurrencia de forma nativa.
Las `task` se pueden ejecutar concurrentemente. Existen mecanismos para sincronización de tareas como `accept` y `select`.


### Lenguaje Java
-----

#### Ejercicio 6
>Diga para qué fue, básicamente, creado Java.¿Qué cambios le introdujo a la Web?
¿Java es un lenguaje dependiente de la plataforma en dónde se ejecuta? ¿Porqué?

Java es un lenguaje de propósito general, orientado a objetos, concurrente que fue diseñado para tener tan pocas dependencias de implementación como fuera posible. Bajo el lema __WORA__ _write once, run anywhere_ se buscaba que el desarrollador escriban un programa una vez y pueda ser corrido en cualquier plataforma.
Eso quiere decir que un código que es compilado en una plataforma no debe ser recompilado para correr en otra.
De ese trabajo se encarga la __JVM__ _Java virtual machine_.
En la web, introdujo pequeños programas llamados _applets Java_ que consistió en programas incrustados en una página web. Estas _miniaplicaciones_ se ejecutan en una JVM instalada en el navegador como plugin.

>¿Sobre cuales lenguaje está basado?
El lenguaje Java está sintácticamente basado en _C++_.

>​ ¿Qué son los applets? ¿Qué son los servlets?
- __Appets__ (descrito) arriba.
- __Servlets:__ Son componentes de la parte del servidor de Java EE encargados de generar respuestas a las peticiones recibidas de los clientes.

### Lenguaje C
----
### Ejercicio 9:
>¿Cómo es la estructura de un programa escrito en C? ¿Existe anidamiento de
funciones?

```c
/* Inclusión de archivos */
#include <stdio.h>

/* Aquí se pueden incluir funciones, variables globales, etc */

/* Función principal */
int main (int argc,char **argv)
{
   /* Cuerpo del programa principal */
   return 0; // por defecto se espera que el main retorne un int. 
}
```
El C estándar no soporta anidamiento de funciones, es decir, no se pueden declarar funciones dentro de otra. 
El compilador dará el siguiente error: `error: function definition is not allowed here`.
Sin embargo con las extensiones del compilador gcc de GNU es posible hacer anidamiento de funciones o `Nested functions`.

### Ejercicio 10:
> Describa el manejo de expresiones que brinda el lenguaje.

saraza


### Lenguajes Python, Ruby, PHP
----

### Ejercicio 11
> ¿Qué tipo de programas se pueden escribir con cada uno de estos lenguajes? ¿A que
paradigma responde cada uno? ¿Qué características determinan la pertenencia a cada paradigma?

| Caracteristica   | Python                                                      | Ruby                              | PHP                                                                     |
|------------------|-------------------------------------------------------------|-----------------------------------|-------------------------------------------------------------------------|
| Paradigma/s      | - Imperativo  - Orientado a objetos - Funcional - Reflexivo | - Orientado a objetos - Reflexivo | - Imperativo - Funcional - Orientado a objetos - Procedural - Reflexivo |

Ruby, PHP y Python son lenguajes interpretados y orientado a objetos. Por este motivo son frecuentemente utilizados para generar scripts.
Los tres tienen frameworks que permiten extender sus funciones fácilmente para escribir determinado tipos de programas como pueden ser Rails para Ruby y Symfony para PHP que nos permiten desarrollar páginas web.


### Ejercicio 12
> Cite otras características importantes de Python, Ruby, PHP, Gobstone y Processing.
Por ejemplo: tipado de datos, como se organizan los programas, etc.


| Caracteristica   | Python                          | Ruby                            | PHP                            | Processing                      |
|------------------|---------------------------------|---------------------------------|--------------------------------|---------------------------------|
| Sistema de tipos | - Fuertemente tipado - Dinámico | - Fuertemente tipado - Dinámico | - Débilmente tipado - Dinámico | - Fuertemente tipado - Estático |

*blabla

### Lenguaje Javascript
------

### Ejercicio 13​
> ¿A qué tipo de paradigma corresponde este lenguajes? ¿A qué tipo de Lenguaje
pertenece?

Javascript es un lenguaje interpretado. Se define como basado en prototipos, imperativo, débilmente tipado y dinámico.

### Ejercicio 14
>Cite otras características importantes de javascript. Tipado de datos, excepciones,variables, etc.

El tipado de datos, como se dijo arriba, es débilmente tipado y dinámico. También usa el estílo de tipicación dinámica de datos _duck typing_.

Javascript suele ejecutarse en un navegador web (lado cliente) aunque actualmente se lo ve también ejecutándose del lado del servidor. Una de las implementaciones mas conocidas para Javascript del lado del servidor es _Node.js_.

*Carasteristicas:*
- Imperativo y estructurado
- Dinámico
- Funcional: Las funciones son objetos. Pueden anidarse.
- Prototípico: Usa prototipos en vez de clases para uso de herencia.
