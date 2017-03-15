---
title: "C&#243;mo: Calcular las referencias de cadenas Unicode mediante la interoperabilidad de C++ | Microsoft Docs"
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
  - "interoperabilidad de C++, cadenas"
  - "cálculo de referencias de datos [C++], cadenas"
  - "interoperabilidad [C++], cadenas"
  - "calcular las referencias [C++], cadenas"
  - "Unicode, calcular las referencias de cadenas"
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de cadenas Unicode mediante la interoperabilidad de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra un aspecto de la interoperabilidad de Visual C\+\+.  Para obtener más información, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
 En los siguientes ejemplos de código, se utilizan las directivas \#pragma [managed, unmanaged](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero sin que éstas dejen de interactuar como si se hubieran definido en archivos separados.  No es necesario compilar con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) los archivos que contienen únicamente funciones no administradas.  
  
 En este tema, se muestra cómo se pueden pasar cadenas Unicode de una función administrada a una no administrada y viceversa.  Para interoperar con otros tipos de cadenas, consulte los temas siguientes:  
  
-   [Cómo: Calcular las referencias de cadenas ANSI mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de cadenas COM mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
## Ejemplo  
 Para pasar una cadena Unicode de una función administrada a una no administrada, se puede usar la función PtrToStringChars \(declarada en Vcclr.h\) para tener acceso a la ubicación en la memoria donde se almacena la cadena administrada.  Dado que esta dirección se pasará a una función nativa, es importante anclar la memoria con [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md) para evitar que los datos de la cadena cambien de ubicación, si tuviese lugar un ciclo de recolección de elementos no utilizados durante la ejecución de la función no administrada.  
  
```  
// MarshalUnicode1.cpp  
// compile with: /clr  
#include <iostream>  
#include <stdio.h>  
#include <vcclr.h>  
  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
void NativeTakesAString(const wchar_t* p) {  
   printf_s("(native) received '%S'\n", p);  
}  
  
#pragma managed  
  
int main() {  
   String^ s = gcnew String("test string");  
   pin_ptr<const wchar_t> str = PtrToStringChars(s);  
  
   Console::WriteLine("(managed) passing string to native func...");  
   NativeTakesAString( str );  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra el cálculo de referencias de datos que se requiere para tener acceso a una cadena Unicode en una función administrada a la que llama una función no administrada.  La función administrada, al recibir la cadena Unicode nativa, la convierte en una cadena administrada utilizando el método <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>.  
  
```  
// MarshalUnicode2.cpp  
// compile with: /clr  
#include <iostream>  
  
using namespace std;  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
  
void ManagedStringFunc(wchar_t* s) {  
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);  
   Console::WriteLine("(managed) received '{0}'", ms);  
}  
  
#pragma unmanaged  
  
void NativeProvidesAString() {  
   cout << "(unmanaged) calling managed func...\n";  
   ManagedStringFunc(L"test string");  
}  
  
#pragma managed  
  
int main() {  
   NativeProvidesAString();  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)