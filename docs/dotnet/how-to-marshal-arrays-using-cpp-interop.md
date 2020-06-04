---
title: 'Cómo: Calcular las referencias de matrices mediante la interoperabilidad de C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++], marshaling
- marshaling [C++], arrays
- interop [C++], arrays
- C++ Interop, arrays
- data marshaling [C++], arrays
ms.assetid: c2b37ab1-8acf-4855-ad3c-7d2864826b14
ms.openlocfilehash: fddb8b4fa645d6fee3597d098fc67a3006603b9f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544950"
---
# <a name="how-to-marshal-arrays-using-c-interop"></a>Cómo: Calcular las referencias de matrices mediante la interoperabilidad de C++

En este tema se muestra una faceta C++ de interoperabilidad visual. Para obtener más información, [vea C++ usar Interop (implicit PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

En los siguientes ejemplos de código se usan las directivas de #pragma [administradas y no administradas](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero estas funciones interoperan de la misma manera si se definen en archivos independientes. No es necesario compilar los archivos que contienen solo funciones no administradas con [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo pasar una matriz administrada a una función no administrada. La función administrada usa [pin_ptrC++(/CLI)](../extensions/pin-ptr-cpp-cli.md) para suprimir la recolección de elementos no utilizados de la matriz antes de llamar a la función no administrada. Al proporcionar la función no administrada con un puntero anclado en el montón GC, se puede evitar la sobrecarga de realizar una copia de la matriz. Para demostrar que la función no administrada está accediendo a la memoria del montón GC, modifica el contenido de la matriz y los cambios se reflejan cuando la función administrada reanuda el control.

```cpp
// PassArray1.cpp
// compile with: /clr
#ifndef _CRT_RAND_S
#define _CRT_RAND_S
#endif

#include <iostream>
#include <stdlib.h>
using namespace std;

using namespace System;

#pragma unmanaged

void TakesAnArray(int* a, int c) {
   cout << "(unmanaged) array received:\n";
   for (int i=0; i<c; i++)
      cout << "a[" << i << "] = " << a[i] << "\n";

   unsigned int number;
   errno_t err;

   cout << "(unmanaged) modifying array contents...\n";
   for (int i=0; i<c; i++) {
      err = rand_s( &number );
      if ( err == 0 )
         a[i] = number % 100;
   }
}

#pragma managed

int main() {
   array<int>^ nums = gcnew array<int>(5);

   nums[0] = 0;
   nums[1] = 1;
   nums[2] = 2;
   nums[3] = 3;
   nums[4] = 4;

   Console::WriteLine("(managed) array created:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);

   pin_ptr<int> pp = &nums[0];
   TakesAnArray(pp, 5);

   Console::WriteLine("(managed) contents:");
   for (int i=0; i<5; i++)
      Console::WriteLine("a[{0}] = {1}", i, nums[i]);
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo pasar una matriz no administrada a una función administrada. La función administrada accede directamente a la memoria de la matriz (en lugar de crear una matriz administrada y copiar el contenido de la matriz), lo que permite que los cambios realizados por la función administrada se reflejen en la función no administrada cuando vuelve a obtener el control.

```cpp
// PassArray2.cpp
// compile with: /clr
#include <iostream>
using namespace std;

using namespace System;

#pragma managed

void ManagedTakesAnArray(int* a, int c) {
   Console::WriteLine("(managed) array received:");
   for (int i=0; i<c; i++)
      Console::WriteLine("a[{0}] = {1}", i, a[i]);

   cout << "(managed) modifying array contents...\n";
   Random^ r = gcnew Random(DateTime::Now.Second);
   for (int i=0; i<c; i++)
      a[i] = r->Next(100);
}

#pragma unmanaged

void NativeFunc() {
   int nums[5] = { 0, 1, 2, 3, 4 };

   printf_s("(unmanaged) array created:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);

   ManagedTakesAnArray(nums, 5);

   printf_s("(ummanaged) contents:\n");
   for (int i=0; i<5; i++)
      printf_s("a[%d] = %d\n", i, nums[i]);
}

#pragma managed

int main() {
   NativeFunc();
}
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
