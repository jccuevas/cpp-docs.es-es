---
title: "Error del evaluador de expresiones CXX0064 | Microsoft Docs"
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
  - "CXX0064"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0064"
  - "CXX0064"
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0064
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede establecer el punto de interrupción en una función miembro virtual enlazada  
  
 Se ha definido un punto de interrupción en una función miembro virtual mediante un puntero a un objeto, así:  
  
```  
pClass->vfunc( int );  
```  
  
 Se puede definir un punto de interrupción en una función virtual escribiendo la clase, así:  
  
```  
Class::vfunc( int );  
```  
  
 Este error es idéntico a CAN0064.