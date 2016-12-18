---
title: "EventSource (Clase) | Microsoft Docs"
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
  - "event/Microsoft::WRL::EventSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EventSource (clase)"
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventSource (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un evento.  Las funciones miembro de EventSource agregan, quitan, y los controladores de eventos.  
  
## Sintaxis  
  
```  
template<  
   typename TDelegateInterface  
>  
class EventSource;  
```  
  
#### Parámetros  
 `TDelegateInterface`  
 La interfaz un delegado que representa un controlador de eventos.  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventSource::EventSource \(Constructor\)](../windows/eventsource-eventsource-constructor.md)|Inicializa una nueva instancia de la clase de EventSource.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventSource::Add \(Método\)](../windows/eventsource-add-method.md)|Anexa el controlador de eventos representado por la interfaz especificada del delegado al conjunto de controladores de eventos para el objeto actual de EventSource.|  
|[EventSource::GetSize \(Método\)](../windows/eventsource-getsize-method.md)|Recupera el número de controladores de eventos asociados al objeto actual de EventSource|  
|[EventSource::InvokeAll \(Método\)](../windows/eventsource-invokeall-method.md)|Llama a cada controlador de eventos asociado al objeto actual de EventSource utilizando los tipos y los argumentos especificados del argumento.|  
|[EventSource::Remove \(Método\)](../Topic/EventSource::Remove%20Method.md)|Elimina el controlador de eventos representado por el símbolo especificado de registro de eventos del conjunto de controladores de eventos asociados al objeto actual de EventSource.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[EventSource::addRemoveLock\_ \(Miembro de datos\)](../windows/eventsource-addremovelock-data-member.md)|Sincronizar el acceso a la matriz de [targets\_](../Topic/EventSource::targets_%20Data%20Member.md) al agregar, quitar, o invocando a los controladores de eventos.|  
|[EventSource::targets\_ \(Miembro de datos\)](../Topic/EventSource::targets_%20Data%20Member.md)|Una matriz de uno o más controladores de eventos.|  
|[EventSource::targetsPointerLock\_ \(Miembro de datos\)](../windows/eventsource-targetspointerlock-data-member.md)|Sincroniza el acceso a los miembros de datos internos mientras están agregando, se están quitando, o se invocan los controladores de eventos para este EventSource.|  
  
## Jerarquía de herencia  
 `EventSource`  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)