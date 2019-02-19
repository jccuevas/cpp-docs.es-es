---
title: Resta (-)
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
ms.openlocfilehash: 5c9510cf3708ef049b5dac213fa3de894fcd4a07
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147612"
---
# <a name="subtraction--"></a>Resta (-)

El operador de sustracción (**-**) resta el segundo operando del primero. Ambos operandos pueden ser tipos enteros o de punto flotante, o un operando puede ser un puntero y el otro un entero.

Cuando se restan dos punteros, la diferencia se convierte en un valor entero con signo mediante la división de la diferencia por el tamaño de un valor de tipo que los punteros direccionan. El tamaño del valor entero se define mediante el tipo **ptrdiff_t** en el archivo de inclusión estándar STDDEF.H. El resultado representa el número de posiciones de memoria de ese tipo entre las dos direcciones. Solo se garantiza que el resultado es significativo para dos elementos de la misma matriz, como se describe en [Aritmética de punteros](../c-language/pointer-arithmetic.md).

Cuando un valor entero se resta de un valor de puntero, el operador de sustracción convierte el valor entero (*i*) multiplicándolo por el tamaño del valor que el puntero direcciona. Después de la conversión, el valor entero representa las posiciones de memoria *i*, donde cada posición tiene la longitud especificada por el tipo de puntero. Cuando el valor entero convertido se resta del valor de puntero, el resultado representa las posiciones de dirección de memoria *i* antes de la dirección original. El nuevo puntero señala a un valor del tipo direccionado por el valor de puntero original.

## <a name="see-also"></a>Vea también

[Operadores de adición de C](../c-language/c-additive-operators.md)
