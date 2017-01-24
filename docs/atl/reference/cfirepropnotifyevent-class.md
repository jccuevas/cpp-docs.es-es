---
title: "CFirePropNotifyEvent Class | Microsoft Docs"
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
  - "CFirePropNotifyEvent"
  - "ATL::CFirePropNotifyEvent"
  - "ATL.CFirePropNotifyEvent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFirePropNotifyEvent class"
  - "puntos de conexión [C++], notifying of events"
  - "sinks, notifying of ATL events"
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFirePropNotifyEvent Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para notificar al receptor de contenedor con relación a los cambios de la propiedad del control.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CFirePropNotifyEvent  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](../Topic/CFirePropNotifyEvent::FireOnChanged.md)|\(Estático\) Notifies el receptor de contenedor que una propiedad de control ha cambiado.|  
|[CFirePropNotifyEvent::FireOnRequestEdit](../Topic/CFirePropNotifyEvent::FireOnRequestEdit.md)|\(Estático\) Notifies el receptor de contenedor que una propiedad de control va a cambiar.|  
  
## Comentarios  
 `CFirePropNotifyEvent` tiene dos métodos que notifica al receptor de contenedor que una propiedad de control ha cambiado o va a cambiar.  
  
 Si la clase que implementa el control es derivada de `IPropertyNotifySink`, se invocan los métodos de `CFirePropNotifyEvent` cuando se llama a `FireOnRequestEdit` o `FireOnChanged`.  Si la clase de control no es derivada de `IPropertyNotifySink`, las llamadas a estas funciones `S_OK`return.  
  
 Para obtener más información sobre cómo crear controles, vea [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)