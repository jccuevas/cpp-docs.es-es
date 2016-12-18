---
title: "operator . | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "operator ."
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dot operator (.)"
  - "operator ."
  - ". operator"
ms.assetid: 468ea0c8-5b08-47be-991b-38abacb77611
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator .
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El primer operador devuelve *la expresión* más el desplazamiento *del campo* de su estructura o unión.  El segundo operador devuelve value en la ubicación indicada por *el registro* más el desplazamiento *del campo* de su estructura o unión.  
  
## Sintaxis  
  
```  
  
      expression  
      . field [[. field]]...  
[register]. field [[. field]]...  
```  
  
## Vea también  
 [Operators Reference](../../assembler/masm/operators-reference.md)