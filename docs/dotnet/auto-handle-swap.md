---
title: "auto_handle::swap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::auto_handle::swap"
  - "auto_handle.swap"
  - "auto_handle::swap"
  - "msclr..auto_handle.swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::swap"
ms.assetid: 3ebf82d7-9b69-4a72-a22d-69b4f640f9b0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# auto_handle::swap
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Intercambia objetos con otro `auto_handle`.  
  
## Sintaxis  
  
```  
void swap(  
   auto_handle<_element_type> % _right  
);  
```  
  
#### Parámetros  
 `_right`  
 `auto_handle` con las que para cambiar objetos.  
  
## Ejemplo  
  
```  
// msl_auto_handle_swap.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1 = "string one";  
   auto_handle<String> s2 = "string two";  
  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
   s1.swap( s2 );  
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",  
      s1->ToString(), s2->ToString() );  
}  
```  
  
  **S1 \= “cadena una”, s2 \= “cadena dos”**  
**S1 \= “cadena dos”, s2 \= “cadena una”**   
## Requisitos  
 **Archivo de encabezado** \<msclr\\auto\_handle.h\>  
  
 msclr de**Namespace**  
  
## Vea también  
 [auto\_handle \(Miembros\)](../dotnet/auto-handle-members.md)   
 [swap \(Función\) \(auto\_handle\)](../dotnet/swap-function-auto-handle.md)