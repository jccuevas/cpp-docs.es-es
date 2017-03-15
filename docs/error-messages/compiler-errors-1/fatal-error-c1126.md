---
title: "Error irrecuperable C1126 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1126"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1126"
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error irrecuperable C1126
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : la asignación automática supera el tamaño  
  
 El espacio asignado para las variables locales de una función \(más una cantidad limitada de espacio utilizada por el compilador, como, por ejemplo, 20 bytes adicionales para funciones intercambiables\) supera el límite.  
  
 Para corregir este error, utilice `malloc` o `new` para asignar cantidades grandes de datos.