---
title: Advertencia del compilador (nivel 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 4625f6bdb4aa6fe86ca881a8e36e5673e55ccb87
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185599"
---
# <a name="compiler-warning-level-3-c4414"></a>Advertencia del compilador (nivel 3) C4414

' función ': salto corto a función convertida en near

Los saltos cortos generan instrucciones compactas que se bifurcan en una dirección dentro de un intervalo limitado de la instrucción. La instrucción incluye un desplazamiento corto que representa la distancia entre el salto y la dirección de destino, la definición de función. Durante la vinculación, es posible que la función se mueva o esté sujeta a optimizaciones en tiempo de vínculo que hacen que la función se mueva fuera del intervalo accesible desde un desplazamiento corto. El compilador debe generar un registro especial para el salto, que requiere que la instrucción JMP esté cerca o lejos. El compilador realizó la conversión.

Por ejemplo, el código siguiente genera C4414:

```cpp
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
