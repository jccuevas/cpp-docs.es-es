---
title: "Error del compilador C3189 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3189"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3189"
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3189
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declarador\<\>'abstracto de typeidtype: esta sintaxis ya no se admite, ::typeid de uso en su lugar  
  
 Se utilizó una forma obsoleta de [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md), utilice la nueva.  
  
 El código siguiente genera el error C3189:  
  
```  
// C3189.cpp  
// compile with: /clr  
int main() {  
   System::Type^ t  = typeid<System::Object>;   // C3189  
   System::Type^ t2  = System::Object::typeid;   // OK  
}  
```