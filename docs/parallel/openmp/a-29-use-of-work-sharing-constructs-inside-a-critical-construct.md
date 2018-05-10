---
title: A.29 para compartir el uso de trabajo construye dentro de una construcción crítica | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ccbb39a9067adf545339d02fe0c05e24fbcdb0a4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="a29---use-of-work-sharing-constructs-inside-a-critical-construct"></a>A.29 Uso de construcciones de uso compartido en una construcción critical
En el ejemplo siguiente se muestra cómo utilizar una construcción de uso compartido dentro de un `critical` construir. En este ejemplo es compatible porque el uso compartido de construir y `critical` construcción no se enlaza a la misma región paralela.  
  
```  
void f()  
{  
  int i = 1;  
  #pragma omp parallel sections  
  {  
    #pragma omp section  
    {  
      #pragma omp critical (name)  
      {  
        #pragma omp parallel  
        {  
          #pragma omp single  
          {  
            i++;  
          }  
        }  
      }  
    }  
  }  
}  
```