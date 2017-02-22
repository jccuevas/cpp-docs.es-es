---
title: "Error del compilador C2108 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2108"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2108"
ms.assetid: c84f0b47-5e2c-47d2-8edb-427a40e17c36
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2108
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el subíndice no es de tipo entero  
  
 El subíndice de la matriz es una expresión no entera.  
  
## Ejemplo  
 El error C2108 puede aparecer si utiliza incorrectamente el puntero `this` de un tipo de valor para tener acceso al indizador predeterminado del tipo.  Para obtener más información, vea [Semántica de este puntero](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).  
  
 El código siguiente genera el error C2108.  
  
```  
// C2108.cpp  
// compile with: /clr  
using namespace System;  
  
value struct B {  
   property Double default[Double] {  
      Double get(Double data) {  
         return data*data;  
      }  
   }  
   void Test() {  
      Console::WriteLine("{0}", this[3.3]);   // C2108  
      Console::WriteLine("{0}", this->default[3.3]);   // OK  
   }  
};  
  
int main() {  
   B ^ myb = gcnew B();  
   myb->Test();  
}  
```