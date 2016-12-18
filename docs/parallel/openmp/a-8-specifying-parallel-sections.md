---
title: "A.8   Specifying Parallel Sections | Microsoft Docs"
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
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.8   Specifying Parallel Sections
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

en el ejemplo siguiente, \(para [sección 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) en la página 14\) funciona el *xaxis*, el *yaxis*, y el *zaxis* se pueden ejecutar en paralelo.  la primera directiva de `section` es opcional.  Observe que todas las directivas de `section` deben aparecer en la extensión léxica de construcciónde `parallel``sections` .  
  
```  
#pragma omp parallel sections  
{  
    #pragma omp section  
        xaxis();  
    #pragma omp section  
        yaxis();  
    #pragma omp section  
        zaxis();  
}  
```