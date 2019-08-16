---
title: Advertencia del compilador (nivel 3) C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: adf233673c4b654927aa9488565adf6ceef5d3e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401571"
---
# <a name="compiler-warning-level-3-c4792"></a>Advertencia del compilador (nivel 3) C4792

función 'function' declarada usando sysimport a la que se hace referencia desde código nativo; biblioteca de importación necesaria para vincular

Se llamó a una función nativa importada en el programa con DllImport desde una función no administrada. Por lo tanto, debe vincular a la biblioteca de importación del archivo DLL.

Esta advertencia no se puede resolver  en el código ni cambiando la forma de realizar la compilación. Para deshabilitar esta advertencia, use la pragma [warning](../../preprocessor/warning.md) .

El ejemplo siguiente genera la advertencia C4792:

```
// C4792.cpp
// compile with: /clr /W3
// C4792 expected
using namespace System::Runtime::InteropServices;
[DllImport("msvcrt")]
extern "C" int __cdecl puts(const char *);
int main() {}

// Uncomment the following line to resolve.
// #pragma warning(disable : 4792)
#pragma unmanaged
void func(void){
   puts("test");
}
```