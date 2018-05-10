---
title: Enumeraciones de espacio de nombres de simultaneidad (AMP) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- amp/Concurrency::access_type
- amp/Concurrency::queuing_mode
dev_langs:
- C++
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a67b5e77b8ab8c52e55dea96e64a3f16a4d70e39
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="concurrency-namespace-enums-amp"></a>Enumeraciones de espacio de nombres de simultaneidad (AMP)
|||  
|-|-|  
|[access_type (enumeración)](#access_type)|[queuing_mode (enumeración)](#queuing_mode)|  
  
##  <a name="access_type"></a>  access_type (enumeración)  
 Tipo de enumeración se usa para denotar los distintos tipos de acceso a datos.  
  
```  
enum access_type;  
```  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`access_type_auto`|Seleccionar automáticamente el mejor `access_type` para el acelerador.|  
|`access_type_none`|Dedicado. La asignación solo es accesible en el acelerador y no en la CPU.|  
|`access_type_read`|Compartir. La asignación es accesible en el acelerador y se puede leer en la CPU.|  
|`access_type_read_write`|Compartir. La asignación es accesible en el acelerador y es grabable en la CPU.|  
|`access_type_write`|Compartir. La asignación es accesible en el acelerador y es de lectura y escritura en la CPU.|  

  
##  <a name="queuing_mode"></a>  queuing_mode (enumeración)  
 Especifica los modos de la puesta en cola que se admiten en el acelerador.  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`queuing_mode_immediate`|Por ejemplo, un modo de puesta en cola que especifica que cualquier comandos [parallel_for_each (función) (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), se envían al dispositivo acelerador correspondiente en cuanto se devuelven al llamador.|  
|`queuing_mode_automatic`|Un modo de puesta en cola que especifica que comandos pondrán en cola en una cola de comando que corresponde a la [accelerator_view](accelerator-view-class.md) objeto. Comandos se envían al dispositivo cuando [accelerator_view:: Flush](accelerator-view-class.md#flush) se llama.|   
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
