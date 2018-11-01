---
title: Advertencia del compilador (nivel 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: f88a61a40a789c31e80875d785b95136ac69253c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466942"
---
# <a name="compiler-warning-level-4-c4481"></a>Advertencia del compilador (nivel 4) C4481

ha utilizado una extensión no estándar: 'keyword' especificador de invalidación

Se utilizó una palabra clave que no está en el estándar de C++, por ejemplo, uno de los especificadores de invalidación que también funciona en/CLR.  Para obtener más información, vea

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4481.

```
// C4481.cpp
// compile with: /W4 /c
class B {
   virtual void f(unsigned);
};

class C : B {
   void f(unsigned) override;   // C4481
   void f2(unsigned);
};
```