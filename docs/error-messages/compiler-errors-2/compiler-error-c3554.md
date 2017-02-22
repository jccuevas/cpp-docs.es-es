---
title: "Error del compilador C3554 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3554"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3554"
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Error del compilador C3554
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'decltype' no se puede combinar con ningún otro especificador de tipo  
  
 No se puede calificar la palabra clave `decltype()` con ningún especificador de tipo. Por ejemplo, el siguiente fragmento de código genera el error C3554.  
  
```  
int x; unsigned decltype(x); // C3554  
```