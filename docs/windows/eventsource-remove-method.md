---
title: Método EventSource | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 36a057bbad39e61576828c5a02f6863248b235cf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641410"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove (Método)
Elimina el controlador del evento representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados con el actual **EventSource** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *símbolo (token)*  
 Un identificador que representa un controlador de eventos. Este token se devolvió cuando se registró el controlador de eventos por la [Add()](../windows/eventsource-add-method.md) método.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la `EventRegistrationToken` estructura, vea el **Windows::Foundation::EventRegistrationToken estructura** tema en el **en tiempo de ejecución de Windows** documentación de referencia.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)