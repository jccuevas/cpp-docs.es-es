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
ms.openlocfilehash: 9dd026158a2bbc76e7a3e195bc5346f65821f2b7
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569500"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove (Método)
Elimina el controlador del evento representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados con el actual **EventSource** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 Para obtener más información acerca de la estructura EventRegistrationToken, consulte el `Windows::Foundation::EventRegistrationToken` tema de la estructura en la documentación de referencia de Windows en tiempo de ejecución.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)