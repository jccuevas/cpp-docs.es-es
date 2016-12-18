---
title: "Error del compilador C3223 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3223"
ms.assetid: 1f4380b4-0413-40db-a868-62f97babaf78
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'property': no se puede aplicar 'typeid' a una propiedad  
  
 No se puede aplicar [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) a una propiedad.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3223.  
  
```  
// C3223.cpp // compile with: /clr ref class R { public: property int myprop; }; int main() { System::Type^ type2 = R::myprop::typeid;   // C3223 }  
```