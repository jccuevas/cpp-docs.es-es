---
title: Advertencia del compilador (nivel 1) C4333
ms.date: 11/04/2016
f1_keywords:
- C4333
helpviewer_keywords:
- C4333
ms.assetid: d3763c52-6110-4da0-84db-5264e3f3f166
ms.openlocfilehash: 534491db2d612f251a6fd85c9239537569083874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162938"
---
# <a name="compiler-warning-level-1-c4333"></a>Advertencia del compilador (nivel 1) C4333

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
