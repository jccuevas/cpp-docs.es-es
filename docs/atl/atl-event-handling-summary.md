---
title: "ATL Event Handling Summary | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de eventos, implementar"
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ATL Event Handling Summary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Normalmente administrar eventos COM es un proceso relativamente simple.  hay tres pasos principales:  
  
-   Implemente la interfaz de evento en el objeto.  
  
-   Advise el origen de eventos que el objeto desee recibir eventos.  
  
-   Unadvise el origen de eventos cuando el objeto ya no necesita recibir eventos.  
  
## implementar la interfaz  
 Hay cuatro formas principales de implementar una interfaz mediante ATL.  
  
|Derivar de|Adecuado para el tipo de interfaz|Requiere implementar todo el methods\*|Requiere una biblioteca de tipos en tiempo de ejecución|  
|----------------|---------------------------------------|--------------------------------------------|-------------------------------------------------------------|  
|la interfaz|Vtable|Sí|No|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Doble|Sí|Sí|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|No|Sí|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|No|No|  
  
 \* Al utilizar clases de soporte de ATL, le nunca que implementar los métodos de **IUnknown** o de `IDispatch` manualmente.  
  
## El muestran y Unadvising el origen del evento  
 Existen tres formas principales de advertir y de unadvising un origen de eventos mediante ATL.  
  
|Advise la función|función de Unadvise|El más adecuado para el uso con|¿Necesita hacer un seguimiento de una cookie?|Comentarios|  
|-----------------------|-------------------------|-------------------------------------|---------------------------------------------------|-----------------|  
|[AtlAdvise](../Topic/AtlAdvise.md), [CComPtrBase:: Advise](../Topic/CComPtrBase::Advise.md)|[AtlUnadvise](../Topic/AtlUnadvise.md)|Vtable o interfaces duales|Sí|`AtlAdvise` es una función global de ATL.  `CComPtrBase::Advise` es utilizado por [CComPtr](../atl/reference/ccomptr-class.md) y [CComQIPtr](../atl/reference/ccomqiptr-class.md).|  
|[IDispEventSimpleImpl:: DispEventAdvise](../Topic/IDispEventSimpleImpl::DispEventAdvise.md)|[IDispEventSimpleImpl:: DispEventUnadvise](../Topic/IDispEventSimpleImpl::DispEventUnadvise.md)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) o [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|No|Menos parámetros que `AtlAdvise` desde la clase base hace más trabajo.|  
|[CComCompositeControl:: AdviseSinkMap \(TRUE\)](../Topic/CComCompositeControl::AdviseSinkMap.md)|[CComCompositeControl:: AdviseSinkMap \(FALSE\)](../Topic/CComCompositeControl::AdviseSinkMap.md)|Controles ActiveX en controles de Compuesto|No|`CComCompositeControl::AdviseSinkMap` indica todas las entradas del mapa de receptor de eventos.  Igual unadvises de función entradas.  Este método llama automáticamente la clase de `CComCompositeControl` .|  
|[CAxDialogImpl:: AdviseSinkMap \(TRUE\)](../Topic/CAxDialogImpl::AdviseSinkMap.md)|[CAxDialogImpl:: AdviseSinkMap \(FALSE\)](../Topic/CAxDialogImpl::AdviseSinkMap.md)|Controles ActiveX en un cuadro de diálogo|No|`CAxDialogImpl::AdviseSinkMap` aconseja y los unadvises todos los controles ActiveX en el recurso de cuadro de diálogo.  Esto se hace automáticamente para usted.|  
  
## Vea también  
 [Control de eventos](../atl/event-handling-and-atl.md)   
 [Supporting IDispEventImpl](../atl/supporting-idispeventimpl.md)