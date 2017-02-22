---
title: "Error del compilador C2388 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2388"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2388"
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C2388
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo': un símbolo no se puede declarar con \_\_declspec\(Appdomain\) y \_\_declspec\(process\).  
  
 Los modificadores `appdomain` y `process` `__declspec` no pueden usarse en el mismo símbolo. El almacenamiento que existe para una variable es por proceso o por dominio de aplicación.  
  
 Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).  
  
 El ejemplo siguiente genera la advertencia C2388:  
  
```  
// C2388.cpp // compile with: /clr /c __declspec(process) __declspec(appdomain) int i;   // C2388 __declspec(appdomain) int i;   // OK  
```