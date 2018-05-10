---
title: 2.4.3 single construcción | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db3f9ca834fb3f35c95732698fd02e16f31b4225
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="243-single-construct"></a>2.4.3 single (Construcción)
El **único** directiva identifica una construcción que especifica que se ejecuta el bloque estructurado asociado con un solo subproceso en el equipo (no necesariamente el subproceso principal). La sintaxis de la **único** directiva es como sigue:  
  
```  
#pragma omp single [clause[[,] clause] ...] new-linestructured-block  
```  
  
 La cláusula es uno de los siguientes:  
  
 **private(** *variable-list* **)**  
  
 **firstprivate(** *variable-list* **)**  
  
 **copyprivate (** *lista de variables* **)**  
  
 **nowait**  
  
 Hay una barrera implícita después de la **único** construir a menos que un **nowait** se especifica la cláusula.  
  
 Restricciones a la **único** directiva son los siguientes:  
  
-   Solo una **nowait** cláusula puede aparecer en un **único** directiva.  
  
-   El **copyprivate** cláusula no debe usarse con el **nowait** cláusula.  
  
## <a name="cross-references"></a>Referencias cruzadas:  
  
-   **privada**, **firstprivate**, y **copyprivate** cláusulas, vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en página 25.