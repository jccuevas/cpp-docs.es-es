---
title: 2.6.6 ordered (construcción) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa66d9fb8a0a9af2fc33497690bfe67a3ea5d717
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="266-ordered-construct"></a>2.6.6 ordered (Construcción)
El siguiente bloque estructurado un **ordenados** directiva se ejecuta en el orden en el que se ejecutaría iteraciones en un bucle secuencial. La sintaxis de la **ordenados** directiva es como sigue:  
  
```  
#pragma omp ordered new-linestructured-block  
```  
  
 Un **ordenados** directiva debe estar en la extensión dinámica de un **para** o **for paralelos** construir. El **para** o **paralelas para** la directiva a la que el **ordenados** enlaza la construcción debe tener un **ordenados** cláusula especificada como se describe en [Sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11. En la ejecución de un **para** o **for paralelos** construir con un **ordenados** cláusula, **ordenados** construcciones se ejecutan de forma estricta en el orden en el que se ejecutaría en una ejecución secuencial del bucle.  
  
 Restricciones a la **ordenados** directiva son los siguientes:  
  
-   Una iteración de un bucle con una **para** construcción no debe ejecutar la misma directiva ordenada más de una vez y no debe ejecutar más de un **ordenados** directiva.