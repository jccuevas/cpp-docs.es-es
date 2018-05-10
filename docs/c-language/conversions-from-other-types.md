---
title: Conversiones de otros tipos | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e919782022ee64f657611a14d6eae6173a67b8c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
