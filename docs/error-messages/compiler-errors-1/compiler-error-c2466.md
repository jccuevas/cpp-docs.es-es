---
title: "Error del compilador C2466 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2466"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2466"
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2466
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede asignar una matriz de tamaño constante 0  
  
 Se ha asignado o declarado una matriz de tamaño cero.  La expresión constante del tamaño de matriz debe ser un entero mayor que cero.  Una declaración de matriz con un subíndice cero es válida sólo para una clase, estructura o unión y sólo con las extensiones de Microsoft \([\/Ze](../../build/reference/za-ze-disable-language-extensions.md)\).  
  
 El código siguiente genera el error C2466:  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```