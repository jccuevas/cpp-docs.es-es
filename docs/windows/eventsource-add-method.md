---
title: "EventSource::Add (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::Add"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Add (método)"
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventSource::Add (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 La interfaz para un objeto de delegado, que representa un controlador de eventos.  
  
 `token`  
 Cuando se complete esta operación, un identificador que representa el evento. Use este token como parámetro para el [Remove()](../Topic/EventSource::Remove%20Method.md) método descartar el controlador de eventos.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)