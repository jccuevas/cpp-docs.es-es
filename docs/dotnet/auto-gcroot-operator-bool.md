---
title: "auto_gcroot::operator bool | Microsoft Docs"
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
  - "auto_gcroot.operator bool"
  - "auto_gcroot::operator bool"
  - "msclr.auto_gcroot.operator bool"
  - "msclr::auto_gcroot::operator bool"
  - "operator bool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bool (operador)"
ms.assetid: 87d38498-4221-4de8-8d02-c2dd2e6274ec
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_gcroot::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Operador para utilizar `auto_gcroot` en una expresión condicional.  
  
## Sintaxis  
  
```  
operator bool() const;  
```  
  
## Valor devuelto  
 `true` si el objeto temperaturescale es válido; `false` de otra manera.  
  
## Comentarios  
 Este operador convierte realmente a `_detail_class::_safe_bool` que es más seguro que `bool` porque no puede convertirse a un tipo entero.  
  
## Ejemplo  
  
```  
// msl_auto_gcroot_operator_bool.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s;  
   if ( s ) Console::WriteLine( "s is valid" );  
   if ( !s ) Console::WriteLine( "s is invalid" );  
   s = "something";  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
   s.reset();  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
}  
```  
  
  **s no es válida**  
**s es válida ahora**  
**s no es válida ahora**   
## Requisitos  
 **Archivo de encabezado** \<msclr\\auto\_gcroot.h\>  
  
 msclr de**Namespace**  
  
## Vea también  
 [auto\_gcroot \(Miembros\)](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::operator\!](../dotnet/auto-gcroot-operator-logical-not.md)