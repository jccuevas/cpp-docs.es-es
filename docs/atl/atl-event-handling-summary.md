---
title: Control de resumen de eventos ATL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a938bd072ea8df30e64cce28fbf0709f08547d28
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356528"
---
# <a name="atl-event-handling-summary"></a>Resumen de control de eventos ATL
En general, el control de eventos COM es un proceso relativamente sencillo. Hay tres pasos principales:  
  
-   Implemente la interfaz de eventos en el objeto.  
  
-   Notificar al origen de eventos que su objeto quiere recibir eventos.  
  
-   No notificar el origen del evento cuando el objeto ya no se necesita recibir eventos.  
  
## <a name="implementing-the-interface"></a>Implementación de la interfaz  
 Hay cuatro maneras de implementar una interfaz utilizando ATL.  
  
|Derivar de|Adecuado para el tipo de interfaz|Debe implementar todos los métodos *|Requiere una biblioteca de tipos en tiempo de ejecución|  
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|  
|La interfaz|Vtable|Sí|No|  
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Doble|Sí|Sí|  
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Dispinterface|No|Sí|  
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Dispinterface|No|No|  
  
 \* Al utilizar las clases de compatibilidad con ATL, nunca necesarias para implementar la **IUnknown** o `IDispatch` métodos manualmente.  
  
## <a name="advising-and-unadvising-the-event-source"></a>Aconsejar y desaconsejar el origen del evento  
 Hay tres maneras principales de aconsejar y desaconsejar un origen de eventos con ATL.  
  
|Función para aconsejar|Función para desaconsejar.|Más adecuado para su uso con|Debe realizar un seguimiento de una cookie|Comentarios|  
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|  

|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [¡CComPtrBase:: Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)| Vtable o interfaces duales | Sí | `AtlAdvise` es una función ATL global. `CComPtrBase::Advise` se utiliza por [CComPtr](../atl/reference/ccomptr-class.md) y [CComQIPtr](../atl/reference/ccomqiptr-class.md). |  

|[IDispEventSimpleImpl:: DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl:: DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) o [ IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)| Ya no | Menos parámetros que `AtlAdvise` desde la clase base realiza más trabajo. |  
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)| Controles ActiveX en controles compuestos | Ya no | `CComCompositeControl::AdviseSinkMap` aconseja todas las entradas del mapa de receptores de eventos. La misma función desaconseja las entradas. Este método se llama de forma automática la `CComCompositeControl` clase. |  
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)| Controles ActiveX en un cuadro de diálogo | Ya no | `CAxDialogImpl::AdviseSinkMap` aconseja y desaconseja todos los controles ActiveX en el recurso de cuadro de diálogo. Esto se hace automáticamente para usted. |  
  
## <a name="see-also"></a>Vea también  
 [Control de eventos](../atl/event-handling-and-atl.md)   
 [Admitir IDispEventImpl](../atl/supporting-idispeventimpl.md)

