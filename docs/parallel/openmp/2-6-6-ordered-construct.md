---
title: "2.6.6 ordered (construcción) | Documentos de Microsoft"
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
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e09a9d756cd068df9345034e26a4f152d3ac19fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="266-ordered-construct"></a>2.6.6 ordered (Construcción)
El siguiente bloque estructurado un **ordenados** directiva se ejecuta en el orden en el que se ejecutaría iteraciones en un bucle secuencial. La sintaxis de la **ordenados** directiva es como sigue:  
  
```  
#pragma omp ordered new-linestructured-block  
```  
  
 Un **ordenados** directiva debe estar en la extensión dinámica de un **para** o **for paralelos** construir. El **para** o **paralelas para** la directiva a la que el **ordenados** enlaza la construcción debe tener un **ordenados** cláusula especificada como se describe en [Sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11. En la ejecución de un **para** o **for paralelos** construir con un **ordenados** cláusula, **ordenados** construcciones se ejecutan de forma estricta en el orden en el que se ejecutaría en una ejecución secuencial del bucle.  
  
 Restricciones a la **ordenados** directiva son los siguientes:  
  
-   Una iteración de un bucle con una **para** construcción no debe ejecutar la misma directiva ordenada más de una vez y no debe ejecutar más de un **ordenados** directiva.