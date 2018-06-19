---
title: 2.7.2.7 copyin | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ee711bfb24e7a2a1cbada1a7e01a243e204f4a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689381"
---
# <a name="2727-copyin"></a>2.7.2.7 copyin
El **copyin** cláusula proporciona un mecanismo para asignar el mismo valor para **threadprivate** variables para cada subproceso en el equipo que ejecuta la región paralela. Para cada variable especificada en un **copyin** se copia la cláusula, el valor de la variable en el subproceso principal del equipo, como por asignación, las copias de subprocesos privados al principio de la región paralela. La sintaxis de la **copyin** cláusula es como sigue:  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 Las restricciones a la **copyin** cláusula son los siguientes:  
  
-   Una variable que se especifica en el **copyin** cláusula debe tener un operador de asignación de copia accesible y no ambigua.  
  
-   Una variable que se especifica en el **copyin** cláusula debe ser un **threadprivate** variable.