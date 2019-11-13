---
title: ADVERTENCIA del compilador (nivel 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 43570cd43ca6e9d4f892dc577f615e9fa980e561
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051583"
---
# <a name="compiler-warning-level-3-c4414"></a>ADVERTENCIA del compilador (nivel 3) C4414

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