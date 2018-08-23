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
ms.openlocfilehash: a13c5b48a7e242f47903fda038331fd126832dcf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592236"
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