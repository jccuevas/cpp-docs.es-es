---
title: 'Cómo: Calcular las referencias de devoluciones de llamadas y delegados mediante la interoperabilidad de C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
ms.openlocfilehash: 592eae0ff59baddb79b810d46669b78ecc801155
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544944"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Cómo: Calcular las referencias de devoluciones de llamadas y delegados mediante la interoperabilidad de C++

En este tema se muestra la serialización de devoluciones de llamada y delegados (la versión administrada de una devolución de llamada C++) entre código administrado y no administrado mediante Visual.

En los siguientes ejemplos de código se usan las directivas de #pragma [administradas y no administradas](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero también se pueden definir las funciones en archivos independientes. No es necesario compilar los archivos que contienen solo funciones no administradas con [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar una API no administrada para desencadenar un delegado administrado. Se crea un delegado administrado y uno de los métodos de interoperabilidad, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, se usa para recuperar el punto de entrada subyacente del delegado. A continuación, esta dirección se pasa a la función no administrada, que lo llama sin tener conocimiento del hecho de que se implementa como una función administrada.

Tenga en cuenta que es posible, pero no es necesario, anclar el delegado mediante [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) para evitar que el recolector de elementos no utilizados lo vuelva a ubicar o deseche. Se necesita protección contra la recolección de elementos no utilizados prematura, pero el anclaje proporciona más protección de lo necesario, ya que evita la recopilación, pero también evita la reubicación.

Si una recolección de elementos no utilizados reubica un delegado, no afectará a la devolución de llamada administrada subyacente, por lo que se usa <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> para agregar una referencia al delegado, lo que permite la reubicación del delegado, pero se impide la eliminación. El uso de GCHandle en lugar de pin_ptr reduce el potencial de fragmentación del montón administrado.

```cpp
// MarshalDelegate1.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);

int TakesCallback(ANSWERCB fp, int n, int m) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n, m);
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   return n + m;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   GCHandle gch = GCHandle::Alloc(fp);
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

// force garbage collection cycle to prove
// that the delegate doesn't get disposed
   GC::Collect();

   int answer = TakesCallback(cb, 243, 257);

// release reference to delegate
   gch.Free();
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente es similar al ejemplo anterior, pero en este caso el puntero de función proporcionado se almacena mediante la API no administrada, por lo que se puede invocar en cualquier momento, lo que requiere que la recolección de elementos no utilizados se suprima durante un período de tiempo arbitrario. Como resultado, en el ejemplo siguiente se usa una instancia global de <xref:System.Runtime.InteropServices.GCHandle> para evitar que el delegado se reubique, independientemente del ámbito de la función. Como se describe en el primer ejemplo, el uso de pin_ptr no es necesario para estos ejemplos, pero en este caso no funcionaría de todas formas, ya que el ámbito de un pin_ptr está limitado a una sola función.

```cpp
// MarshalDelegate2.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);
static ANSWERCB cb;

int TakesCallback(ANSWERCB fp, int n, int m) {
   cb = fp;
   if (cb) {
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);
      return cb(n, m);
   }
   printf_s("[unmanaged] unregistering callback");
   return 0;
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;

   return n + m + x;
}

static GCHandle gch;

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);

   gch = GCHandle::Alloc(fp);

   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TakesCallback(cb, 243, 257);

   // possibly much later (in another function)...

   Console::WriteLine("[managed] releasing callback mechanisms...");
   TakesCallback(0, 243, 257);
   gch.Free();
}
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
