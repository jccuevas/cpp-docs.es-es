---
title: Error del compilador C3899
ms.date: 11/04/2016
f1_keywords:
- C3899
helpviewer_keywords:
- C3899
ms.assetid: 14e07e4a-f7a7-4309-baaa-649d69e12e23
ms.openlocfilehash: 26860ba0e8fd92f491ee389147605ba82cecf25c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376034"
---
# <a name="compiler-error-c3899"></a>Error del compilador C3899

'var': no se permite el uso de valor l del miembro de datos initonly directamente dentro de una región paralela en la clase 'class'

Un [initonly (C++ / c++ / CLI)](../../dotnet/initonly-cpp-cli.md) no se puede inicializar el miembro de datos dentro de la parte de un constructor que se encuentra en un [paralelo](../../parallel/openmp/reference/parallel.md) región.  Esto es porque el compilador realiza una reubicación interna de dicho código, que efectivamente ya no forma parte del constructor.

Para resolverlo, inicialice al miembro de datos initonly en el constructor, pero fuera de la región paralela.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3899.

```
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