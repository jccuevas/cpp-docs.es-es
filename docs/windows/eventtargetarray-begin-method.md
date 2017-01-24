---
title: "EventTargetArray::Begin (M&#233;todo) | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::EventTargetArray::Begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Begin (método)"
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventTargetArray::Begin (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
ComPtr<IUnknown>* Begin();  
```  
  
## Valor devuelto  
 La dirección del primer elemento de la matriz interna de controladores de eventos.  
  
## Comentarios  
 Obtiene la dirección del primer elemento de la matriz interna de controladores de eventos.  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [EventTargetArray \(Clase\)](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)