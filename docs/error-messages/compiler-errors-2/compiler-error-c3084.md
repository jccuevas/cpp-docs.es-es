---
title: "Error del compilador C3084 | Microsoft Docs"
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
  - "C3084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3084"
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': un finalizador o destructor no puede ser 'keyword'  
  
 Se declaró un destructor o finalizador de forma incorrecta.  
  
 Por ejemplo, un destructor no debería marcarse como sealed.  El destructor no será accesible para los tipos derivados.  Para más información, vea [Invalidaciones explícitas](../../windows/explicit-overrides-cpp-component-extensions.md) y [Destructores y finalizadores de Visual C\+\+](../../misc/destructors-and-finalizers-in-visual-cpp.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3084.  
  
```  
// C3084.cpp // compile with: /clr /c ref struct R { protected: !R() sealed;   // C3084 !R() abstract;   // C3084 !R(); };  
```