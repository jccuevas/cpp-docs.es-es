---
title: Advertencia del compilador (nivel 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 0a9ceb332888e306b8cb3bcbe1832f773d02d63d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401948"
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