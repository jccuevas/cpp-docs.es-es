---
title: "Error del evaluador de expresiones CXX0065 | Microsoft Docs"
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
  - "CXX0065"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0065"
  - "CXX0065"
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0065
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la variable necesita un marco de pila  
  
 Una expresión que contiene una variable perteneciente al ámbito actual pero que aún no se ha creado.  
  
 Este error puede ocurrir cuando se ha ejecutado el prólogo de una función pero todavía no se ha establecido el marco de pila para la función, o si se ha ejecutado paso a paso el código de salida para la función.  
  
 Recorra el código de prólogo hasta haber definido el marco de pila antes de evaluar la expresión.  
  
 Este error es idéntico a CAN0065.