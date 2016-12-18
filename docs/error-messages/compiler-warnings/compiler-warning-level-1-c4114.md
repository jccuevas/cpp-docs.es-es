---
title: "Advertencia del compilador (nivel 1) C4114 | Microsoft Docs"
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
  - "C4114"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4114"
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4114
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el mismo calificador de tipo se ha utilizado más de una vez  
  
 Una declaración o definición de tipos utiliza un calificador de tipo \(**const**, `volatile`, **signed** o `unsigned`\) más de una vez.  Esto provoca una advertencia con las extensiones de Microsoft \(\/Ze\) y un error cuando está habilitada la compatibilidad con ANSI \(\/Za\).  
  
 El código siguiente genera el error C4114:  
  
```  
// C4114.cpp  
// compile with: /W1 /c  
volatile volatile int i;   // C4114  
```  
  
 El código siguiente genera el error C4114:  
  
```  
// C4114_b.cpp  
// compile with: /W1 /c  
static const int const * ii;   // C4114  
static const int * const iii;   // OK  
```