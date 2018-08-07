---
title: EventTargetArray (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2757589509e4a2b091c5057ef2065866a8829494
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570426"
---
# <a name="eventtargetarray-class"></a>EventTargetArray (Clase)
Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>Comentarios  
 Representa una matriz de controladores de eventos.  
  
 Los controladores de eventos que están asociados con un [EventSource](../windows/eventsource-class.md) objeto se almacenan en un protegido **EventTargetArray** miembro de datos.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventTargetArray::EventTargetArray (constructor)](../windows/eventtargetarray-eventtargetarray-constructor.md)|Inicializa una nueva instancia de la **EventTargetArray** clase.|  
|[EventTargetArray::~EventTargetArray (destructor)](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|Desinicializa actual **EventTargetArray** clase.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventTargetArray::AddTail (método)](../windows/eventtargetarray-addtail-method.md)|El controlador de eventos especificado se anexa al final de la matriz interna de controladores de eventos.|  
|[EventTargetArray::Begin (método)](../windows/eventtargetarray-begin-method.md)|Obtiene la dirección del primer elemento de la matriz interna de controladores de eventos.|  
|[EventTargetArray::End (método)](../windows/eventtargetarray-end-method.md)|Obtiene la dirección del último elemento de la matriz interna de controladores de eventos.|  
|[EventTargetArray::Length (método)](../windows/eventtargetarray-length-method.md)|Obtiene el número actual de elementos de la matriz interna de controladores de eventos.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `EventTargetArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Namespace:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)