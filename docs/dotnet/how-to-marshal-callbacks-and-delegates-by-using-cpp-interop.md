---
title: "C&#243;mo: Calcular las referencias de devoluciones de llamadas y delegados mediante la interoperabilidad de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "interoperabilidad de C++, devoluciones de llamada y delegados"
  - "devoluciones de llamada [C++], calcular las referencias"
  - "cálculo de referencias de datos [C++], devoluciones de llamada y delegados"
  - "delegados [C++], calcular las referencias"
  - "interoperabilidad [C++], devoluciones de llamada y delegados"
  - "calcular las referencias [C++], devoluciones de llamada y delegados"
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de devoluciones de llamadas y delegados mediante la interoperabilidad de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema, se muestra el cálculo de referencias de devoluciones de llamadas y delegados \(la versión administrada de una devolución de llamada\) entre código administrado y no administrado utilizando Visual C\+\+.  
  
 En los siguientes ejemplos de código, se utilizan las directivas \#pragma [managed, unmanaged](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, aunque éstas también se podrían definir en archivos separados.  No es necesario compilar con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) los archivos que contienen únicamente funciones no administradas.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar una API no administrada para desencadenar un delegado administrado.  Se crea un delegado administrado y se utiliza uno de los métodos de interoperabilidad, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, para recuperar el punto de entrada subyacente para el delegado.  Después, esta dirección se pasa a la función no administrada, que la llama sin conocer el hecho de que se implementa como función administrada.  
  
 Tenga en cuenta que es posible, aunque no necesario, anclar el delegado mediante [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md) para evitar que se cambie de ubicación o que el recolector de elementos no utilizados lo elimine.  Es necesario proteger de una recolección de elementos no utilizados prematura, pero el anclaje proporciona más protección de la necesaria, ya que evita la recolección y también la reubicación.  
  
 Si una recolección de elementos no utilizados cambia la ubicación de un delegado, no afecta a la devolución de llamada administrada subyacente, de modo que <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> se utiliza para agregar una referencia al delegado, de modo que se permita su reubicación pero se evite su eliminación.  El uso de GCHandle en lugar de pin\_ptr reduce la fragmentación potencial del montón administrado.  
  
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
  
## Ejemplo  
 El siguiente ejemplo es similar al anterior, pero en este caso, el puntero a función suministrado se almacena mediante la API no administrada, de modo que se puede invocar en cualquier momento y requiere que la recolección de elementos no utilizados se suprima durante un período de tiempo arbitrario.  Como resultado, el ejemplo siguiente utiliza una instancia global de <xref:System.Runtime.InteropServices.GCHandle> para evitar que se reubique el delegado, independientemente del ámbito de la función.  Como se indicó en el primer ejemplo, el uso de pin\_ptr es innecesario para estos ejemplos, pero en este caso no funcionaría de todos modos, ya que el ámbito de pin\_ptr se limita a una sola función.  
  
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
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)