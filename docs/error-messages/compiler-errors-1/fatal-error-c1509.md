---
title: "Error irrecuperable C1509 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1509"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1509"
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error irrecuperable C1509
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador: hay demasiados estados de controlador de excepciones en la función “función”. simplifique la función  
  
 El código supera el límite interno de estados de controlador de excepciones \(32.768 estados\).  
  
 La causa más común de este error es que la función contenga una expresión compleja de variables de clase definidas por el usuario y operadores aritméticos.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Simplifique las expresiones asignando las subexpresiones comunes a variables temporales.  
  
2.  Divida la función en funciones más pequeñas.