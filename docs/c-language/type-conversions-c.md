---
title: Conversiones de tipos (C)
ms.date: 11/04/2016
helpviewer_keywords:
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
ms.openlocfilehash: 27dcdbf810199c62b7c267270ad62ed1ed677494
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503360"
---
# <a name="type-conversions-c"></a>Conversiones de tipos (C)

Las conversiones de tipos dependen del operador especificado y del tipo del operando o de los operadores. Las conversiones de tipos se realizan en los casos siguientes:

- Cuando se asigna un valor de un tipo a una variable de un tipo diferente o un operador convierte el tipo del operando o los operandos antes de realizar una operación

- Cuando un valor de un tipo se convierte explícitamente a un tipo diferente

- Cuando se pasa un valor como argumento a una función o cuando se devuelve un tipo de una función

Un carácter, un entero corto o un campo de bits entero, todos con signo o sin él o un tipo de objeto o de enumeración se pueden usar en una expresión siempre que se pueda usar un entero. Si `int` puede representar todos los valores del tipo original, el valor se convierte en `int`; si no, se convierte en `unsigned int`. Este proceso se denomina “promoción entera”. Las promociones enteras conservan el valor. Es decir, se garantiza que el valor después de la promoción es igual que el valor antes de la promoción. Vea [Conversiones aritméticas usuales](../c-language/usual-arithmetic-conversions.md) para obtener más información.

## <a name="see-also"></a>Vea también

[Expresiones y asignaciones](../c-language/expressions-and-assignments.md)