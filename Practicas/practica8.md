# Conceptos 2019
## Práctica 8 - Excepciones

_Objetivo: ​ Conocer e interpretar los distintos modelos de excepciones que implementan los lenguajes de programación._

#### Ejercicio 1:​ ¿Explique claramente a qué se denomina excepción?

Una excepción es una situación anómala que se da en la ejecución de un programa y se supone que ocurre con poca frecuencia.

#### Ejercicio 2​ : ¿Qué debería proveer un lenguaje para el manejo de las excepciones? ¿Todos los lenguajes lo proveen?

Para que un lenguaje trate excepciones debe proveer:
- Un modo de definirlas
- Una forma de alcanzarlas, invocarlas
- Una forma de manejarlas
- Un criterio de continuación

#### Ejercicio 3:​ ¿Qué ocurre cuando un lenguaje no provee manejo de excepciones? ¿Se podría simular? Explique cómo lo haría

Definiendo procedimientos para tratar la excepción y haciendo if en lugares donde podría haber una excepción. En caso de ser true la condición se llama a la excepción preparada.