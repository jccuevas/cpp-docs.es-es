---
title: "Error irrecuperable C1002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1002"
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error irrecuperable C1002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el compilador no tiene espacio en el montón en el paso 2  
  
 El compilador se ha quedado sin espacio de memoria dinámica durante su segunda pasada, probablemente debido a un programa con demasiados símbolos o expresiones complejas.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Divida el archivo de código fuente en varios archivos más pequeños.  
  
2.  Descomponga las expresiones en subexpresiones más pequeñas.  
  
3.  Quite otros programas o controladores que consuman memoria.