---
title: "Advertencia del compilador (nivel 1) C4138 | Microsoft Docs"
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
  - "C4138"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4138"
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4138
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\*\/' se encontró fuera del comentario  
  
 El delimitador de comentario de cierre no está precedido de un delimitador de comentario de apertura. El compilador supone que hay un espacio entre el asterisco \(**\***\) y la barra diagonal \(\/\).  
  
## Ejemplo  
  
```  
// C4138a.cpp // compile with: /W1 int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning int main() { }  
```  
  
 Esta advertencia puede producirse en un intento de anidar comentarios.  
  
 Esta advertencia puede evitarse si convierte en comentario las secciones de código que contienen comentarios, incluye el código en un bloque **\#if\/\#endif** y establece la expresión de control en cero:  
  
```  
// C4138b.cpp // compile with: /W1 #if 0 int my_variable;   /* Declaration currently not needed */ #endif int main() { }  
```