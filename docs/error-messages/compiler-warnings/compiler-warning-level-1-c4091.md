---
title: "Advertencia del compilador (nivel 1) C4091 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4091"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4091"
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 1) C4091
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'palabra clave' : se ha omitido a la izquierda de 'tipo' cuando no hay ninguna variable declarada  
  
 El compilador ha detectado una situación en la que es probable que el usuario haya intentado declarar una variable, pero el compilador no ha podido declarar la variable.  
  
## Ejemplo  
 Un atributo `__declspec` al comienzo de una declaración de tipos definidos por el usuario se aplica a la variable de ese tipo.  La advertencia C4091 indica que no se ha declarado ninguna variable.  El ejemplo siguiente genera el error C4091.  
  
```  
// C4091.cpp  
// compile with: /W1 /c  
__declspec(dllimport) class X {}; // C4091  
  
// __declspec attribute applies to varX  
__declspec(dllimport) class X2 {} varX;  
  
// __declspec attribute after the class or struct keyword   
// applies to user defined type  
class __declspec(dllimport) X3 {};  
```  
  
## Ejemplo  
 Si un identificador es de tipo typedef, no puede ser a la vez un nombre de variable.  El ejemplo siguiente genera el error C4091.  
  
```  
// C4091_b.cpp  
// compile with: /c /W1 /WX  
#define LIST 4  
typedef struct _LIST {} LIST;   // C4091  
```