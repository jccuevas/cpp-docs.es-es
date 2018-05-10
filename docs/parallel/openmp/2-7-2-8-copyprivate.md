---
title: 2.7.2.8 copyprivate | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c809f297da5059a98915e8055dfe23f45074366f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate
El **copyprivate** cláusula proporciona un mecanismo para utilizar una variable privada para difundir un valor de un miembro de un equipo a los demás miembros. Es una alternativa al uso de una variable compartida para el valor al proporcionar esa variable compartida sería difícil (por ejemplo, en una necesidad de una variable distinta en cada nivel de recursividad). El **copyprivate** cláusula solamente puede aparecer en el **único** directiva.  
  
 La sintaxis de la **copyprivate** cláusula es como sigue:  
  
```  
  
copyprivate(  
variable-list  
)  
  
```  
  
 El efecto de la **copyprivate** cláusula en las variables en su lista de variables se produce después de la ejecución del bloque estructurado asociado a la **único** construir y antes de cualquiera de los subprocesos en la equipo han dejado la barrera al final de la construcción. A continuación, en todos los demás subprocesos en el equipo, para cada variable en el *lista de variables*, esa variable queda definida (como si de asignación) con el valor de la correspondiente variable en el subproceso que ejecutó la construcción de la estructura bloque.  
  
 Restricciones a la **copyprivate** cláusula son los siguientes:  
  
-   Una variable que se especifica en el **copyprivate** cláusula no debe aparecer en un **privada** o **firstprivate** cláusula para el mismo **único**directiva.  
  
-   Si un **único** directiva con un **copyprivate** cláusula se encuentra en la extensión dinámica de una región paralela, todas las variables que se especifica en el **copyprivate** cláusula debe privado en el contexto envolvente.  
  
-   Una variable que se especifica en el **copyprivate** cláusula debe tener un operador de asignación de copia no ambigua accesible.