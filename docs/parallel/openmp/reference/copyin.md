---
title: "copyin | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "copyin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copyin OpenMP clause"
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# copyin
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Permite que los subprocesos tienen acceso al valor del subproceso principal, para una variable de [threadprivate](../../../parallel/openmp/reference/threadprivate.md) .  
  
## Sintaxis  
  
```  
copyin(var)  
```  
  
## Comentarios  
 donde  
  
 `var`  
 La variable de `threadprivate` que se inicializará con el valor de la variable en el subproceso principal, como existe antes de la construcción paralela.  
  
## Comentarios  
 `copyin` se aplica a las siguientes directivas:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [sections](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Para obtener más información, vea [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).  
  
## Ejemplo  
 Vea [threadprivate](../../../parallel/openmp/reference/threadprivate.md) para obtener un ejemplo de `copyin`mediante.  
  
## Vea también  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)