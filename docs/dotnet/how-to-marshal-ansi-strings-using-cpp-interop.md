---
title: "C&#243;mo: Calcular las referencias de cadenas ANSI mediante la interoperabilidad de C++ | Microsoft Docs"
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
  - "ANSI [C++], calcular las referencias de cadenas"
  - "interoperabilidad de C++, cadenas"
  - "cálculo de referencias de datos [C++], cadenas"
  - "interoperabilidad [C++], cadenas"
  - "calcular las referencias [C++], cadenas"
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de cadenas ANSI mediante la interoperabilidad de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema muestra cómo se pueden pasar cadenas ANSI mediante la interoperabilidad de C\+\+, pero <xref:System.String> de .NET Framework representa cadenas en formato Unicode, por lo que la conversión a ANSI requiere un paso adicional.  Para interoperar con otros tipos de cadenas, vea los temas siguientes:  
  
-   [Cómo: Calcular las referencias de cadenas Unicode mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de cadenas COM mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
 En los siguientes ejemplos de código, se utilizan las directivas \#pragma [managed, unmanaged](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero sin que éstas dejen de interactuar como si se hubieran definido en archivos separados.  Dado que los archivos que contienen sólo funciones no administradas no necesitan ser compilados con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md), pueden retener sus características de rendimiento.  
  
## Ejemplo  
 El ejemplo muestra el paso de una cadena ANSI de una función administrada a una no administrada utilizando <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>.  Este método asigna memoria en el montón no administrado y devuelve la dirección después de realizar la conversión.  Esto significa que no es necesario anclar \(ya que la memoria del montón GC no se pasa a la función no administrada\) y que el valor IntPtr devuelto de <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> se debe liberar explícitamente o se producirá una pérdida de memoria.  
  
```  
// MarshalANSI1.cpp  
// compile with: /clr  
#include <iostream>  
#include <stdio.h>  
  
using namespace std;  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
void NativeTakesAString(const char* p) {  
   printf_s("(native) received '%s'\n", p);  
}  
  
#pragma managed  
  
int main() {  
   String^ s = gcnew String("sample string");  
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);  
   const char* str = static_cast<const char*>(ip.ToPointer());  
  
   Console::WriteLine("(managed) passing string...");  
   NativeTakesAString( str );  
  
   Marshal::FreeHGlobal( ip );  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra el cálculo de referencias de datos necesario para tener acceso a una cadena ANSI en una función administrada a la que se llama mediante una función no administrada.  La función administrada, cuando recibe la cadena nativa, puede usarla directamente o convertirla en una cadena administrada utilizando el método <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>, como se muestra.  
  
```  
// MarshalANSI2.cpp  
// compile with: /clr  
#include <iostream>  
#include <vcclr.h>  
  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
  
void ManagedStringFunc(char* s) {  
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));  
   Console::WriteLine("(managed): received '{0}'", ms);  
}  
  
#pragma unmanaged  
  
void NativeProvidesAString() {  
   cout << "(native) calling managed func...\n";  
   ManagedStringFunc("test string");  
}  
  
#pragma managed  
  
int main() {  
   NativeProvidesAString();  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)