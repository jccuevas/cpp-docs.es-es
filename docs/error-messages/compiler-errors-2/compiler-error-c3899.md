---
title: Error del compilador C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: 022bc1a37f7d9cfdb2c206592dd303a9c3c95080
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749118"
---
# <a name="compiler-error-c3899"></a>Error del compilador C3899

' var ': no se permite el uso del valor l del miembro de datos initonly directamente dentro de una región paralela de la clase ' clase '

No se puede inicializar un miembro de datos [InitOnly (C++/CLI)](../../dotnet/initonly-cpp-cli.md) dentro de la parte de un constructor que se encuentra en una región [paralela](../../parallel/openmp/reference/parallel.md) .  Esto se debe a que el compilador realiza una reubicación interna de ese código, de modo que ya no forma parte del constructor.

Para resolverlo, inicialice el miembro de datos initonly en el constructor, pero fuera de la región paralela.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3899.

```cpp
// C3899.cpp
// compile with: /clr /openmp
#include <omp.h>

public ref struct R {
   initonly int x;
   R() {
      x = omp_get_thread_num() + 1000;   // OK
      #pragma omp parallel num_threads(5)
      {
         // cannot assign to 'x' here
         x = omp_get_thread_num() + 1000;   // C3899
         System::Console::WriteLine("thread {0}", omp_get_thread_num());
      }
      x = omp_get_thread_num() + 1000;   // OK
   }
};

int main() {
   R^ r = gcnew R;
   System::Console::WriteLine(r->x);
}
```
