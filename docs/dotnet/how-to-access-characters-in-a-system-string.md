---
title: 'Cómo: obtener acceso a caracteres en un System:: String | Documentos de Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ed9682492eedc915919758d42d5594560cb4a83a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129754"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Cómo: Tener acceso a caracteres en un objeto System::String
Puede obtener acceso a caracteres de un <xref:System.String> objeto para las llamadas de alto rendimiento a no administrado, las funciones que toman `wchar_t*` cadenas. El método produce un puntero interior al primer carácter de la <xref:System.String> objeto. This (puntero) se puede manipular directamente o anclado y pasa a una función que espera un normal `wchar_t` cadena.  
  
## <a name="example"></a>Ejemplo  
 `PtrToStringChars` Devuelve un <xref:System.Char>, que es un puntero interior (también conocido como un `byref`). Por lo tanto, resulta sujeta a la colección de elementos no utilizados. No tienes que anclar this (puntero), a menos que va a pasar a una función nativa.  
  
 Observe el código siguiente.  Fijar no es necesaria porque `ppchar` es un puntero interior y, si el recolector de elementos no utilizados mueve la cadena que señala, también actualizará `ppchar`. Sin un [pin_ptr (C++ / CLI)](../windows/pin-ptr-cpp-cli.md), el código funcionará y no tendrá el rendimiento potencial debido con anclados.  
  
 Si se pasa `ppchar` a una función nativa, a continuación, debe ser un puntero anclado; el recolector de elementos no utilizados no podrá actualizar punteros en el marco de pila no administrados.  
  
```  
// PtrToStringChars.cpp  
// compile with: /clr  
#include<vcclr.h>  
using namespace System;  
  
int main() {  
   String ^ mystring = "abcdefg";  
  
   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );  
  
   for ( ; *ppchar != L'\0'; ++ppchar )  
      Console::Write(*ppchar);  
}  
```  
  
```Output  
abcdefg  
```  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra dónde es preciso anclar.  
  
```  
// PtrToStringChars_2.cpp  
// compile with: /clr  
#include <string.h>  
#include <vcclr.h>  
// using namespace System;  
  
size_t getlen(System::String ^ s) {  
   // Since this is an outside string, we want to be secure.  
   // To be secure, we need a maximum size.  
   size_t maxsize = 256;  
   // make sure it doesn't move during the unmanaged call  
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);  
   return wcsnlen(pinchars, maxsize);  
};  
  
int main() {  
   System::Console::WriteLine(getlen("testing"));  
}  
```  
  
```Output  
7  
```  
  
## <a name="example"></a>Ejemplo  
 Un puntero interior tiene todas las propiedades de un puntero de C++ nativo. Por ejemplo, puede utilizar para recorrer una estructura de datos vinculado y hacer inserciones y eliminaciones sólo mediante un puntero:  
  
```  
// PtrToStringChars_3.cpp  
// compile with: /clr /LD  
using namespace System;  
ref struct ListNode {  
   Int32 elem;   
   ListNode ^ Next;  
};  
  
void deleteNode( ListNode ^ list, Int32 e ) {   
   interior_ptr<ListNode ^> ptrToNext = &list;  
   while (*ptrToNext != nullptr) {  
      if ( (*ptrToNext) -> elem == e )  
         *ptrToNext = (*ptrToNext) -> Next;   // delete node  
      else  
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node  
   }  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)