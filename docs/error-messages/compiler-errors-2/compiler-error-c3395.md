---
title: "Error del compilador C3395 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3395"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3395"
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3395
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : \_\_declspec\(dllexport\) no se puede aplicar a una función con la convención de llamada \_\_clrcall  
  
 `__declspec(dllexport)` y [\_\_clrcall](../../cpp/clrcall.md) no son compatibles.  Para obtener más información, vea [dllexport, dllimport](../../cpp/dllexport-dllimport.md).  
  
 El código siguiente genera el error C3395:  
  
```  
// C3395.cpp  
// compile with: /clr /c  
  
__declspec(dllexport) void __clrcall Test(){}   // C3395  
void __clrcall Test2(){}   // OK  
__declspec(dllexport) void Test3(){}   // OK  
```