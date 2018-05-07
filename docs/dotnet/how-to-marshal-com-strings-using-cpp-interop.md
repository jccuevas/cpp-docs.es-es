---
title: 'Cómo: serializar cadenas COM mediante la interoperabilidad de C++ | Documentos de Microsoft'
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
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 918825dd6563f59167baa844b94edfc1033498a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Cómo: serializar cadenas COM mediante la interoperabilidad de C++
Este tema muestra cómo puede ser una cadena BSTR (el formato de cadena básico preferido en programación COM) pase de una en una función no administrada y viceversa. Para interoperar con otros tipos de cadenas, vea los temas siguientes:  
  
-   [Cómo: Serializar cadenas Unicode mediante la interoperabilidad de C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Cómo: Serializar cadenas ANSI mediante la interoperabilidad de C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 El siguiente código, se ejemplos utilizan la [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma implementar administrados y funciones en el mismo archivo, pero estas funciones interoperan de la misma manera, si está definido en archivos independientes. No es necesario que los archivos que contienen únicamente funciones no administradas pueden compilarse con [/clr (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo se puede pasar una cadena BSTR (un formato de cadena utilizado en programación COM) de administrado a una función no administrada. Administrados de la llamada a función usa <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> para obtener la dirección de una representación de BSTR del contenido de una System.String. NET. Este puntero se ancla mediante [pin_ptr (C++ / CLI)](../windows/pin-ptr-cpp-cli.md) para asegurarse de que su dirección física no cambie durante un ciclo de recopilación de elementos no utilizados mientras se ejecuta la función no administrada. El recolector de elementos no utilizados está prohibido al mover la memoria hasta que el [pin_ptr (C++ / CLI)](../windows/pin-ptr-cpp-cli.md) sale del ámbito.  
  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo se puede pasar una cadena BSTR de no administrado a una función no administrada. La recepción puede usar la cadena de como una cadena BSTR o usar función administrada <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> para convertirlo en un <xref:System.String> para su uso con otras funciones administradas. Dado que la memoria que representa BSTR está asignada en el montón no administrado, no es necesario fijar, porque no hay ninguna colección de elementos no utilizados en el montón no administrado.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)