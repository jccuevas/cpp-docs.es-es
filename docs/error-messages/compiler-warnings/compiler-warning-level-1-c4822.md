---
title: Advertencia del compilador (nivel 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 02e7ba11f7bda134bcc98ce2c494a3ef367c0d6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591248"
---
# <a name="compiler-warning-level-1-c4822"></a>Advertencia del compilador (nivel 1) C4822

'member': la función miembro de clase local no tiene cuerpo

Una función de miembro de clase local se ha declarado, pero no se ha definido en la clase. Para usar una función de miembro de clase local, debe definirla en la clase. No se puede declarar en la clase y definirla fuera de ella.

Cualquier definición de la clase de una función miembro de clase local será un error.

El ejemplo siguiente genera la advertencia C4822:

```
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```