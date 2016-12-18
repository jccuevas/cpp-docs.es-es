---
title: "Error del compilador C3080 | Microsoft Docs"
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
  - "C3080"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3080"
ms.assetid: ff62a3f7-9b3b-44bd-b8d9-f3a8e5354560
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3080
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función\_finalizador': un finalizador no puede tener un especificador de clase de almacenamiento.  
  
 Para obtener más información, consulta [Destructores y finalizadores de Visual C\+\+](../../misc/destructors-and-finalizers-in-visual-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3080.  
  
```  
// C3080.cpp // compile with: /clr /c ref struct rs { protected: static !rs(){}   // C3080 !rs(){}   // OK };  
```