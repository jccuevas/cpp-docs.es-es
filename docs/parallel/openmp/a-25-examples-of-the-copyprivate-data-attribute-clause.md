---
title: "Ejemplos A.25 de la cláusula de atributo de datos copyprivate | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 7b1cb6a5-5691-4b95-b3ac-d7543ede6405
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7cdf7598e00bab72966fe79454567b0a59dcbaae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="a25---examples-of-the-copyprivate-data-attribute-clause"></a>A.25 Ejemplos de la cláusula de atributos de datos copyprivate
**Ejemplo 1:** el `copyprivate` cláusula ([sección 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) en la página 32) puede usarse para difundir valores adquiridos por un único subproceso directamente para todas las instancias de las variables privadas en los demás subprocesos.  
  
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
  
 Si la rutina *init* se llama desde una región de la serie, su comportamiento no resulta afectado por la presencia de las directivas. Después de llamar a la *get_values* rutina se ha ejecutado por un subproceso, ningún subproceso abandona la construcción hasta que los objetos privados designados por *una*, *b*, *x*, y *y* en todos los subprocesos se convierten en ha definido con los valores leídos.  
  
 **Ejemplo 2:** a diferencia del ejemplo anterior, suponga que un subproceso determinado, diga el subproceso principal debe realizar la operación de lectura. En este caso, el `copyprivate` cláusula no puede utilizarse para realizar la difusión directamente, pero se puede utilizar para proporcionar acceso a un objeto compartido temporal.  
  
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
  
 **Ejemplo 3:** suponga que el número de objetos de bloqueo necesarios dentro de una región paralela no se puede determinar fácilmente antes de escribir en él. El `copyprivate` cláusula puede usarse para proporcionar acceso a objetos de bloqueo compartido que se asignan dentro de esa región paralela.  
  
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