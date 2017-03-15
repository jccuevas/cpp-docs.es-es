---
title: "C&#243;mo: Calcular las referencias de cadenas COM mediante la interoperabilidad de C++ | Microsoft Docs"
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
  - "COM [C++], calcular las referencias de cadenas"
  - "cálculo de referencias de datos [C++], cadenas"
  - "interoperabilidad [C++], cadenas"
  - "calcular las referencias [C++], cadenas"
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias de cadenas COM mediante la interoperabilidad de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tema siguiente muestra cómo se puede hacer que BSTR \(el formato de cadena básico preferido en programación COM\) pase de una función administrada a no administrada, y al contrario.  Para interoperar con otros tipos de cadenas, consulte los temas siguientes:  
  
-   [Cómo: Calcular las referencias de cadenas Unicode mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Cómo: Calcular las referencias de cadenas ANSI mediante la interoperabilidad de C\+\+](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 En los siguientes ejemplos de código, se utilizan las directivas \#pragma [managed, unmanaged](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero sin que éstas dejen de interactuar como si se hubieran definido en archivos separados.  No es necesario compilar con [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) los archivos que contienen únicamente funciones no administradas.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo se puede hacer que BSTR \(un formato de cadena utilizado en programación COM\) pase de una función administrada a no administrada.  La función administrada de llamada usa <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> para obtener la dirección de una representación de BSTR del contenido de una System.String de .NET.  Este puntero se ancla mediante [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md), para asegurarse de que su dirección física no cambie durante un ciclo de recolección de elementos no utilizados mientras se ejecuta la función no administrada.  El recolector de elementos no utilizados no puede de ningún modo mover la memoria hasta que [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md) salga del ámbito.  
  
```  
// MarshalBSTR1.cpp  
// compile with: /clr  
#define WINVER 0x0502  
#define _AFXDLL  
#include <afxwin.h>  
  
#include <iostream>  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma unmanaged  
  
void NativeTakesAString(BSTR bstr) {  
   printf_s("%S", bstr);  
}  
  
#pragma managed  
  
int main() {  
   String^ s = "test string";  
  
   IntPtr ip = Marshal::StringToBSTR(s);  
   BSTR bs = static_cast<BSTR>(ip.ToPointer());  
   pin_ptr<BSTR> b = &bs;  
  
   NativeTakesAString( bs );  
   Marshal::FreeBSTR(ip);  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo se puede hacer que BSTR pase de una función no administrada a una administrada.  La función administrada receptora puede utilizar la cadena como BSTR, o usar <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> para convertirla en <xref:System.String> y poder utilizarla con otras funciones administradas.  Dado que la memoria que representa BSTR está asignada en el montón no administrado, no es necesario anclar, ya que no hay recolección de elementos no utilizados en dicho montón.  
  
```  
// MarshalBSTR2.cpp  
// compile with: /clr  
#define WINVER 0x0502  
#define _AFXDLL  
#include <afxwin.h>  
  
#include <iostream>  
using namespace std;  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#pragma managed  
  
void ManagedTakesAString(BSTR bstr) {  
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));  
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);  
}  
  
#pragma unmanaged  
  
void UnManagedFunc() {  
   BSTR bs = SysAllocString(L"test string");  
   printf_s("(unmanaged) passing BSTR to managed func...\n");  
   ManagedTakesAString(bs);  
}  
  
#pragma managed  
  
int main() {  
   UnManagedFunc();  
}  
```  
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)