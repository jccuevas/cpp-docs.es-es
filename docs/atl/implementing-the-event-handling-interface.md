---
title: "Implementing the Event Handling Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, control de eventos"
  - "control de eventos, ATL"
  - "interfaces, event and event sink"
ms.assetid: eb2a5b33-88dc-4ce3-bee0-c5c38ea050d7
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementing the Event Handling Interface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL ayuda con los tres elementos necesarios para administrar eventos: implementar la interfaz de eventos, aconsejando el origen de eventos, y unadvising el origen de eventos.  Los pasos exactos que necesitará realizar dependen del tipo de la interfaz de eventos y los requisitos de rendimiento de la aplicación.  
  
 Las maneras más comunes de implementar una interfaz mediante ATL son:  
  
-   Derivar de una interfaz personalizada directamente.  
  
-   Derivar de [IDispatchImpl](../atl/reference/idispatchimpl-class.md) para las interfaces duales descritas en una biblioteca de tipos.  
  
-   Derivar de [IDispEventImpl](../atl/reference/idispeventimpl-class.md) para dispinterfaces descritos en una biblioteca de tipos.  
  
-   Derivar de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) para dispinterfaces no descritos en una biblioteca de tipos o cuando se desea mejorar la eficacia no carga la información de tipo en tiempo de ejecución.  
  
 Si está implementando una interfaz personalizada o dual, debe advertir el origen de eventos llamando a [AtlAdvise](../Topic/AtlAdvise.md) o [CComPtrBase:: Advise](../Topic/CComPtrBase::Advise.md).  Necesitará hacer un seguimiento de la cookie devuelta por la llamada personalmente.  llamada [AtlUnadvise](../Topic/AtlUnadvise.md) para interrumpir la conexión.  
  
 Si está implementando una dispinterface mediante `IDispEventImpl` o `IDispEventSimpleImpl`, debe advertir el origen de eventos llamando a [IDispEventSimpleImpl:: DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md).  llamada [IDispEventSimpleImpl:: DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md) para interrumpir la conexión.  
  
 Si usa `IDispEventImpl` como clase base de un control compuesto, los orígenes de eventos enumerados en el mapa del receptor se aconsejable y sin haber recibido consejo algunos automáticamente mediante [CComCompositeControl:: AdviseSinkMap](../Topic/CComCompositeControl::AdviseSinkMap.md).  
  
 las clases de `IDispEventImpl` y de `IDispEventSimpleImpl` administran la cookie para usted.  
  
## Vea también  
 [Control de eventos](../atl/event-handling-and-atl.md)