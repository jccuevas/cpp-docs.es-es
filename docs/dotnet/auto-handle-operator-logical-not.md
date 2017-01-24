---
title: "auto_handle::operator! | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr.auto_handle.operator!"
  - "msclr::auto_handle::operator!"
  - "auto_handle.operator!"
  - "auto_handle::operator!"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator!"
ms.assetid: 3f6c7729-3260-4842-87f9-c491c140b299
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle::operator!
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Operador para utilizar `auto_handle` en una expresión condicional.  
  
## Sintaxis  
  
```  
bool operator!();  
```  
  
## Valor devuelto  
 `true` si el objeto ajustado no es válida; `false` de otra manera.  
  
## Ejemplo  
  
```  
// msl_auto_handle_operator_not.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1;  
   auto_handle<String> s2 = "something";  
   if ( s1) Console::WriteLine( "s1 is valid" );  
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );  
   if ( s2 ) Console::WriteLine( "s2 is valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );  
   s2.reset();  
   if ( s2 ) Console::WriteLine( "s2 is now valid" );  
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );  
}  
```  
  
  **S1 es no válido**  
**s2 es válido**  
**s2 ahora no son válidos**   
## Requisitos  
 **Archivo de encabezado** \<msclr\\auto\_handle.h\>  
  
 msclr de**Namespace**  
  
## Vea también  
 [auto\_handle \(Miembros\)](../dotnet/auto-handle-members.md)   
 [auto\_handle::operator bool](../dotnet/auto-handle-operator-bool.md)