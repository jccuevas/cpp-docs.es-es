---
title: "EventSource:: Remove (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::Remove
dev_langs: C++
helpviewer_keywords: Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c1879c939237275c279e1dd4bd1861ab3b02b468
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="eventsourceremove-method"></a>EventSource::Remove (Método)
Elimina el controlador de eventos representado por el token de registro de eventos especificado del conjunto de controladores de eventos asociados con el objeto de origen de eventos actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `token`  
 Un identificador que representa un controlador de eventos. Este token se devolvió cuando se registró el controlador de eventos por la [Add()](../windows/eventsource-add-method.md) método.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de la estructura EventRegistrationToken, vea el tema de la estructura de Windows::Foundation::EventRegistrationToken en la documentación de referencia en tiempo de ejecución de Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)