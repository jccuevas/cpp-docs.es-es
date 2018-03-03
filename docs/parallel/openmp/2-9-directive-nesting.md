---
title: 2.9 anidamiento de directivas | Documentos de Microsoft
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
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd3c4f790681b1b044f435c03d185585b565eb62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="29-directive-nesting"></a>2.9 Anidamiento de directivas
El anidamiento dinámico de directivas debe cumplir las reglas siguientes:  
  
-   A **paralelo** directiva dinámicamente dentro de otro **paralelo** lógicamente establece un nuevo equipo, que se compone del subproceso actual, a menos que anidada paralelismo está habilitado.  
  
-   **para**, **secciones**, y **único** directivas que se enlazan a la misma **paralelo** no pueden anidarse dentro de otros.  
  
-   **crítico** directivas con el mismo nombre no pueden anidarse dentro de otros. Tenga en cuenta que esta restricción no es suficiente para evitar el interbloqueo.  
  
-   **para**, **secciones**, y **único** directivas no están permitidas en la extensión dinámica de **crítico**, **ordenados**, y **maestro** regiones si las directivas se enlazan a la misma **paralelo** como las regiones.  
  
-   **barrera** directivas no están permitidas en la extensión dinámica de **para**, **ordenados**, **secciones**, **único**, **maestro**, y **crítico** regiones si las directivas se enlazan a la misma **paralelo** como las regiones.  
  
-   **maestro** directivas no están permitidas en la extensión dinámica de **para**, **secciones**, y **único** directivas si la **master** directivas enlazar al mismo **paralelo** como las directivas de uso compartido.  
  
-   **ordenados** directivas no están permitidas en la extensión dinámica de **crítico** regiones si las directivas se enlazan a la misma **paralelo** como las regiones.  
  
-   También se permite que ninguna directiva que se permite cuando se ejecuta de forma dinámica dentro de una región paralela cuando se ejecuta fuera de una región paralela. Cuando se ejecuta de forma dinámica fuera de una región paralela especificada por el usuario, se ejecuta la directiva de un equipo que se compone del subproceso principal.