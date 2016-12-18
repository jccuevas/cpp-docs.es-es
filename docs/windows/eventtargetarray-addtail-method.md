---
title: "EventTargetArray::AddTail (M&#233;todo) | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::EventTargetArray::AddTail"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddTail (método)"
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventTargetArray::AddTail (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
void AddTail(  
   _In_ IUnknown* element  
);  
```  
  
#### Parámetros  
 `element`  
 Puntero al controlador de eventos para anexar.  
  
## Comentarios  
 Anexa el controlador de eventos especificado al final de la matriz interno de controladores de eventos.  
  
 AddTail\(\) está diseñado para usarse internamente por sólo la clase de EventSource.  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [EventTargetArray \(Clase\)](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)