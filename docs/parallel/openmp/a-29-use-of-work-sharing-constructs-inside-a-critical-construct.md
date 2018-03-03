---
title: "A.29 para compartir el uso de trabajo construye dentro de una construcción crítica | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9bd95a689fbb643af5e2291c0a86b248705b5f9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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