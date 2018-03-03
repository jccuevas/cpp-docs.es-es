---
title: 2.7.2.7 copyin | Documentos de Microsoft
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
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ba09b70b3a3591b1f8b427ac107576cfcac7935
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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