---
title: Error del compilador C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: ba1dbf08fb56364d2ab5b8c40847ab89484dc005
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328803"
---
# <a name="compiler-error-c3375"></a>Error del compilador C3375

'function': función delegada ambigua

Una creación de instancias de delegado podría haber tenido lugar en una función miembro estática o, como un delegado sin enlazar, en una función de instancia, por lo que el compilador emitió este error.

Para obtener más información, consulte [delegate (extensiones de componentes de C++)](../../extensions/delegate-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3375.

```
// C3375.cpp
// compile with: /clr
ref struct R {
   static void f(R^) {}
   void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::f);   // C3375
}
```