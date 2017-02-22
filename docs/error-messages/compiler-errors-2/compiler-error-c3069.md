---
title: "Error del compilador C3069 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3069"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3069"
ms.assetid: ca94291b-2bb4-4e3f-9acf-534234b83513
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3069
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator': no se permite para el tipo de enumeración  
  
 Un operador no se admite en las enumeraciones de CLR.  Para más información, consulte [Uso de operadores y enumeraciones](../../misc/operators-and-enumerations.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3069:  
  
```  
// C3069.cpp // compile with: /clr enum struct E { e1 }; enum F { f1 }; int main() { E e = E::e1; bool tf; tf = !e;   // C3069 // supported for native enums F f = f1; tf = !f; }  
```