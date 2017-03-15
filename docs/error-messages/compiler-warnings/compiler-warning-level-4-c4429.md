---
title: "Advertencia del compilador (nivel 4) C4429 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4429"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4429"
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 4) C4429
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

nombre de carácter universal posiblemente incompleto o incorrectamente formado  
  
 El compilador detectó una secuencia de caracteres que puede ser un nombre de carácter universal mal formado.  Un nombre de carácter universal va `\u` seguido de 4 u 8 dígitos hexadecimales. `\U`  
  
 El código siguiente genera el error C4429:  
  
```  
// C4429.cpp  
// compile with: /W4 /WX  
int \ug0e4 = 0;   // C4429  
// Try the following line instead:  
// int \u00e4 = 0;   // OK, a well-formed universal character name.  
```