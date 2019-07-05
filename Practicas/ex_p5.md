Pila de ejecución

Arbol de anidamiento

    Ejemplo corto
    /           \
    B            A
                 |
                 f

Se sigue la cadena estática

Registro de activación con registro corto
PR
LE *1
LD
a|0
b|-1
ProcA
ProcB
VR
-------
ProcA
PR
LE *1
LD *1
a|
Fun f
VR = 3

b:= f-a
b(*1):= 3-3
b(*1):=0

----------------
Fun f
PR
LE *2
LD *2
VR 
a:= b+4
--------------------- (termina)
ProcB
PR
LE *1
LD *2
f | 1
VR

a:= f-3
a(*1):= 1-3
a(*1):= -2

-------------

Imprime
-2
0

Tener en cuenta el link estático y el dinámico.
Cuando es link estático se sigue el link estático cuando no está en el entorno.
La cadena dinámica los buscará por el link dinámico.



Cadena dinámica



seguimos el liknk estatico
a(*2):=-1+4
a(*2):= 3