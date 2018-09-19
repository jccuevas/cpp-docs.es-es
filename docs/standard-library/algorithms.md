---
title: Algoritmos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5338ddeb802d13d100e5e3026152793f866c90f6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961030"
---
# <a name="algorithms"></a>Algoritmos

Los algoritmos son una parte fundamental de la biblioteca estándar de C++. Los algoritmos no funcionan con los contenedores en sí, sino con iteradores. Por lo tanto, la mayoría de los contenedores de la biblioteca estándar de C++, si no todos, pueden usar el mismo algoritmo. En esta sección se tratan las convenciones y la terminología de los algoritmos de la biblioteca estándar de C++.

## <a name="remarks"></a>Comentarios

La descripción de las funciones de plantilla de algoritmo emplea varias frases de forma abreviada:

- La frase "en el intervalo [*A*, *B*)" significa la secuencia de cero o más valores discretos que comienza con *A* y termina con *B*, sin incluirlo. Un intervalo es válido únicamente si *B* es accesible desde *A*; puede almacenar *A* en un objeto *N* (*N* = *A*), incrementar el objeto cero o más veces (++*N*) y hacer que el objeto sea igual a *B* después de un número finito de incrementos (N == B *).*

- La frase "cada *N* en el intervalo [*A*, *B*)" significa que *N* comienza con el valor *A* y se incrementa cero o más veces hasta que es igual que el valor *B*. El caso *N* == *B* no está en el intervalo.

- La frase "el valor más bajo de *N* en el intervalo [*A*, *B*) tal que *X*" significa que la condición *X* se comprueba para cada *N* del intervalo [*A*, *B*) hasta que la condición *X* se cumple.

- La frase "el valor más alto de *N* en el intervalo [*A*, *B*) tal que *X*" significa que *X* se comprueba para cada *N* del intervalo [*A*, *B*). La función almacena en `K` una copia de *N* cada vez que la condición *X* se cumple. Si se produce cualquier almacenamiento de este tipo, la función sustituye el valor final de *N*, que es igual a *B*, con el valor de `K`. Pero en el caso de un iterador de acceso aleatorio o bidireccional también puede significar que *N* comienza con el valor más alto del intervalo y va disminuyendo en el intervalo hasta que la condición *X* se cumple.

- Las expresiones como *X* - *Y*, donde *X* e *Y* pueden ser iteradores distintos de los iteradores de acceso aleatorio, se han diseñado en el sentido matemático. La función no evalúa necesariamente al operador **-** si debe determinar dicho valor. Lo mismo se aplica a expresiones como *X* + *N* y *X* - *N*, donde *N* es un tipo entero.

Varios algoritmos hacen uso de un predicado que realiza una comparación en pares, como con `operator==`, para producir un **bool** resultado. La función de predicado `operator==`, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos. Debe producir el mismo **bool** resultado cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.

Varios algoritmos hacen uso de un predicado que debe imponer una ordenación débil estricta en pares de elementos de una secuencia. Para el predicado `pr`(*X*, *Y*):

- Estricta significa que `pr`(*X*, *X*) es falso.

- Débil significa que *X* e *Y* tienen una ordenación equivalente si !`pr`(*X*, *Y*) && !`pr`(*Y*, *X*) (no es necesario definir *X* == *Y*).

- Ordenación significa que `pr`(*X*, *Y*) && `pr`(*Y*, Z) implica `pr`(*X*, Z).

Algunos de estos algoritmos usan el predicado *X* \< *Y* de forma implícita. Otros predicados que normalmente cumplen el requisito de ordenación débil estricta son *X* > *Y*, `less`(*X*, *Y*), y `greater`(*X*, *Y*). Pero tenga en cuenta que predicados como *X* \<= *Y* y *X* >= *Y* no cumplen este requisito.

Una secuencia de elementos designados por los iteradores del intervalo [`First`, `Last`) es una secuencia ordenada por operator**<** si, para cada *N* del intervalo [0, `Last` - `First`) y para cada *M* del intervalo (N, `Last` - `First`), el predicado !(\*(`First` + *M*) < \*(*First* + *N*)) es verdadero. (Tenga en cuenta que los elementos se ordenan en orden ascendente). La función de predicado `operator<`, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos. Debe producir el mismo resultado `bool` cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando. Además, debe imponer una ordenación débil estricta en los operandos que compara.

Una secuencia de elementos designados por los iteradores del intervalo [`First`, `Last`) es un montón, ordenada por `operator<` si, para cada *N* en el intervalo [1, `Last`  -  `First`) el ¡predicado! (\*`First` < \*(`First` + *N*)) es true. (El primer elemento es el mayor). Si no se conoce su estructura interna solo a las funciones de plantilla [make_heap](../standard-library/algorithm-functions.md#make_heap), [pop_heap](../standard-library/algorithm-functions.md#pop_heap), y [push_heap](../standard-library/algorithm-functions.md#push_heap). Igual que con una secuencia ordenada, la función de predicado `operator<`, o cualquiera que la sustituya, no debe modificar ninguno de sus operandos, y debe imponer una ordenación débil estricta en los operandos que compara. Debe producir el mismo **bool** resultado cada vez que se evalúa y debe producir el mismo resultado si una copia de cualquiera de los operandos se sustituye por el operando.

Los algoritmos de la biblioteca estándar de C++ se encuentran en los archivos de encabezado [\<algorithm>](../standard-library/algorithm.md) y [\<numeric>](../standard-library/numeric.md).

## <a name="see-also"></a>Vea también

[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
