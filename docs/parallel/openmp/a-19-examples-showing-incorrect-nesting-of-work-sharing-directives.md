---
title: Ejemplos A.19 que muestran el anidamiento incorrecto de directivas de uso compartido | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a3f8a4e1ca62a77c16dafedd0921ca842d7a048
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 Ejemplos donde se muestra un anidamiento incorrecto de directivas de uso compartido
Los ejemplos de esta sección muestra las reglas de anidamiento de directivas. Para obtener más información sobre el anidamiento de directivas, consulte [sección 2.9](../../parallel/openmp/2-9-directive-nesting.md) en la página 33.  
  
 En el ejemplo siguiente no es conforme porque interno y externo `for` directivas están anidadas y enlazar a los mismos `parallel` directiva:  
  
```  
void wrong1(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
      int i, j;  
      #pragma omp for  
      for (i=0; i<n; i++) {  
          #pragma omp for  
              for (j=0; j<n; j++)  
                 work(i, j);  
     }  
   }  
}  
```  
  
 La siguiente versión dinámicamente anidada del ejemplo anterior también será no compatible:  
  
```  
void wrong2(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++)  
        work1(i, n);  
  }  
}  
  
void work1(int i, int n)  
{  
  int j;  
  #pragma omp for  
    for (j=0; j<n; j++)  
      work2(i, j);  
}  
```  
  
 En el ejemplo siguiente no es conforme porque la `for` y `single` directivas están anidadas, y que se enlacen a la misma región paralela:  
  
```  
void wrong3(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        #pragma omp single  
          work(i);  
      }  
  }  
}  
```  
  
 En el ejemplo siguiente no es conforme porque un `barrier` directiva dentro de un `for` puede dar lugar a un interbloqueo:  
  
```  
void wrong4(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        work1(i);  
        #pragma omp barrier  
        work2(i);  
      }  
  }  
}  
```  
  
 En el ejemplo siguiente no es conforme porque el `barrier` da como resultado un interbloqueo, debido al hecho de que solo un subproceso a la vez puede entrar en la sección crítica:  
  
```  
void wrong5()  
{  
  #pragma omp parallel  
  {  
    #pragma omp critical  
    {  
       work1();  
       #pragma omp barrier  
       work2();  
    }  
  }  
}  
```  
  
 En el ejemplo siguiente no es conforme porque la `barrier` da como resultado un interbloqueo, debido al hecho de que sólo un subproceso ejecuta el `single` sección:  
  
```  
void wrong6()  
{  
  #pragma omp parallel  
  {  
    setup();  
    #pragma omp single  
    {  
      work1();  
      #pragma omp barrier  
      work2();  
    }  
    finish();  
  }  
}  
```