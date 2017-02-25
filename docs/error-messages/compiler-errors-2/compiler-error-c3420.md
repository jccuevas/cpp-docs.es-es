---
title: "Error del compilador C3420 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3420"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3420"
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# Error del compilador C3420
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'finalizador': un finalizador no puede ser virtual  
  
 Solo se puede llamar a un finalizador de forma no virtual desde su tipo envolvente. Por consiguiente, es un error declarar un finalizador virtual.  
  
 Para obtener más información, consulte [Destructores y finalizadores de Visual C\+\+](../../misc/destructors-and-finalizers-in-visual-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3420.  
  
```  
// C3420.cpp // compile with: /clr /c ref class R { virtual !R() {}   // C3420 };  
```