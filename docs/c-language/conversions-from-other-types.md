---
title: Conversiones de otros tipos
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: f9f2d73e57c576dcf8afed008a74e5e7dd9b9d6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448664"
---
# <a name="conversions-from-other-types"></a>Conversiones de otros tipos

Puesto que un valor **enum** es un valor **int** por definición, las conversiones de y a valores **enum** son iguales que las del tipo **int**. Para el compilador de C de Microsoft, un entero es igual que **long**.

**Específicos de Microsoft**

No se permite ninguna conversión entre tipos de estructura o unión.

Cualquier valor se puede convertir al tipo **void**, pero el resultado de dicha conversión solo se puede utilizar en un contexto donde se descarte un valor de expresión, como una instrucción de expresión.

El tipo **void**, por definición, no tiene ningún valor. Por consiguiente, no se puede convertir a ningún otro tipo, y otros tipos no pueden convertirse a **void** por asignación. Sin embargo, puede convertir un valor al tipo **void** explícitamente, como se describe en [Conversiones de tipos](../c-language/type-cast-conversions.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Conversiones de asignación](../c-language/assignment-conversions.md)
