---
title: Error del compilador C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: 129d2698a782d2b98267877e8d575a6ee641b94b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772051"
---
# <a name="compiler-error-c3255"></a>Error del compilador C3255

'tipo de valor': no se puede asignar dinámicamente este objeto de tipo de valor en el montón nativo

Las instancias de un tipo de valor (consulte [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md)) que contienen miembros administrados pueden crearse en la pila, pero no en el montón.

El ejemplo siguiente genera C3255:

```
// C3255.cpp
// compile with: /clr
using namespace System;
value struct V {
   Object^ o;
};

value struct V2 {
   int i;
};

int main() {
   V* pv = new V;   // C3255
   V2* pv2 = new V2;
   V v2;
}
```
