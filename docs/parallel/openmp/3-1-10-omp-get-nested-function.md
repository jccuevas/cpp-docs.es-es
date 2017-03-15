---
title: "3.1.10 omp_get_nested Function | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.10 omp_get_nested Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función de `omp_get_nested` devuelve un valor distinto de cero si se habilita el paralelismo anidados y 0 si está deshabilitado.  Para obtener más información sobre el paralelismo anidadas, vea la sección 3.1.9 en la página 40.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 Si una implementación no implementa paralelismo anidados, esta función siempre devuelve 0.