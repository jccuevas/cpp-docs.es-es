---
title: "Error del compilador C2081 | Microsoft Docs"
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
  - "C2081"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2081"
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2081
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : el nombre de la lista de parámetros formales no es válido  
  
 El identificador ha originado un error de sintaxis.  
  
 La causa de este error puede ser el uso del estilo anterior para la lista de parámetros formales.  Deberá especificarse el tipo de los parámetros formales en la lista.  
  
 El código siguiente genera el error C2081:  
  
```  
// C2081.c  
void func( int i, j ) {}  // C2081, no type specified for j  
```  
  
 Posible solución:  
  
```  
// C2081b.c  
// compile with: /c  
void func( int i, int j ) {}  
```