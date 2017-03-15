---
title: "Advertencia del compilador (nivel 1) C4662 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4662"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4662"
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Advertencia del compilador (nivel 1) C4662
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

creación de instancias explícita; la clase de plantilla 'identifier1' no tiene definición a partir de la cual especializar 'identifier2'  
  
 La clase de plantilla especificada se declaró, pero no se definió.  
  
## Ejemplo  
  
```  
// C4662.cpp // compile with: /W1 /LD template<class T, int i> class MyClass; // no definition template MyClass< int, 1>;              // C4662  
```