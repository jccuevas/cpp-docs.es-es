---
title: Especificar el modelo de subprocesamiento de un proyecto (ATL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f807aa82a62fb703430ace5bc6be516e08ca9dc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359641"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>Especificar el modelo de subprocesos de un proyecto (ATL)
Las macros siguientes están disponibles para especificar el modelo de subprocesos de un proyecto ATL:  
  
|Macro|Directrices para usar|  
|-----------|--------------------------|  
|_ATL_SINGLE_THREADED|Define si todos los objetos utilizan el modelo de subprocesamiento único.|  
|_ATL_APARTMENT_THREADED|Define si uno o varios de los objetos utilizan el apartamento de subproceso.|  
|_ATL_FREE_THREADED|Define si uno o varios de los objetos utilizan el subprocesamiento libre o neutral. El código existente puede contener referencias a la macro equivalente [_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded).|  
  
 Si no se define ninguna de estas macros para el proyecto, _ATL_FREE_THREADED estará en vigor.  
  
 Las macros afectan al rendimiento de tiempo de ejecución como se indica a continuación:  
  
-   Especificación de la macro que corresponde a los objetos del proyecto puede mejorar el rendimiento de tiempo de ejecución.  
  
-   Especificar un nivel más alto de la macro, por ejemplo, si se especifica _ATL_APARTMENT_THREADED cuando todos los objetos tienen un únicos subproceso, degradará ligeramente el rendimiento en tiempo de ejecución.  
  
-   Especificar un nivel inferior de la macro, por ejemplo, si especifica _ATL_SINGLE_THREADED cuando uno o varios de los objetos usar apartamento de subproceso o subprocesamiento libre, puede hacer que la aplicación genere un error en tiempo de ejecución.  
  
 Vea [opciones, Asistente para objetos simples de ATL](../atl/reference/options-atl-simple-object-wizard.md) para obtener una descripción de los subprocesos los modelos disponibles para un objeto ATL.  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)

