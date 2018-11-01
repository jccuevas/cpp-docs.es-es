---
title: Advertencia del compilador (nivel 4) C4623
ms.date: 11/04/2016
f1_keywords:
- C4623
helpviewer_keywords:
- C4623
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
ms.openlocfilehash: d1b659a6aed593a2e3f01ac1b82e60878cb09c80
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585437"
---
# <a name="compiler-warning-level-4-c4623"></a>Advertencia del compilador (nivel 4) C4623

'`derived class`': El constructor predeterminado se definió implícitamente como eliminado porque un constructor predeterminado de clase base es inaccesible o se eliminó

Un constructor no estaba accesible en una clase base y no se generó para la clase derivada. Cualquier intento de crear un objeto de este tipo en la pila provocará un error del compilador.

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4623:

```
// C4623.cpp
// compile with: /W4
#pragma warning(default : 4623)
class B {
   B();
};

class C {
public:
   C();
};

class D : public B {};   // C4623 - to fix, make B's constructor public
class E : public C {};   // OK - class C constructor is public

int main() {
   // D d;  will cause an error
}
```