---
title: "swap (Funci&#243;n) (auto_gcroot) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::swap"
  - "msclr.swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap (función)"
ms.assetid: 2fe8146b-a7f7-445a-9ae9-53b5556be701
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# swap (Funci&#243;n) (auto_gcroot)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Objetos de los intercambios entre un `auto_gcroot` y otro.  
  
## Sintaxis  
  
```  
template<typename _element_type>  
void swap(  
   auto_gcroot<_element_type> & _left,  
   auto_gcroot<_element_type> & _right  
);  
```  
  
#### Parámetros  
 `_left`  
 Interfaz `auto_gcroot`.  
  
 `_right`  
 Otro objeto `auto_gcroot`.  
  
## Ejemplo  
  
```  
// msl_swap_auto_gcroot.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s1 = "string one";  
   auto_gcroot<String^> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   swap( s1, s2 );  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
}  
```  
  
  **S1 \= “cadena una”, s2 \= “cadena dos”**  
**S1 \= “cadena dos”, s2 \= “cadena una”**   
## Requisitos  
 **Archivo de encabezado** \<msclr\\auto\_gcroot.h\>  
  
 msclr de**Namespace**  
  
## Vea también  
 [auto\_gcroot](../dotnet/auto-gcroot.md)   
 [auto\_gcroot::swap](../dotnet/auto-gcroot-swap.md)