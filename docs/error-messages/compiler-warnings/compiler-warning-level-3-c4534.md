---
title: Advertencia del compilador (nivel 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 81445ff42aca78a8e40e9c88eff4bb76a41a8669
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401883"
---
# <a name="compiler-warning-level-3-c4534"></a>Advertencia del compilador (nivel 3) C4534

'constructor' no será un constructor predeterminado para la clase 'class' debido al argumento predeterminado

Una clase no administrada puede tener un constructor con parámetros que tienen valores predeterminados y el compilador usará esto como el constructor predeterminado. Una clase marcada con el `value` palabra clave no usará un constructor con valores predeterminados para sus parámetros como un constructor predeterminado.

Para obtener más información, consulte [clases y Structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

El ejemplo siguiente genera C4534:

```
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