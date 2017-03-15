---
title: "Advertencia del compilador (nivel 1) C4167 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4167"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4167"
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4167
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

función: solo disponible como función intrínseca  
  
 La **función \#pragma** intenta obligar al compilador a usar una llamada convencional a una función que debe usarse de forma intrínseca. La función pragma se ignorará.  
  
 Para evitar esta advertencia, quite la **función \#pragma**.  
  
## Ejemplo  
  
```  
// C4167.cpp // compile with: /W1 #include <malloc.h> #pragma function(_alloca )   // C4167: _alloca() is intrinsic only int main(){}  
```