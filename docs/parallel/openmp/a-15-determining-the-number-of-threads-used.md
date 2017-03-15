---
title: "A.15   Determining the Number of Threads Used | Microsoft Docs"
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
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.15   Determining the Number of Threads Used
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Considere el siguiente ejemplo incorrecto \(para [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en la página 37\):  
  
```  
np = omp_get_num_threads(); // misplaced   
#pragma omp parallel for schedule(static)  
    for (i=0; i<np; i++)  
        work(i);  
```  
  
 La llamada de `omp_get_num_threads()` devuelve 1 en la sección en serie del código, así que *NP* siempre será igual a 1 en el ejemplo anterior.  Para determinar el número de subprocesos que se implementarán para la región paralela, la llamada debe estar dentro de la región paralela.  
  
 El ejemplo siguiente se muestra cómo escribir este programa sin incluir una consulta para el número de subprocesos:  
  
```  
#pragma omp parallel private(i)  
{  
    i = omp_get_thread_num();  
    work(i);  
}  
```