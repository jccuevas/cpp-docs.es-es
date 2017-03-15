---
title: "C&#243;mo: Tener acceso a caracteres en un objeto System::String | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "caracteres [C++], obtener acceso en System::String"
  - "ejemplos [C++], cadenas"
  - "cadenas [C++], obtener acceso a caracteres"
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# C&#243;mo: Tener acceso a caracteres en un objeto System::String
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se puede tener acceso a los caracteres de un objeto <xref:System.String> para las llamadas de alto rendimiento a funciones no administradas que toman cadenas `wchar_t*`.  El método produce un puntero interior al primer carácter del objeto <xref:System.String>.  Se puede manipular este puntero directamente o se puede anclar y pasar a una función que espera una cadena `wchar_t` normal.  
  
## Ejemplo  
 `PtrToStringChars` devuelve un valor <xref:System.Char>, que es un puntero interior \(también conocido como `byref`\).  Como tal, está sujeto a la recolección de elementos no utilizados.  No es necesario que ancle este puntero a menos que vaya a pasarlo a una función nativa.  
  
 Observe el código siguiente.  No hace falta anclarlo porque `ppchar` es un puntero interior y, si el recolector de elementos no utilizados mueve la cadena a la que señala, también actualizará `ppchar`.  Sin [pin\_ptr \(C\+\+\/CLI\)](../Topic/pin_ptr%20\(C++-CLI\).md), el código funcionará y no tendrá el rendimiento potencial debido al anclaje.  
  
 Si pasa `ppchar`  a una función nativa, entonces deberá ser un puntero anclado; el recolector de elementos no utilizados no podrá actualizar punteros en el marco no administrado de la pila.  
  
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
  
  **abcdefg**   
## Ejemplo  
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
  
 **7**   
## Ejemplo  
 Un puntero interior tiene todas las propiedades de un puntero de C\+\+ nativo.  Por ejemplo, puede utilizarlo para recorrer una estructura de datos vinculada y hacer inserciones y eliminaciones sólo mediante un puntero:  
  
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
  
## Vea también  
 [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)