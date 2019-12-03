---
title: Advertencia del compilador (nivel 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: fb51d16cc15c244b31d65f7777de66c372bbde33
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683207"
---
# <a name="compiler-warning-level-4-c4481"></a>Advertencia del compilador (nivel 4) C4481

se ha utilizado una extensión no estándar: especificador de invalidación ' palabra clave '

Se usó una palabra clave que no está en C++ el estándar, por ejemplo, uno de los especificadores de invalidación que también funcionan en/CLR.  Para obtener más información, vea

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Especificadores de invalidación](../../extensions/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4481.

```cpp
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