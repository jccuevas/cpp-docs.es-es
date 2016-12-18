---
title: "EventTargetArray::End (M&#233;todo) | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::EventTargetArray::End"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "End (método)"
ms.assetid: 20c491b8-f355-4d8f-ad14-8f46121d9af6
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventTargetArray::End (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
ComPtr<IUnknown>* End();  
```  
  
## Valor devuelto  
 La dirección del último elemento de la matriz interno de controladores de eventos.  
  
## Comentarios  
 Obtiene la dirección del último elemento de la matriz interno de controladores de eventos.  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [EventTargetArray \(Clase\)](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)