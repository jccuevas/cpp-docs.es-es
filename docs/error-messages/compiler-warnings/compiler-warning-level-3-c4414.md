---
title: Compilador advertencia (nivel 3) C4414 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd0868fea89cd868178956c0aba171ce6525bd75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043214"
---
# <a name="compiler-warning-level-3-c4414"></a>Advertencia del compilador (nivel 3) C4414

'function': salto short a la función ha convertido en near

Los saltos short generan una instrucción compacta que se dirige a una dirección dentro de un intervalo limitado de la instrucción. La instrucción incluye un desplazamiento short que representa la distancia entre el salto y la dirección de destino, la definición de función. Durante la vinculación de una función puede ser mover o están sujetas a optimizaciones en tiempo de vínculo que consiguen que dicha función puede moverse fuera del intervalo alcanzable desde un desplazamiento short. El compilador debe generar un registro especial para el salto, que requiere la instrucción jmp NEAR o FAR. El compilador realiza la conversión.

Por ejemplo, el código siguiente genera C4414:

```
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```