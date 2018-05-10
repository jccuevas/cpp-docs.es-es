---
title: 'EventSource:: Add (método) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Add
dev_langs:
- C++
helpviewer_keywords:
- Add method
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 92af8746b4d2b5ba2f379cc8660b5345b2c5f175
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="eventsourceadd-method"></a>EventSource::Add (Método)
Anexa el controlador del evento representado por la interfaz de delegado especificado para el conjunto de controladores de eventos para el objeto de origen de eventos actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `delegateInterface`  
 La interfaz a un objeto de delegado, que representa un controlador de eventos.  
  
 `token`  
 Cuando se completa esta operación, un identificador que representa el evento. Usar este token como parámetro a la [Remove()](../windows/eventsource-remove-method.md) método para descartar el controlador de eventos.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)