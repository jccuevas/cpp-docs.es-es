---
title: "2.5.2 parallel sections Construct | Microsoft Docs"
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
ms.assetid: 94220e27-14f8-465c-bd8d-eb960b4b5dee
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.5.2 parallel sections Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva de **secciones paralelas** proporciona un formulario de acceso directo para especificar una región de **Paralelo** que contiene solo una única directiva de **secciones** .  La semántica es idéntica explícitamente a especificar una directiva de **Paralelo** inmediatamente seguida de una directiva de **secciones** .  La sintaxis de la directiva de **secciones paralelas** es la siguiente:  
  
```  
#pragma omp parallel sections  [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-line  
      structured-block  ]  
   ...  
}  
```  
  
 *La cláusula* puede ser una de las cláusulas consolidar las directivas de **Paralelo** y de **secciones** , excepto la cláusula de **nowait** .  
  
## referencias cruzadas:  
  
-   La directiva de**Paralelo** , vea [sección 2,3](../../parallel/openmp/2-3-parallel-construct.md) en la página 8.  
  
-   la directiva de**secciones** , vea [sección 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) en la página 14.