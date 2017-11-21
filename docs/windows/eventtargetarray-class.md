---
title: EventTargetArray (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::EventTargetArray
dev_langs: C++
helpviewer_keywords: EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b7f23265601411c0a1913b1e06b9fffa62bfa07f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="eventtargetarray-class"></a>EventTargetArray (Clase)
Admite la infraestructura WRL y no está diseñada para utilizarse directamente desde el código.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>Comentarios  
 Representa una matriz de controladores de eventos.  
  
 Los controladores de eventos que están asociados a un [EventSource](../windows/eventsource-class.md) objeto se almacenan en un miembro de datos EventTargetArray protegido.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[EventTargetArray::EventTargetArray (constructor)](../windows/eventtargetarray-eventtargetarray-constructor.md)|Inicializa una nueva instancia de la clase EventTargetArray.|  
|[EventTargetArray::~EventTargetArray (destructor)](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|Desinicializa la EventTargetArray (clase) actual.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
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