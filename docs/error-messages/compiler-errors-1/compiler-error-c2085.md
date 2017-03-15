---
title: "Error del compilador C2085 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2085"
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : no está en la lista de parámetros formales  
  
 El identificador se ha declarado en una definición de función, pero no en la lista de parámetros formales \(sólo en ANSI C\).  
  
 El código siguiente genera el error C2085:  
  
```  
// C2085.c  
void func1( void )  
int main( void ) {}   // C2085  
```  
  
 Posible solución:  
  
```  
// C2085b.c  
void func1( void );  
int main( void ) {}  
```  
  
 Sin el punto y coma, `func1()` parecerá una definición de función, no un prototipo, por lo que `main` se definirá dentro de `func1()` y, con ello, se generará el error C2085 para el identificador `main`.