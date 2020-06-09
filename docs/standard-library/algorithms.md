---
title: Algoritmos
ms.date: 10/18/2018
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
ms.openlocfilehash: 4b49b3c296d3afcbb26af028dc0b4a885444a897
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617631"
---
# <a name="algorithms"></a>Algoritmos

Los algoritmos son una parte fundamental de la biblioteca estándar de C++. Los algoritmos no funcionan con los contenedores en sí, sino con iteradores. Por lo tanto, la mayoría de los contenedores de la biblioteca estándar de C++, si no todos, pueden usar el mismo algoritmo. En esta sección se tratan las convenciones y la terminología de los algoritmos de la biblioteca estándar de C++.

## <a name="remarks"></a>Observaciones

La descripción de las funciones de plantilla de algoritmo emplea varias frases de forma abreviada:

- La frase "en el intervalo \[ *A*, *B*)" significa la secuencia de cero o más valores discretos que comienzan *A* con hasta, pero sin incluir *B*. Un intervalo solo es válido si *B* es accesible desde *a;* puede almacenar *un* en un objeto *n* (*n*  =  *A*), incrementar el objeto cero o más veces (+ +*N*) y hacer que el objeto sea igual a *B* después de un número finito de incrementos (*N*  ==  *B*).

- La frase "cada *n* en el intervalo \[ *a*, *B*)" significa que *N* comienza con el valor *a* y se incrementa cero o más veces hasta que es igual al valor *B*. El caso *N*  ==  *B* no está en el intervalo.

- La frase "el valor más bajo de *N* en el intervalo \[ *a*, *b*) tal *que x*" significa que la condición *x* se determina para cada *N* del intervalo \[ *a*, *b*) hasta que se cumple la condición *x* .

- La frase "el valor más alto de *N* en el intervalo \[ *a*, *b*), de modo que *x* significa que *x* se determina para cada *N* del intervalo \[ *a*, *b*). La función almacena en *K* una copia de *N* cada vez que se cumple la condición *X* . Si se produce este tipo de almacenamiento, la función reemplaza el valor final de *N*, que es igual a *B*, con el valor de *K*. En el caso de un iterador de acceso aleatorio o bidireccional, sin embargo, también puede significar que *N* comienza con el valor más alto del intervalo y se disminuye en el intervalo hasta que se cumple la condición *X* .

- Las expresiones como *x*  -  *Y*y, donde *x* e *Y* y pueden ser iteradores distintos de los iteradores de acceso aleatorio, están diseñadas en el sentido matemático. La función no evalúa necesariamente el operador **-** si debe determinar este tipo de valor. Lo mismo se aplica también a las expresiones como *x*  +  *n* y *x*  -  *n*, donde *N* es un tipo entero.

Varios algoritmos hacen uso de un predicado que realiza una comparación en pares, como con `operator==` , para producir un resultado **booleano** . La función de predicado `operator==`, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos. Debe producir el mismo resultado **booleano** cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.

Varios algoritmos hacen uso de un predicado que debe imponer una ordenación débil estricta en pares de elementos de una secuencia. Para el predicado *Pred*(*X*, *Y*):

- STRICT significa que *Pred*(*x*, *x*) es false.

- Débil significa que *X* e *y tienen una* ordenación equivalente si \! *se Pred*(*x*, *Y*)  && \! *Pred*(*Y*, *x*) (*X*  ==  no es necesario definir x*y* ).

- La ordenación significa que una *Pred*(*x*, *Y*)  && *Pred*(*y*, *z*) implica una *Pred*(*x*, *z*).

Algunos de estos algoritmos usan implícitamente el predicado *X* \< *Y*. Other predicates that typically satisfy the strict weak ordering requirement are *X* > *y*, `less` (*x*, *Y*) y `greater` (*x*, *y*). Tenga en cuenta, sin embargo, que los predicados como *X* \<= *Y* and *X* > =  *Y* no cumplen este requisito.

Una secuencia de elementos designados por los iteradores del rango \[ *First*, *Last*) es una secuencia ordenada por Operator **<** si, para *cada N* en el intervalo de \[ 0, *Last*  -  *primero*) y para cada *M* del intervalo (*n*, *Last*  -  *primero*), el predicado \! ( \* (*primero*  +  *M*) < \* (*First*  +  *N*)) es true. (Tenga en cuenta que los elementos se ordenan en orden ascendente). La función de predicado `operator<` , o cualquier reemplazo, no debe modificar ninguno de sus operandos. Debe producir el mismo resultado **booleano** cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando. Además, debe imponer una ordenación débil estricta en los operandos que compara.

Una secuencia de elementos designados por los iteradores en el intervalo \[ `First` , `Last` ) es un montón ordenado por `operator<` si, para cada *N* en el intervalo \[ 1, *último*  -  *primero*, el predicado \! ( \* _primero_  <  \* (*primero*  +  *N*)) es true. (El primer elemento es el mayor). De lo contrario, su estructura interna solo se conoce en las funciones de plantilla [make_heap](algorithm-functions.md#make_heap), [pop_heap](algorithm-functions.md#pop_heap)y [push_heap](algorithm-functions.md#push_heap). Al igual que con una secuencia ordenada, la función de predicado `operator<` , o cualquier reemplazo, no debe modificar ninguno de sus operandos y debe imponer una ordenación débil estricta en los operandos que compara. Debe producir el mismo resultado **booleano** cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.

Los algoritmos de la biblioteca estándar de C++ se encuentran en los [\<algorithm>](algorithm.md) [\<numeric>](numeric.md) archivos de encabezado y.

## <a name="see-also"></a>Consulte también

[Referencia de la biblioteca estándar de C++](cpp-standard-library-reference.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](thread-safety-in-the-cpp-standard-library.md)
