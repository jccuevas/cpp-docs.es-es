---
title: Error del compilador C3293
ms.date: 07/21/2017
f1_keywords:
- C3293
helpviewer_keywords:
- C3293
ms.assetid: b772cf98-52e0-4e24-be23-1f5d87d999ac
ms.openlocfilehash: 1713632d21ef401fb1177350c81a4a64ed0503ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760119"
---
# <a name="compiler-error-c3293"></a>Error del compilador C3293

'accessor': use 'default' para acceder a la propiedad predeterminada (indexador) de la clase 'type'

Se accedió incorrectamente a una propiedad indexada.  Consulte [Cómo: usar propiedades C++en/CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md) para obtener más información.

**Visual studio 2017 y versiones posteriores**: en visual Studio 2015 y versiones anteriores, el compilador en algunos casos inidentificó una propiedad predeterminada como indizador predeterminado. Era posible solucionar el problema con el identificador "default" para acceder a la propiedad. La solución en sí misma se volvió problemática después de que se empezara a usar default como palabra clave en C++11. Por lo tanto, en Visual Studio 2017 se corrigieron los errores necesarios para la solución, y el compilador ahora genera un error cuando se usa "default" para acceder a la propiedad predeterminada de una clase.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3293 en Visual Studio 2015 y versiones anteriores.

```cpp
// C3293.cpp
// compile with: /clr /c
using namespace System;
ref class IndexerClass {
public:
   // default indexer
   property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};

int main() {
   IndexerClass ^ ic = gcnew IndexerClass;
   ic->Item[0] = 21;   // C3293 in VS2015 OK in VS2017
   ic->default[0] = 21;   // OK in VS2015 and earlier

   String ^s = "Hello";
   wchar_t wc = s->Chars[0];   // C3293 in VS2015 OK in VS2017
   wchar_t wc2 = s->default[0];   // OK in VS2015 and earlier
   Console::WriteLine(wc2);
}
```
