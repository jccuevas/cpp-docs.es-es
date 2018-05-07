---
title: 'Cómo: serializar cadenas Unicode mediante la interoperabilidad de C++ | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e5290958a55c61dd55adac0f182af7163896d694
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Cómo: serializar cadenas Unicode mediante la interoperabilidad de C++
En este tema se muestra un aspecto de la interoperabilidad de Visual C++. Para obtener más información, consulte [uso de la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
 El siguiente código, se ejemplos utilizan la [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma implementar administrados y funciones en el mismo archivo, pero estas funciones interoperan de la misma manera, si está definido en archivos independientes. No es necesario que los archivos que contienen únicamente funciones no administradas pueden compilarse con [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Este tema muestra cómo pueden ser cadenas Unicode pasado de administrada a una función no administrada y viceversa. Para interoperar con otros tipos de cadenas, vea los temas siguientes:  
  
-   [Cómo: Serializar cadenas ANSI mediante la interoperabilidad de C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [Cómo: Serializar cadenas COM mediante la interoperabilidad de C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
## <a name="example"></a>Ejemplo  
 Para pasar una cadena Unicode de administrada a una función no administrada, se puede usar la función PtrToStringChars (declarada en Vcclr.h) para tener acceso a la memoria donde se almacena la cadena administrada. Dado que esta dirección se pasará a una función nativa, es importante que la memoria se anclado con [pin_ptr (C++ / CLI)](../windows/pin-ptr-cpp-cli.md) para impedir que los datos de cadena ubicarlos, un ciclo de recopilación de elementos no utilizados tendrá lugar al ejecuta la función no administrada.  
  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el cálculo de referencias de datos necesarios para tener acceso a una cadena Unicode en una función administrada llamada a una función no administrada. La función administrada, al recibir la cadena Unicode nativa, lo convierte en una cadena administrada mediante el <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> método.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)