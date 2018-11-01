---
title: Interpretación del operador de subíndice
ms.date: 08/27/2018
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
ms.openlocfilehash: 1c3d5bca66cb294503805fd5b7691331ac380ae5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446610"
---
# <a name="interpretation-of-subscript-operator"></a>Interpretación del operador de subíndice

Al igual que otros operadores, el operador de subíndice (**\[]**) puede definirse por el usuario. El comportamiento predeterminado del operador de subíndice, si no está sobrecargado, consiste en combinar el nombre de la matriz y el subíndice usando el método siguiente:

\*((*nombre de la matriz*) + (*subíndice*))

Como en toda suma que implica tipos de puntero, el ajuste de escala se realiza automáticamente para que se produzca el ajuste correspondiente al tamaño del tipo. Por lo tanto, el valor resultante no es *subíndice* bytes desde el origen de *nombre de la matriz*; en su lugar, es el *subíndice*elemento de la matriz. (Para obtener más información acerca de esta conversión, consulte [operadores aditivos](../cpp/additive-operators-plus-and.md).)

De igual forma, para las matrices multidimensionales, la dirección se deriva usando el método siguiente:

((*nombre de la matriz*) + (*subíndice*1 \* *max*2 \* *max*3 \* ... \* *max*n) + (*subíndice*2 \* *max*3 \* ... \* *max*n) +... + *subíndice*n))

## <a name="see-also"></a>Vea también

[Matrices](../cpp/arrays-cpp.md)<br/>
