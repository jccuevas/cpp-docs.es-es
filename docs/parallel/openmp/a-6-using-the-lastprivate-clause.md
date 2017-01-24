---
title: "A.6   Using the lastprivate Clause | Microsoft Docs"
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
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.6   Using the lastprivate Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La ejecución correcta depende a veces el valor que la última iteración de las asignaciones de un bucle a una variable.  Tales programas deben enumerar todas las variables como argumentos a una cláusula de `lastprivate` \([sección 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) en la página 27\) de modo que los valores de las variables son iguales que cuando el bucle se ejecuta secuencialmente.  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 En el ejemplo anterior, el valor de `i` al final de la región paralela será igual que `n–1`, como en el caso secuencial.