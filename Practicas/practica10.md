# Conceptos 2019
## Práctica 10 - Paradigmas de Lenguajes de Programación

_Objetivo: poder reconocer las diferentes características que poseen los paradigmas de programación_

#### Ejercicio 1: Un programa en un lenguaje procedural es una secuencia de instrucciones o comandos que se van ejecutando y producen cambios en las celdas de memoria, a través de las sentencias de asignación. ¿Qué es un programa escrito en un lenguaje funcional? y ¿Qué rol cumple la computadora?

En lenguaje funcional es un lenguaje que respeta el paradigma funcional, que básicamente es que los programas se componen de funciones. Muy popular en la resolución de problemas de inteligencia artificial, matemática, lógica, procesamiento paralelo.

Características de los lenguajes funcionales
- Define un conjunto de datos
- Provee un conjunto de funciones primitivas
- Provee un conjunto de formas funcionales
- Requiere de un operador de aplicación
- Semántica basada en valores
- Transparencia referencial
- Regla de mapeo basada en combinación o composición
- Las funciones de primer orden



#### Ejercicio 2:​ ¿Cómo se define el lugar donde se definen las funciones en un lenguaje funcional?


#### Ejercicio 3:​ ¿Cuál es el concepto de variables en los lenguajes funcionales?

Se refiere a variables matemática y NO a lugares en memoria.

#### Ejercicio 4:​ ¿Qué es una expresión en un lenguaje funcional? ¿Su valor de qué depende?

- La expresión es la noción central de la programación Funcional.
- **_Una expresión es su VALOR_**
- El valor de una expresión depende ÚNICAMENTE de los valores de las sub expresiones que la componen.

#### Ejercicio 5: ​ ¿Cuál es la forma de evaluación que utilizan los lenguajes funcionales?

La forma de evaluar expresiones es a través de un mecanismo de REDUCCIÓN o SIMPLIFICACIÓN.
Ejemplo:
```
cuadrado (3 + 4)
    => cuadrado 7 (+)
    => 7 * 7 (cuadrado)
    => 49 (*)
```

#### Ejercicio 6: ​ ¿Un lenguaje funcional es fuertemente tipado? ¿Qué tipos existen? ¿Por qué?

#### Ejercicio 7: ​ ¿Cómo definiría un programa escrito en POO?

“Un programa escrito con un lenguaje OO es un conjunto de OBJETOS que INTERACTÚAN mandándose MENSAJES”

#### Ejercicio 8: Diga cuáles son los elementos más importantes y hable sobre ellos en la programación orientada a objetos.

Los elementos mas importantes en la POO son:
- Objetos:
    - Son entidades que poseen estado interno y comportamiento
    - Es el equivalente a un dato abstracto
- Mensajes:
    - Es una petición de un objeto a otro para que este se comporte de una determinada manera ejecutando uno de sus métodos.
- Métodos:
    - Es un programa que está asociado a un objeto determinado y cuya ejecución solo puede desencadenarse a través de un mensaje recibido por este o por sus descendientes.
- Clases:
    - Es un tipo definido por el usuario que determina las estructuras de datos y las operaciones asociadas a este tipo.
    - Cada objeto pertenece a una clase y recibe de ella su funcionalidad.
    - Primer nivel de abtracción de datos: definimos estructura, comportamiento y tenemos ocultamiento.
    - La información es contenida en el objeto solo puede ser accedida por la ejecución de los métodos correspondientes.
- Instancias de clase:
    - Cada vez que se contruye un objeto se está creando una **instancia** de esa clase.
    - Una instancia es un objeto individualizado por los valores que tomen sus atributos.

#### Ejercicio 9: ​ La posibilidad de ocultamiento y encapsulamiento para los objetos es el primer nivel de abstracción de la POO, ¿cuál es el segundo?

El segundo nivel de abstracción es la HERENCIA entre clases.

#### Ejercicio 10:​ ¿Qué tipos de herencias hay? Cuál usa Smalltalk y C++
