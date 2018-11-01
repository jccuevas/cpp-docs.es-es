---
title: 'Cómo: serializar estructuras mediante la interoperabilidad de C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Interop, structures
- structures [C++], marshaling
- data marshaling [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: c2080200-f983-4d6e-a557-cd870f060a54
ms.openlocfilehash: c44b23bf0f73191b86b4970c57313d9bc38c8b7a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521338"
---
# <a name="how-to-marshal-structures-using-c-interop"></a>Cómo: serializar estructuras mediante la interoperabilidad de C++

En este tema se muestra un aspecto de la interoperabilidad de Visual C++. Para obtener más información, consulte [utilizando interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Uso de ejemplos de código siguiente el [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma para implementar administrados y las funciones en el mismo archivo, pero estas funciones interoperan de la misma manera, si se definen en archivos independientes. No es necesario que los archivos que contienen solo las funciones no administradas se compilan con [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra cómo pasar una estructura de administrado a una función no administrada, por valor y por referencia. Dado que la estructura de este ejemplo contiene los tipos de datos intrínsecos simples solo (consulte [Non-bits/bytes tipos](/dotnet/framework/interop/blittable-and-non-blittable-types)), ningún cálculo de referencias especial es necesario. Para calcular las referencias de estructuras de espacio, como las que contienen punteros, vea [Cómo: serializar incrustado punteros Using C++ Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```
// PassStruct1.cpp
// compile with: /clr

#include <stdio.h>
#include <math.h>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

struct Location {
   int x;
   int y;
};

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}

#pragma managed

int main() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   Location loc3;
   InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo pasar una estructura de no administrado a una función administrada, por valor y por referencia. Dado que la estructura de este ejemplo contiene los tipos de datos intrínsecos simples solo (consulte [Non-bits/bytes tipos](/dotnet/framework/interop/blittable-and-non-blittable-types)), ningún cálculo de referencias especial es necesario. Para calcular las referencias de estructuras de espacio, como las que contienen punteros, vea [Cómo: serializar incrustado punteros Using C++ Interop](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

```
// PassStruct2.cpp
// compile with: /clr
#include <stdio.h>
#include <math.h>
using namespace System;

// native structure definition
struct Location {
   int x;
   int y;
};

#pragma managed

double GetDistance(Location loc1, Location loc2) {
   Console::Write("[managed] got loc1({0},{1})", loc1.x, loc1.y);
   Console::WriteLine(" loc2({0},{1})", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   Console::WriteLine("[managed] Initializing location...");
   lp->x = 50;
   lp->y = 50;
}

#pragma unmanaged

int UnmanagedFunc() {
   Location loc1;
   loc1.x = 0;
   loc1.y = 0;

   Location loc2;
   loc2.x = 100;
   loc2.y = 100;

   printf_s("(unmanaged) loc1=(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2=(%d,%d)\n", loc2.x, loc2.y);

   double dist = GetDistance(loc1, loc2);
   printf_s("[unmanaged] distance = %f\n", dist);

   Location loc3;
   InitLocation(&loc3);
   printf_s("[unmanaged] got x=%d y=%d\n", loc3.x, loc3.y);

    return 0;
}

#pragma managed

int main() {
   UnmanagedFunc();
}
```

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)