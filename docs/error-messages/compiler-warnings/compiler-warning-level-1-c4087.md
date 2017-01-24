---
title: "Advertencia del compilador (nivel 1) C4087 | Microsoft Docs"
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
  - "C4087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4087"
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': se ha declarado con la lista de parámetros 'void'.  
  
 La declaración de función no tiene parámetros formales, pero la llamada de función tiene parámetros reales. Se pasan parámetros adicionales según la convención de llamada de la función.  
  
 Esta advertencia es para el compilador de C.  
  
## Ejemplo  
  
```  
// C4087.c // compile with: /W1 int f1( void ) { } int main() { f1( 10 );   // C4087 }  
```