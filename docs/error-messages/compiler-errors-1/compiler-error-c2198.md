---
title: "Error del compilador C2198 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2198"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2198"
ms.assetid: 638a845c-9d7f-4115-a9aa-d72455605668
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2198
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': no hay suficientes argumentos para la llamada  
  
 El compilador no encontró parámetros suficientes para realizar una llamada a la función o detectó una declaración de función incorrecta.  
  
 El ejemplo siguiente genera la advertencia C2198:  
  
```  
// C2198.c // compile with: /c void func( int, int ); int main() { func( 1 );   // C2198 only one actual parameter func( 1, 1 );   // OK }  
```