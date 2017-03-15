---
title: "A.27   Use of C99 Variable Length Arrays | Microsoft Docs"
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
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.27   Use of C99 Variable Length Arrays
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El ejemplo siguiente muestra cómo utilizar las matrices de longitud variable C99 \(VLAs\) en una directiva de `firstprivate` \([sección 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) en la página 26\).  
  
> [!NOTE]
>  Las matrices de longitud variable no se admiten en Visual C\+\+.  
  
```  
void f(int m, int C[m][m])  
{  
    double v1[m];  
    ...  
    #pragma omp parallel firstprivate(C, v1)  
    ...  
}  
```