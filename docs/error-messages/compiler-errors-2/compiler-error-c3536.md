---
title: "Error del compilador C3536 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3536"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3536"
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3536
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"símbolo": no se puede usar antes de inicializarlo  
  
 No se puede usar el símbolo indicado antes de inicializarlo.  En la práctica, esto significa que una variable no se puede usar para inicializarse a sí misma.  
  
### Para corregir este error  
  
1.  No use una variable para inicializarse a sí misma.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3536 porque se usa cada variable para inicializarse a sí misma.  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)