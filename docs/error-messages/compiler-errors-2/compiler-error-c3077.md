---
title: "Error del compilador C3077 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3077"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3077"
ms.assetid: d9f3c619-d1e2-4656-81a5-a35a9586a7d4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3077
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'finalizer': un finalizador solamente puede ser miembro de un tipo de referencia  
  
 No se puede declarar un finalizador en un tipo de valor o nativo.  
  
 Para obtener más información, consulta [Destructores y finalizadores de Visual C\+\+](../../misc/destructors-and-finalizers-in-visual-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3077.  
  
```  
// C3077.cpp // compile with: /clr /c value struct vs { !vs(){}   // C3077 }; ref struct rs { protected: !rs(){}   // OK };  
```