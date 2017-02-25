---
title: "EventTargetArray (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::EventTargetArray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EventTargetArray (clase)"
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# EventTargetArray (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
|[Constructor Eventtargetarray](../windows/eventtargetarray-eventtargetarray-constructor.md)|Inicializa una nueva instancia de la clase EventTargetArray.|  
|[EventTargetArray:: ~ EventTargetArray (destructor)](../Topic/EventTargetArray::~EventTargetArray%20Destructor.md)|Deinitializes la clase EventTargetArray actual.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Eventtargetarray:: AddTail (método)](../windows/eventtargetarray-addtail-method.md)|El controlador de eventos especificado se anexa al final de la matriz interna de controladores de eventos.|  
|[Eventtargetarray:: begin (método)](../windows/eventtargetarray-begin-method.md)|Obtiene la dirección del primer elemento de la matriz interna de controladores de eventos.|  
|[Eventtargetarray:: end (método)](../windows/eventtargetarray-end-method.md)|Obtiene la dirección del último elemento de la matriz interna de controladores de eventos.|  
|[Eventtargetarray:: Length (método)](../windows/eventtargetarray-length-method.md)|Obtiene el número actual de elementos de la matriz interna de controladores de eventos.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `EventTargetArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** wrl  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de wrl](../windows/microsoft-wrl-details-namespace.md)