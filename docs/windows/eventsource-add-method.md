---
title: Método EventSource | Microsoft Docs
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
ms.openlocfilehash: 65e8576f069cce7d7aec2eae18ad577820ca93a4
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644747"
---
# <a name="eventsourceadd-method"></a>EventSource::Add (Método)
Anexa el controlador del evento representado por la interfaz de delegado especificado al conjunto de controladores de eventos actual **EventSource** objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 *delegateInterface*  
 La interfaz para un objeto delegado, que representa un controlador de eventos.  
  
 *símbolo (token)*  
 Cuando se completa esta operación, un identificador que representa el evento. Use este token como parámetro para el [Remove()](../windows/eventsource-remove-method.md) método para descartar el controlador de eventos.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)