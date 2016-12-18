---
title: "Error del compilador C2860 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2860"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2860"
ms.assetid: ccc83553-90ed-4e94-b5e9-38b58ae38e31
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2860
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'void' no puede ser un tipo de argumento, con la excepción de '\(void\)'  
  
 El tipo `void` no se puede utilizar como tipo de argumento en otros argumentos.  
  
 El código siguiente genera el error C2860:  
  
```  
// C2860.cpp  
// compile with: /c  
void profunc1(void, int i);   // C2860  
void func10(void);   // OK  
```