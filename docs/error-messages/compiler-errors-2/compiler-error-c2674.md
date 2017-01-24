---
title: "Error del compilador C2674 | Microsoft Docs"
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
  - "C2674"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2674"
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2674
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permite una declaración genérica en este contexto  
  
 Se ha declarado incorrectamente una declaración genérica.  Para obtener más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2674.  
  
```  
// C2674.cpp  
// compile with: /clr /c  
void F(generic <class T> ref class R1);   // C2674  
generic <class T> ref class R2 {};   // OK  
```