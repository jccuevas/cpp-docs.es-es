---
title: "Cómo: serializar devoluciones de llamadas y delegados mediante la interoperabilidad de C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dbae96aeb7b11105a1a2aa30aa513c8d94011a91
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Cómo: Serializar devoluciones de llamadas y delegados mediante la interoperabilidad de C++
En este tema se muestra el cálculo de referencias de devoluciones de llamada y delegados (la versión administrada de una devolución de llamada) entre código administrado y el uso de Visual C++.  
  
 El siguiente código, se ejemplos utilizan la [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma implementar administrados y funciones en el mismo archivo, pero también se pudieron definir las funciones en archivos independientes. No es necesario que los archivos que contienen únicamente funciones no administradas pueden compilarse con la [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar una API no administrada para desencadenar a un delegado administrado. Se crea un delegado administrado y uno de los métodos de interoperabilidad, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, se utiliza para recuperar el punto de entrada subyacente para el delegado. Esta dirección, a continuación, se pasa a la función no administrada, que llama a ningún conocimiento del hecho de que se implementa como una función administrada.  
  
 Tenga en cuenta que es posible, pero no es necesario, para anclar el delegado mediante [pin_ptr (C++ / CLI)](../windows/pin-ptr-cpp-cli.md) para evitar que lo que se va a volver a encontrar o eliminado por el recolector de elementos no utilizados. Es necesaria protección de la recolección prematura, pero el anclaje proporciona más protección de la necesaria, ya que evita la recolección y también evita la reubicación.  
  
 Si un delegado volver a se encuentra en una colección de elementos no utilizados, no afectará a la devolución de llamada administrada subyacente, por lo que <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> se utiliza para agregar una referencia al delegado, lo que permite la reubicación del delegado, pero evite su eliminación. El uso de GCHandle en lugar de pin_ptr reduce la fragmentación potencial del montón administrado.  
  
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
 El ejemplo siguiente es similar al ejemplo anterior, pero en este caso se almacena el puntero de función proporcionada por la API no administrada, por lo que se puede invocar en cualquier momento, que requieren que se suprimir la recolección de elementos durante un período de tiempo arbitrario. Como resultado, el ejemplo siguiente utiliza una instancia global de <xref:System.Runtime.InteropServices.GCHandle> para impedir que el delegado que se va a reubicado, independiente del ámbito de función. Como se describe en el primer ejemplo, uso de pin_ptr no es necesario para estos ejemplos, pero en este caso no funcionaría de todos modos, como el ámbito de pin_ptr se limita a una sola función.  
  
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