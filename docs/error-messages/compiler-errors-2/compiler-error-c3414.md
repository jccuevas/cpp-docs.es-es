---
title: Error del compilador C3414
ms.date: 11/04/2016
f1_keywords:
- C3414
helpviewer_keywords:
- C3414
ms.assetid: 715f5432-b509-4f8f-84f5-e1463bac490f
ms.openlocfilehash: ee1e6913d108d0e5519eac6399ed83ac057da9e2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742943"
---
# <a name="compiler-error-c3414"></a>Error del compilador C3414

' Member ': no se puede definir la función miembro importada

Se definió un miembro en el código que también se define en un ensamblado al que se hace referencia.

En el ejemplo siguiente se genera C3414:

```cpp
// C3414a2.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

y luego:

```cpp
// C3414b2.cpp
// compile with: /clr
#using <C3414a2.dll>

void MyClass::Test() {    // C3414
}

System::Object::Object() {    // C3414
}
```
