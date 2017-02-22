---
title: "Error del compilador C2683 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2683"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2683"
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2683
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'conversión de tipos' : 'tipo' no es un tipo polimórfico  
  
 No se puede usar [dynamic\_cast](../../cpp/dynamic-cast-operator.md) para convertir desde una clase no polimórfica \(una clase sin funciones virtuales\).  
  
 Se puede utilizar [static\_cast](../../cpp/static-cast-operator.md) para realizar conversiones de tipos no polimórficos.  Sin embargo, `static_cast` no realiza una comprobación en tiempo de ejecución.  
  
 El código siguiente genera el error C2683:  
  
```  
// C2683.cpp  
// compile with: /c  
class B { };  
class D : public B { };  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  // C2683  
   D* pd1 = static_cast<D*>(pb);   // OK  
}  
```