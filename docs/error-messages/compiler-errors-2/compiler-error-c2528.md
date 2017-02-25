---
title: "Error del compilador C2528 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2528"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2528"
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2528
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre' : el puntero a referencia no es válido  
  
 No se puede declarar un puntero a una referencia.  Desreferencie la variable antes de declarar un puntero a ella.  
  
 El código siguiente genera el error C2528:  
  
```  
// C2528.cpp  
int i;  
int &ir = i;  
int & (*irptr) = ir;    // C2528  
```