---
title: 2.7.2.8 copyprivate | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 21d739fb3ead0512776cfd996b59f1ceab5e8250
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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