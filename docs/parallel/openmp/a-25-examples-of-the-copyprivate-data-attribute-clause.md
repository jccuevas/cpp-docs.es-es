---
title: "A.25   Examples of the copyprivate Data Attribute Clause | Microsoft Docs"
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
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.25   Examples of the copyprivate Data Attribute Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la cláusula de**ejemplo 1:** The `copyprivate` \([sección 2.7.2.8](../Topic/2.7.2.8%20copyprivate.md) en la página 32\) se puede utilizar para propagar la configuración adquiridos por un subproceso directamente a todas las instancias de las variables privadas de los otros subprocesos.  
  
```  
float x, y;  
#pragma omp threadprivate(x, y)  
  
void init( )   
{  
    float a;  
    float b;  
  
    #pragma omp single copyprivate(a,b,x,y)  
    {  
        get_values(a,b,x,y);  
    }  
  
    use_values(a, b, x, y);  
}  
```  
  
 Si *el init* rutinario se denomina de una región en serie, el comportamiento no se ve afectado por la presencia de las directivas.  Después de la llamada a la rutina *de los get\_values* ha sido ejecutada por un subproceso, ningún subproceso sale de la construcción hasta los objetos privados notificados por *a*, *b*, *x*, y *y* en todos los subprocesos ha vuelto a definir con la lectura de valores.  
  
 **ejemplo 2:** In Contrast To el ejemplo anterior, supone que la lectura se debe realizar mediante un subproceso determinado, indica el subproceso principal.  En este caso, la cláusula de `copyprivate` no se puede utilizar para hacer la difusión directamente, sino que se puede utilizar para proporcionar acceso a un objeto compartido temporal.  
  
```  
float read_next( )   
{  
    float * tmp;  
    float return_val;  
  
    #pragma omp single copyprivate(tmp)  
    {  
        tmp = (float *) malloc(sizeof(float));  
    }  
  
    #pragma omp master  
    {  
        get_float( tmp );  
    }  
  
    #pragma omp barrier  
    return_val = *tmp;  
    #pragma omp barrier  
  
    #pragma omp single  
    {  
       free(tmp);  
    }  
  
    return return_val;  
}  
```  
  
 **ejemplo 3:** Suppose que el número de objetos de bloqueo necesarios dentro de una región paralela no se puede determinar con facilidad antes de escribir.  La cláusula de `copyprivate` se puede utilizar para proporcionar acceso a los objetos compartidos de bloqueo que se asignan en esa región paralela.  
  
```  
#include <omp.h>  
  
omp_lock_t *new_lock()  
{  
    omp_lock_t *lock_ptr;  
  
    #pragma omp single copyprivate(lock_ptr)  
    {  
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));  
        omp_init_lock( lock_ptr );  
    }  
  
    return lock_ptr;  
}  
```