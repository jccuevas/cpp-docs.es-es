---
title: "2.4.3 single construcción | Documentos de Microsoft"
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
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 72dc551986f149bda668c438ac5f51d01d530c51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="243-single-construct"></a>2.4.3 single (Construcción)
El **único** directiva identifica una construcción que especifica que se ejecuta el bloque estructurado asociado con un solo subproceso en el equipo (no necesariamente el subproceso principal). La sintaxis de la **único** directiva es como sigue:  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 La cláusula es uno de los siguientes:  
  
 **privada (** *lista de variables* **)**  
  
 **firstprivate (** *lista de variables* **)**  
  
 **copyprivate (** *lista de variables* **)**  
  
 **nowait**  
  
 Hay una barrera implícita después de la **único** construir a menos que un **nowait** se especifica la cláusula.  
  
 Restricciones a la **único** directiva son los siguientes:  
  
-   Solo una **nowait** cláusula puede aparecer en un **único** directiva.  
  
-   El **copyprivate** cláusula no debe usarse con el **nowait** cláusula.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **privada**, **firstprivate**, y **copyprivate** cláusulas, vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en página 25.