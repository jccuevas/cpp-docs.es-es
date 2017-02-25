---
title: "Error irrecuperable C1054 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1054"
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error irrecuperable C1054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador: los inicializadores están demasiado anidados  
  
 El código supera el límite de anidamiento para inicializadores \(de 10 a 15 niveles, según la combinación de tipos que se estén inicializando\).  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Reduzca el anidamiento simplificando los tipos de datos que se estén inicializando.  
  
2.  Inicialice las variables en instrucciones independientes después de la declaración.