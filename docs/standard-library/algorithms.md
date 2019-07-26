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
ms.openlocfilehash: d363dc3f06222121ac5efc79b30516ebd55ff539
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456484"
---
# <a name="algorithms"></a>Algoritmos

Los algoritmos son una parte fundamental de la biblioteca estándar de C++. Los algoritmos no funcionan con los contenedores en sí, sino con iteradores. Por lo tanto, la mayoría de los contenedores de la biblioteca estándar de C++, si no todos, pueden usar el mismo algoritmo. En esta sección se tratan las convenciones y la terminología de los algoritmos de la biblioteca estándar de C++.

## <a name="remarks"></a>Comentarios

La descripción de las funciones de plantilla de algoritmo emplea varias frases de forma abreviada:

- La frase "en el intervalo \[ *A*, *B*)" significa la secuencia de cero o más valores discretos que comienzan *con hasta* , pero sin incluir *B*. Un intervalo solo es válido si *B* es accesible desde *a;* puede almacenar *un* en un objeto *n* (*n* = *A*), incrementar el objeto cero o más veces (+ +*N*) y hacer que el objeto Compare sea igual a *B* . después de un número finito de incrementos (*N* == *B*).

- La frase "cada *n* en el intervalo \[ *a*, *B*)" significa que *N* comienza con el valor *a* y se incrementa cero o más veces hasta que es igual al valor *B*. El caso *N* == *B* no está en el intervalo.

- La frase "el valor más bajo de *N* en el \[intervalo *a*, *b*) tal *que x*" significa que la *condición x* se determina para cada *N* del intervalo \[ *a*, *b*) hasta que el se cumple la condición *X* .

- La frase "el valor más alto *de N* en el \[intervalo *a*, *b*), de modo que *x* significa que *x* se determina para cada *N* del intervalo \[ *a*, *b*). La función almacena en *K* una copia de *N* cada vez que se cumple la condición *X* . Si se produce este tipo de almacenamiento, la función reemplaza el valor final de *N*, que es igual a *B*, con el valor de *K*. Pero en el caso de un iterador de acceso aleatorio o bidireccional también puede significar que *N* comienza con el valor más alto del intervalo y va disminuyendo en el intervalo hasta que la condición *X* se cumple.

- Las expresiones como *X* - *Y*, donde *X* e *Y* pueden ser iteradores distintos de los iteradores de acceso aleatorio, se han diseñado en el sentido matemático. La función no evalúa necesariamente el operador **-** si debe determinar este tipo de valor. Lo mismo se aplica a expresiones como *X* + *N* y *X* - *N*, donde *N* es un tipo entero.

Varios algoritmos hacen uso de un predicado que realiza una comparación en pares, como `operator==`con, para producir un resultado **booleano** . La función de predicado `operator==`, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos. Debe producir el mismo resultado **booleano** cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.

Varios algoritmos hacen uso de un predicado que debe imponer una ordenación débil estricta en pares de elementos de una secuencia. Para el predicado *Pred*(*X*, *Y*):

- STRICT significa que *Pred*(*x*, *x*) es false.

- Débil significa que *X* e *y* tienen una ordenación equivalente \!si *Pred*(*X*, *Y*) & \!& *Pred*(*Y*, *x*) (*x* == *y* no debe definirse).

- La ordenación significa que una *Pred*(*x*, *Y*) & & *Pred*(*Y*, *z*) implica una *Pred*(*x*, *z*).

Algunos de estos algoritmos usan el predicado *X* \< *Y* de forma implícita. Otros predicados que normalmente cumplen el requisito de ordenación débil  > estricta son X `less`*y*, (*x*, *Y*) `greater`y (*x*, *y*). Pero tenga en cuenta que predicados como *X* \<= *Y* y *X* >= *Y* no cumplen este requisito.

Una secuencia de elementos designados por los iteradores en \[el rango *First*, *Last*) es una secuencia ordenada **<** por Operator si, para cada *N* del \[intervalo de 0, *último* - *primero* ) y para cada *M* del intervalo (*N*, *último* - *primero*) del predicado \!(\*(*primero* + *M*) < \*(First + *N*)) es true. (Tenga en cuenta que los elementos se ordenan en orden ascendente). La función de predicado `operator<`, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos. Debe producir el mismo resultado **booleano** cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando. Además, debe imponer una ordenación débil estricta en los operandos que compara.

Una secuencia de elementos designados por los iteradores en \[el `Last`intervalo `First`,) es un montón `operator<` ordenado por si, para cada *N* en \[el intervalo 1, *último* - *primero*). \!Predicate\*(First < (primerN + )) es true.\* (El primer elemento es el mayor). De lo contrario, su estructura interna solo se conoce en las funciones de plantilla [make_heap](../standard-library/algorithm-functions.md#make_heap), [pop_heap](../standard-library/algorithm-functions.md#pop_heap)y [push_heap](../standard-library/algorithm-functions.md#push_heap). Al igual que con una secuencia ordenada, la `operator<`función de predicado, o cualquier reemplazo, no debe modificar ninguno de sus operandos y debe imponer una ordenación débil estricta en los operandos que compara. Debe producir el mismo resultado **booleano** cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.

Los algoritmos de la biblioteca estándar de C++ se encuentran en los archivos de encabezado [\<algorithm>](../standard-library/algorithm.md) y [\<numeric>](../standard-library/numeric.md).

## <a name="see-also"></a>Vea también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
