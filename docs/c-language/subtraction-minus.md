---
title: Resta (-) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b32986513a94c20f0fb0cd1b4c65dd21e8c9e8aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="subtraction--"></a>Resta (-)
El operador de sustracción (**-**) resta el segundo operando del primero. Ambos operandos pueden ser tipos enteros o de punto flotante, o un operando puede ser un puntero y el otro un entero.  
  
 Cuando se restan dos punteros, la diferencia se convierte en un valor entero con signo mediante la división de la diferencia por el tamaño de un valor de tipo que los punteros direccionan. El tamaño del valor entero se define mediante el tipo **ptrdiff_t** en el archivo de inclusión estándar STDDEF.H. El resultado representa el número de posiciones de memoria de ese tipo entre las dos direcciones. Solo se garantiza que el resultado es significativo para dos elementos de la misma matriz, como se describe en [Aritmética de punteros](../c-language/pointer-arithmetic.md).  
  
 Cuando un valor entero se resta de un valor de puntero, el operador de sustracción convierte el valor entero (*i*) multiplicándolo por el tamaño del valor que el puntero direcciona. Después de la conversión, el valor entero representa las posiciones de memoria *i*, donde cada posición tiene la longitud especificada por el tipo de puntero. Cuando el valor entero convertido se resta del valor de puntero, el resultado representa las posiciones de dirección de memoria *i* antes de la dirección original. El nuevo puntero señala a un valor del tipo direccionado por el valor de puntero original.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de adición de C](../c-language/c-additive-operators.md)