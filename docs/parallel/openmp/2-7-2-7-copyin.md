---
title: 2.7.2.7 copyin | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd296192146e76085e1b987e29a377eb621917ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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