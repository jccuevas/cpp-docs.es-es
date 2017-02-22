---
title: "Error irrecuperable C1191 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1191"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1191"
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error irrecuperable C1191
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'dll' sólo se puede importar en un ámbito global  
  
 La instrucción para importar mscorlib.dll en un programa que utiliza programación \/clr debe aparecer en el ámbito global, no en un espacio de nombres o en una función.  
  
 El código siguiente genera el error C1191:  
  
```  
// C1191.cpp  
// compile with: /clr  
namespace sample {  
   #using <mscorlib.dll>   // C1191 not at global scope  
}  
```  
  
 Posible solución:  
  
```  
// C1191b.cpp  
// compile with: /clr /c  
#using <mscorlib.dll>  
namespace sample {}  
```