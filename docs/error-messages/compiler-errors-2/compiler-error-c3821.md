---
title: Error del compilador C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 25023277258d33ab77bde18f6cdfabc862f50a63
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741747"
---
# <a name="compiler-error-c3821"></a>Error del compilador C3821

' función ': no se puede usar la función o el tipo administrado en una función no administrada

Las funciones con ensamblado alineado o [setjmp](../../c-runtime-library/reference/setjmp.md) no pueden contener tipos de valor ni clases administradas. Para corregir este error, quite el ensamblado alineado y `setjmp` o quite los objetos administrados.

C3821 también puede producirse si se intenta utilizar el almacenamiento automático en una función vararg.  Para obtener más información, vea [listas de argumentos variables (...C++) (/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md) y [ C++ semántica de pila para los tipos de referencia](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3821.

```cpp
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3821.

```cpp
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
