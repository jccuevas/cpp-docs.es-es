---
title: "C&#243;mo: Implementar las palabras claves is y as de C# (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "as (palabra clave) en C# [C++]"
  - "is (palabra clave) en C# [C++]"
ms.assetid: bc66c0d1-696b-480d-977c-5d9d1ad1ece6
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Implementar las palabras claves is y as de C# (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra cómo implementar la funcionalidad de las palabras clave de C\# `is` y `as` en Visual C\+\+.  
  
 Para obtener más información, vea [is](../Topic/is%20\(C%23%20Reference\).md) y [as](../Topic/as%20\(C%23%20Reference\).md).  
  
## Ejemplo  
  
```  
// CS_is_as.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I {  
public:  
   void F();  
};  
  
ref struct C : public I {  
   virtual void F( void ) { }  
};  
  
template < class T, class U >   
Boolean isinst(U u) {  
   return dynamic_cast< T >(u) != nullptr;  
}  
  
int main() {  
   C ^ c = gcnew C();  
   I ^ i = safe_cast< I ^ >(c);   // is (maps to castclass in IL)  
   I ^ ii = dynamic_cast< I ^ >(c);   // as (maps to isinst in IL)  
  
   // simulate 'as':  
   Object ^ o = "f";  
   if ( isinst< String ^ >(o) )  
      Console::WriteLine("o is a string");  
}  
```  
  
  **o es una cadena**   
## Vea también  
 [Interoperabilidad con otros lenguajes de .NET](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)