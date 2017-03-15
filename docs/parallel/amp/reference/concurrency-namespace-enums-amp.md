---
title: Enumeraciones del espacio de nombres de simultaneidad (AMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c87457e-184f-4992-81ab-ca75e7d524ab
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: b9555023e01cb765ca943fcaaf785cdc2b4e2d0d
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-enums-amp"></a>Enumeraciones del espacio de nombres de simultaneidad (AMP)
|||  
|-|-|  
|[access_type (enumeración)](#access_type)|[queuing_mode (enumeración)](#queuing_mode)|  
  
##  <a name="a-nameaccesstypea--accesstype-enumeration"></a><a name="access_type"></a>access_type (enumeración)  
 Tipo de enumeración se usa para denotar los distintos tipos de acceso a datos.  
  
```  
enum access_type;  
```  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`access_type_auto`|Elige automáticamente la mejor `access_type` para el acelerador.|  
|`access_type_none`|Dedicado. La asignación solo es accesible en el acelerador y no en la CPU.|  
|`access_type_read`|Compartir. La asignación es accesible en el acelerador y es legible en la CPU.|  
|`access_type_read_write`|Compartir. La asignación es accesible en el acelerador y admite la escritura en la CPU.|  
|`access_type_write`|Compartir. La asignación es accesible en el acelerador y es de lectura y escritura en la CPU.|  

  
##  <a name="a-namequeuingmodea--queuingmode-enumeration"></a><a name="queuing_mode"></a>queuing_mode (enumeración)  
 Especifica los modos de la puesta en cola que se admiten en el acelerador.  
  
```  
enum queuing_mode;  
``` 
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`queuing_mode_immediate`|Por ejemplo, si el modo de cola especifica que cualquier comandos [parallel_for_each (función) (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each), se envían al dispositivo acelerador correspondiente en cuanto se devuelven al llamador.|  
|`queuing_mode_automatic`|Un modo de cola que especifica que comandos pondrán en cola en una cola de comando que corresponde a la [accelerator_view](accelerator-view-class.md) objeto. Comandos que se envían al dispositivo cuando [accelerator_view:: Flush](accelerator-view-class.md#flush) se llama.|   
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

