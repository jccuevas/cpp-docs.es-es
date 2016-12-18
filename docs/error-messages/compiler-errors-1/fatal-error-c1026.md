---
title: "Error irrecuperable C1026 | Microsoft Docs"
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
  - "C1026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1026"
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

desbordamiento de la pila del analizador, programa demasiado complejo  
  
 El espacio requerido para analizar el programa ha producido un desbordamiento de la pila del compilador.  
  
 Reduzca la complejidad de las expresiones:  
  
-   Reduciendo el anidamiento en las instrucciones `for` y `switch`.  Colocando las instrucciones más anidadas en funciones independientes.  
  
-   Descomponiendo las expresiones largas que utilicen operadores coma o llamadas a funciones.