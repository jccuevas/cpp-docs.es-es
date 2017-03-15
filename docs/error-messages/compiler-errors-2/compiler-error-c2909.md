---
title: "Error del compilador C2909 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2909"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2909"
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2909
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': la creación de instancias explícita de la plantilla de función requiere un tipo de valor devuelto  
  
 La creación de instancias explícita de una plantilla de función requiere la especificación explícita de su tipo de valor devuelto. La especificación de tipo de valor devuelto implícita no funciona.  
  
 El ejemplo siguiente genera la advertencia C2909:  
  
```  
// C2909.cpp // compile with: /c template<class T> int f(T); template f<int>(int);         // C2909 template int f<int>(int);   // OK  
```