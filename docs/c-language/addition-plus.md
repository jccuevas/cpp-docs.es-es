---
title: Suma (+) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d41fe0369235bbdaf6723d01fdaf4bbf552a9ea5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="addition-"></a>Suma (+)
El operador de suma (**+**) hace que los dos operandos se sumen. Ambos operandos pueden ser tipos enteros o de punto flotante, o un operando puede ser un puntero y el otro un entero.  
  
 Cuando se suma un entero a un puntero, el valor entero (*i*) se convierte multiplicándolo por el tamaño del valor que direcciona el puntero. Después de la conversión, el valor entero representa las posiciones de memoria *i*, donde cada posición tiene la longitud especificada por el tipo de puntero. Cuando el valor entero convertido se suma al valor del puntero, el resultado es un nuevo valor de puntero que representa las posiciones de dirección *i* de la dirección original. El nuevo valor de puntero direcciona un valor del mismo tipo que el valor del puntero original y, por consiguiente, es igual que la indexación de matrices (vea [Matrices unidimensionales](../c-language/one-dimensional-arrays.md) y [Matrices multidimensionales](../c-language/multidimensional-arrays-c.md)). Si el puntero de la suma apunta fuera de la matriz, excepto en la primera ubicación más allá de la parte alta, el resultado es indefinido. Para más información, vea [Aritmética de punteros](../c-language/pointer-arithmetic.md).  
  
## <a name="see-also"></a>Vea también  
 [Operadores de adición de C](../c-language/c-additive-operators.md)