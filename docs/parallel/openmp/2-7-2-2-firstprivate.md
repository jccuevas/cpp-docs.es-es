---
title: 2.7.2.2 firstprivate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e4f73b3cb418204008fda9962cf67797c8182f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="2722-firstprivate"></a>2.7.2.2 firstprivate
El **firstprivate** cláusula proporciona un superconjunto de la funcionalidad proporcionada por el **privada** cláusula. La sintaxis de la **firstprivate** cláusula es como sigue:  
  
```  
firstprivate(variable-list)  
```  
  
 Las variables especificadas en *lista de variables* tienen **privada** semántica de cláusula, como se describe en [sección 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) en página 25. Se produce la inicialización o construcción como si se realiza una vez por subproceso, antes de la ejecución del subproceso de la construcción. Para una **firstprivate** cláusula en una construcción paralela, el valor inicial del nuevo objeto privado es el valor del objeto original que existe inmediatamente antes de la construcción paralela para el subproceso que lo detecta. Para una **firstprivate** cláusula en una construcción de uso compartido, el valor inicial del nuevo objeto privado para cada subproceso que ejecuta la construcción de uso compartido es el valor del objeto original que existe anterior al punto en el tiempo que el mismo subproceso encuentra la construcción de uso compartido. Además, para los objetos de C++, el nuevo objeto privado para cada subproceso es han creado a partir del objeto original.  
  
 Las restricciones a la **firstprivate** cláusula son los siguientes:  
  
-   Una variable especificada en un **firstprivate** cláusula no debe tener un tipo incompleto ni un tipo de referencia.  
  
-   Una variable con un tipo de clase que se especifica como **firstprivate** debe tener un constructor de copias sea accesible y no ambigua.  
  
-   Las variables que son privadas dentro de una región paralela o que aparecen en la **reducción** cláusula de un **paralelo** directiva no se puede especificar en un **firstprivate** cláusula en una Directiva de uso compartido que se enlaza a la construcción paralela.