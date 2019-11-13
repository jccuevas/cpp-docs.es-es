---
title: ADVERTENCIA del compilador (nivel 1) C4333
ms.date: 11/04/2016
f1_keywords:
- C4333
helpviewer_keywords:
- C4333
ms.assetid: d3763c52-6110-4da0-84db-5264e3f3f166
ms.openlocfilehash: 0b4e567f07d15b47d3c1f507b43257dac9a49d66
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966053"
---
# <a name="compiler-warning-level-1-c4333"></a>ADVERTENCIA del compilador (nivel 1) C4333

' operador ': desplazamiento a la derecha con una cantidad demasiado grande, pérdida de datos

Una operación de desplazamiento A la derecha era demasiado grande.  Todos los bits significativos se desplazan hacia afuera y el resultado siempre será cero.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4333.

```cpp
// C4333.cpp
// compile with: /c /W1
unsigned shift8 (unsigned char c) {
   return c >> 8;   // C4333

   // try the following line instead
   // return c >> 4;   // OK
}
```