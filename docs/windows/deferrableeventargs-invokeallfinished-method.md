---
title: "M&#233;todo DeferrableEventArgs::InvokeAllFinished | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# M&#233;todo DeferrableEventArgs::InvokeAllFinished
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se llama para indicar que se ha completado todo el procesamiento para controlar un evento diferido.  
  
## Sintaxis  
  
```cpp  
void InvokeAllFinished()  
```  
  
## Comentarios  
 Debe llamar a este método después de que el origen del evento llame a [InvokeAll](../windows/eventsource-invokeall-method.md).  Llamar a este método evita que se realicen futuros aplazamientos y obliga al controlador de finalización a ejecutarse si no se realizaron aplazamientos.  
  
 Para ver un ejemplo de código, vea [Clase DeferrableEventArgs](../windows/deferrableeventargs-class.md).  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Clase DeferrableEventArgs](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll \(Método\)](../windows/eventsource-invokeall-method.md)