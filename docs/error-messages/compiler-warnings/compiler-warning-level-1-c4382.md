---
title: Advertencia del compilador (nivel 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: cca2f8cc13cc8317bac3736e142ef58e126ed994
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390495"
---
# <a name="compiler-warning-level-1-c4382"></a>Advertencia del compilador (nivel 1) C4382

> Iniciando '*tipo*': solamente se puede detectar un tipo con el destructor __clrcall o el constructor de copias en/CLR: pure módulo

## <a name="remarks"></a>Comentarios

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Cuando se compila con **/CLR** (no **/CLR: pure**), control de excepciones espera que las funciones miembro de un tipo nativo que [__cdecl](../../cpp/cdecl.md) y no [__clrcall](../../cpp/clrcall.md). Los tipos nativos con funciones miembro mediante `__clrcall` convención de llamada no se pueden detectar en un módulo compilado con **/CLR**.

Si la excepción se capturará en un módulo compilado con **/CLR: pure**, puede omitir esta advertencia.

Para obtener más información, consulte [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4382.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```