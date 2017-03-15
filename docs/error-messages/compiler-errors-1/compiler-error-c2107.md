---
title: "Error del compilador C2107 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2107"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2107"
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2107
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

índice no válido, direccionamiento indirecto no permitido  
  
 Se ha intentado aplicar un subíndice a una expresión que no se evalúa como puntero.  
  
## Ejemplo  
 El error C2107 puede aparecer si utiliza incorrectamente el puntero `this` de un tipo de valor para tener acceso al indizador predeterminado del tipo.  Para obtener más información, vea [Semántica de este puntero](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).  
  
 El código siguiente genera el error C2107.  
  
```  
// C2107.cpp  
// compile with: /clr  
using namespace System;  
  
value struct B {  
   property String ^ default[String ^] {  
      String ^ get(String ^ data) {  
         return "abc";  
      }  
   }  
   void Test() {  
      Console::WriteLine("{0}", this["aa"]);   // C2107  
      Console::WriteLine("{0}", this->default["aa"]);   // OK  
   }  
};  
  
int main() {  
   B ^ myb = gcnew B();  
   myb->Test();  
}  
```