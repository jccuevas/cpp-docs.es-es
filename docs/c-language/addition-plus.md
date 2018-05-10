---
title: Suma (+) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3fcdb309e65c822e511b9cfd4a9ce7255be235a4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="addition-"></a>Suma (+)
El operador de suma (**+**) hace que los dos operandos se sumen. Ambos operandos pueden ser tipos enteros o de punto flotante, o un operando puede ser un puntero y el otro un entero.  
  
 Cuando se suma un entero a un puntero, el valor entero (*i*) se convierte multiplicándolo por el tamaño del valor que direcciona el puntero. Después de la conversión, el valor entero representa las posiciones de memoria *i*, donde cada posición tiene la longitud especificada por el tipo de puntero. Cuando el valor entero convertido se suma al valor del puntero, el resultado es un nuevo valor de puntero que representa las posiciones de dirección *i* de la dirección original. El nuevo valor de puntero direcciona un valor del mismo tipo que el valor del puntero original y, por consiguiente, es igual que la indexación de matrices (vea [Matrices unidimensionales](../c-language/one-dimensional-arrays.md) y [Matrices multidimensionales](../c-language/multidimensional-arrays-c.md)). Si el puntero de la suma apunta fuera de la matriz, excepto en la primera ubicación más allá de la parte alta, el resultado es indefinido. Para más información, vea [Aritmética de punteros](../c-language/pointer-arithmetic.md).  
  
## <a name="see-also"></a>Vea también  
 [Operadores de adición de C](../c-language/c-additive-operators.md)