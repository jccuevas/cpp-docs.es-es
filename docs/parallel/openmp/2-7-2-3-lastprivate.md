---
title: 2.7.2.3 lastprivate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5caf9d870dce301c6055dcb55418b3dbbc3e741f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate
El `lastprivate` cláusula proporciona un superconjunto de la funcionalidad proporcionada por el `private` cláusula. La sintaxis de la `lastprivate` cláusula es como sigue:  
  
```  
lastprivate(variable-list)  
```  
  
 Las variables especificadas en el *lista de variables* tienen `private` semántica de la cláusula. Cuando un `lastprivate` cláusula aparece en la directiva que identifica una construcción de uso compartido, el valor de cada `lastprivate` variable desde la última secuencialmente iteración del bucle asociado, o la directiva de sección léxicamente última, se asigna a la objeto original de la variable. Variables que no están asignan un valor de la última iteración de la **para** o **paralelas para**, o en la sección léxicamente última de la **secciones** o  **secciones en paralelo** directiva, tienen valores indeterminados después de la construcción. Sin asignar subobjetos también tienen un valor indeterminado después de la construcción.  
  
 Las restricciones a la `lastprivate` cláusula son los siguientes:  
  
-   Todas las restricciones para `private` aplicar.  
  
-   Una variable con un tipo de clase que se especifica como `lastprivate` debe tener un operador de asignación de copia accesible y no ambigua.  
  
-   Las variables que son privadas dentro de una región paralela o que aparecen en la `reduction` cláusula de una **paralelo** directiva no se puede especificar en un `lastprivate` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.