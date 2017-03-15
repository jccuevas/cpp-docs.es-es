---
title: "Prioridad en las reglas de inferencia | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reglas de inferencia en NMAKE"
  - "prioridad, regla de inferencia"
  - "reglas, inferencia"
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Prioridad en las reglas de inferencia
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si una regla de inferencia se define de forma múltiple, NMAKE utiliza la definición de precedencia más alta.  La lista siguiente muestra el orden de precedencia de mayor a menor:  
  
1.  Regla de inferencia definida en un archivo MAKE; las definiciones posteriores tienen precedencia.  
  
2.  Regla de inferencia definida en Tools.ini; las definiciones posteriores tienen precedencia.  
  
3.  Regla de inferencia predefinida.  
  
## Vea también  
 [Reglas de inferencia](../build/inference-rules.md)