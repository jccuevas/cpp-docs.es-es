---
title: 2.7.2.2 firstprivate | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b8e44ca52ba1f76d5b3791a1d08301bf06e7eab
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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