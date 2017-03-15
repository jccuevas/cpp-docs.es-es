---
title: "A.9   Using single Directives | Microsoft Docs"
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
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.9   Using single Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El ejemplo siguiente se muestra la directiva de `single` \([sección 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) en la página 15\).  En el ejemplo, solo un subproceso \(normalmente el primer subproceso que busca la directiva de `single` \) imprime el mensaje de progreso.  El usuario no debe tener ninguna idea preconcebida acerca de qué el subproceso ejecute la sección de `single` .  Los demás omitir la sección de `single` y detendrá en la barrera al final de la construcción de `single` .  Si otros subprocesos pueden continuar sin esperar a que el subproceso que ejecuta la sección de `single` , una cláusula de `nowait` se puede especificar en la directiva de `single` .  
  
```  
#pragma omp parallel  
{  
    #pragma omp single  
        printf_s("Beginning work1.\n");  
    work1();  
    #pragma omp single  
        printf_s("Finishing work1.\n");  
    #pragma omp single nowait  
        printf_s("Finished work1 and beginning work2.\n");  
    work2();  
}  
```