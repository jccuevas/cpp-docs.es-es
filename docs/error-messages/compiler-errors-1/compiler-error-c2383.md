---
title: "Error del compilador C2383 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2383"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2383"
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2383
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo' : no se permiten argumentos predeterminados en este símbolo  
  
 El compilador de C\+\+ no permite argumentos predeterminados en punteros a funciones.  
  
 El compilador de la versión anterior aceptaba este código, pero ahora produce un error.  Para que el código funcione en todas las versiones de Visual C\+\+, no asigne un valor predeterminado a un argumento puntero a función.  
  
 La línea siguiente genera el error C2383:  
  
```  
// C2383.cpp  
// compile with: /c   
void (*pf)(int = 0);   // C2383  
void (*pf)(int);   // OK  
```