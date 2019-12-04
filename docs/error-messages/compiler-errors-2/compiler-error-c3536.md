---
title: Error del compilador C3536
ms.date: 11/04/2016
f1_keywords:
- C3536
helpviewer_keywords:
- C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
ms.openlocfilehash: a140847b642ac2437b67aa957328c3b8fbfc592d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761574"
---
# <a name="compiler-error-c3536"></a>Error del compilador C3536

' Symbol ': no se puede usar antes de inicializarse

No se puede usar el símbolo indicado antes de inicializarlo. En la práctica, esto significa que una variable no se puede usar para inicializarse a sí misma.

### <a name="to-correct-this-error"></a>Para corregir este error

1. No inicialice una variable con sí misma.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se produce C3536 porque cada variable se inicializa con sí misma.

```cpp
// C3536.cpp
// Compile with /Zc:auto
int main()
{
   auto a = a;     //C3536
   auto b = &b;    //C3536
   auto c = c + 1; //C3536
   auto* d = &d;   //C3536
   auto& e = e;    //C3536
   return 0;
};
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)
