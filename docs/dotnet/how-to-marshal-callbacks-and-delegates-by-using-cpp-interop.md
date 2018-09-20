---
title: 'Cómo: serializar devoluciones de llamadas y delegados mediante la interoperabilidad de C++ | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: db3d4cf59aa3ec14e964d53a54afbe5a9fe0aecd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381899"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Cómo: Serializar devoluciones de llamadas y delegados mediante la interoperabilidad de C++

En este tema se muestra el cálculo de referencias de devoluciones de llamada y delegados (la versión administrada de una devolución de llamada) entre código administrado y el uso de Visual C++.

Uso de ejemplos de código siguiente el [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma para implementar administrados y las funciones en el mismo archivo, pero también se puede definir las funciones en archivos independientes. No es necesario que los archivos que contienen solo las funciones no administradas se compilan con la [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo configurar una API no administrada para desencadenar a un delegado administrado. Se crea un delegado administrado y uno de los métodos de interoperabilidad, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, se usa para recuperar el punto de entrada subyacente para el delegado. Esta dirección, a continuación, se pasa a la función no administrada, que se llama sin el conocimiento del hecho de que se implementa como una función administrada.

Tenga en cuenta que es posible, aunque no es necesario, para anclar el delegado mediante [pin_ptr (C++ / c++ / CLI)](../windows/pin-ptr-cpp-cli.md) para evitar que lo que se va a volver a encontrar o eliminado por el recolector de elementos no utilizados. Protección de la recolección prematura es necesario, pero anclar ofrece más protección de la necesaria, ya que evita la colección y también impide la reubicación.

Si un delegado se encuentra volver a una recolección, no afectará a la devolución de llamada administrada subyacente, por lo que <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> se usa para agregar una referencia al delegado, lo que permite la reubicación del delegado, pero impide su eliminación. El uso de GCHandle en lugar de pin_ptr reduce el potencial de la fragmentación del montón administrado.

```
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

El ejemplo siguiente es similar al ejemplo anterior, pero en este caso se almacena el puntero de función proporcionado por la API no administrada, por lo que se puede invocar en cualquier momento, que requieren que se puede suprimir la recolección de elementos durante un período de tiempo arbitrario. Como resultado, el ejemplo siguiente utiliza una instancia global de <xref:System.Runtime.InteropServices.GCHandle> para impedir que el delegado que se cambia la ubicación, independientemente del ámbito de función. Como se describe en el primer ejemplo, uso de pin_ptr no es necesario para estos ejemplos, pero en este caso no funcionaría de todos modos, el ámbito de pin_ptr se limita a una sola función.

```
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

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)