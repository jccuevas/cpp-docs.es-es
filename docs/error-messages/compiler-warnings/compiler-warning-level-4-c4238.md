---
title: "Advertencia del compilador (nivel 4) C4238 | Microsoft Docs"
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
  - "C4238"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4238"
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4238
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar: valor\-R de clase utilizado como valor L  
  
 Por compatibilidad con versiones anteriores de Visual C\+\+, las extensiones de Microsoft \(**\/Ze**\) permiten utilizar un tipo de clase como valor R en un contexto que implícita o explícitamente tome su dirección correspondiente.  En algunos casos, como en el ejemplo siguiente, esto puede resultar peligroso.  
  
## Ejemplo  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 Esta práctica genera un error en condiciones de compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).