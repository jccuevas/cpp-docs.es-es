---
title: "Cómo: serializar cadenas ANSI mediante la interoperabilidad de C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e70d62fa7a94a7278080c31f6650b31b71ff35b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Cómo: serializar cadenas ANSI mediante la interoperabilidad de C++
Este tema muestra cómo pueden ser cadenas ANSI pasado utilizando la interoperabilidad de C++, pero .NET Framework <xref:System.String> representa las cadenas en formato Unicode, por lo que la conversión a ANSI requiere un paso adicional. Para interoperar con otros tipos de cadena, vea los temas siguientes:  
  
-   [Cómo: Serializar cadenas Unicode mediante la interoperabilidad de C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Cómo: Serializar cadenas COM mediante la interoperabilidad de C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
 El siguiente código, se ejemplos utilizan la [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma implementar administrados y funciones en el mismo archivo, pero estas funciones interoperan de la misma manera, si está definido en archivos independientes. Dado que no es necesario que los archivos que contienen únicamente funciones no administradas pueden compilarse con [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), pueden conservar sus características de rendimiento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo se muestra cómo pasar una cadena ANSI de administrada a una función no administrada usando <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Este método asigna memoria en el montón no administrado y devuelve la dirección después de realizar la conversión. Esto significa que no es necesario fijar (debido a memoria en el montón del GC no se pasa a la función no administrada) y que el valor IntPtr devuelto desde <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> debe liberar de forma explícita o una memoria de la pérdida de resultados.  
  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el cálculo de referencias de datos necesarios para tener acceso a una cadena ANSI en una función administrada que llama a una función no administrada. La función administrada, al recibir la cadena nativa, puede usarla directamente o convertirla en una cadena administrada mediante el <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> método, tal como se muestra.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)