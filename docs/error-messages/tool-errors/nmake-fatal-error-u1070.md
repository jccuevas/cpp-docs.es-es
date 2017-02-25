---
title: "Error grave de NMAKE U1070 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1070"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1070"
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error grave de NMAKE U1070
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ciclo en definición de macro 'nombredemacro'  
  
 La definición de macro dada contiene una macro cuya definición contiene la macro dada.  Las definiciones de macro circulares no son válidas.  
  
## Ejemplo  
 Las siguientes definiciones de macro  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 provocan el siguiente error:  
  
```  
cycle in macro definition 'TWO'  
```