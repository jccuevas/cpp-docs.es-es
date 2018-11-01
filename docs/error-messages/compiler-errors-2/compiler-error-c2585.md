---
title: Error del compilador C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 812ab15aacd1f6a215c6a5beb7781983859fe858
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593263"
---
# <a name="compiler-error-c2585"></a>Error del compilador C2585

conversión explícita a 'type' es ambigua

El tipo de conversión puede producir más de un resultado.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Convertir un tipo de clase o estructura en función de herencia múltiple. Si el tipo hereda la misma clase base más de una vez, la función de conversión o un operador debe utilizar la resolución de ámbito (`::`) para especificar cuál de las clases heredadas a usar en la conversión.

1. Se ha definido un operador de conversión y un constructor que hace la misma conversión.