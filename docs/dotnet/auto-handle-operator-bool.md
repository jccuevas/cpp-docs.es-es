---
title: "auto_handle::operator bool | Microsoft Docs"
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
  - "auto_handle.operator bool"
  - "msclr.auto_handle.operator bool"
  - "operator bool"
  - "msclr::auto_handle::operator bool"
  - "auto_handle::operator bool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_handle::operator bool"
ms.assetid: 2e535e99-cf87-4008-b588-02c587d77453
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_handle::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Operador para utilizar `auto_handle` en una expresión condicional.  
  
## Sintaxis  
  
```  
operator bool();  
```  
  
## Valor devuelto  
 `true` si el objeto temperaturescale es válido; `false` de otra manera.  
  
## Comentarios  
 Este operador convierte realmente a `_detail_class::_safe_bool` que es más seguro que `bool` porque no puede convertirse a un tipo entero.  
  
## Ejemplo  
  
```  
// msl_auto_handle_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_handle.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_handle<String> s1;  
   auto_handle<String> s2 = "hi";  
   if ( s1 ) Console::WriteLine( "s1 is valid" );  
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
 [auto\_handle::operator\!](../dotnet/auto-handle-operator-logical-not.md)