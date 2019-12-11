---
title: Advertencia del compilador (nivel 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 7d8ff442e84aa7563b1787e5a030297c034e1871
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992062"
---
# <a name="compiler-warning-level-3-c4534"></a>Advertencia del compilador (nivel 3) C4534

' constructor ' no será un constructor predeterminado para la clase ' Class ' debido al argumento predeterminado

Una clase no administrada puede tener un constructor con parámetros que tienen valores predeterminados y el compilador lo utilizará como el constructor predeterminado. Una clase marcada con la palabra clave `value` no usará un constructor con valores predeterminados para sus parámetros como constructor predeterminado.

Para más información, vea [ref class and ref struct (C++/CLI and C++/CX)](../../extensions/classes-and-structs-cpp-component-extensions.md) [ref class y ref struct (C++/CLI y C++/CX)].

En el ejemplo siguiente se genera C4534:

```cpp
// C4534.cpp
// compile with: /W3 /clr /WX
value class MyClass {
public:
   int ii;
   MyClass(int i = 9) {   // C4534, will not be the default constructor
      i++;
   }
};

int main() {
   MyClass ^ xx = gcnew MyClass;
   xx->ii = 0;
}
```
