---
title: "Error del compilador C3295 | Microsoft Docs"
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
  - "C3295"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3295"
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3295
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\#pragma pragma' solo se puede usar en un ámbito global o de espacio de nombres  
  
 Algunas pragmas no se pueden usar en una función.  Vea [Directives pragma y la palabra clave \_\_pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3295.  
  
```  
// C3295.cpp int main() { #pragma managed   // C3295 }  
```