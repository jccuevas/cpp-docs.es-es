---
title: "push_macro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.push_macro"
  - "push_macro_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pragma (directivas), push_macro"
  - "push_macro (pragma)"
ms.assetid: ac89efc9-afd1-4dfe-bfd1-497229b3e81d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# push_macro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Guarda el valor de la macro *macro\_name* en la parte superior de la pila para esta macro.  
  
## Sintaxis  
  
```  
  
#pragma push_macro("  
macro_name  
")  
  
```  
  
## Comentarios  
 Puede recuperar el valor de *macro\_name* con **pop\_macro**.  
  
 Vea [pop\_macro](../preprocessor/pop-macro.md) para ver un ejemplo.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)