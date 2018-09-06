---
title: Control de resumen de eventos ATL | Microsoft Docs
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
ms.openlocfilehash: 3d5a7e97f631bfa3666da00887dce2c8ba865028
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767303"
---
# <a name="atl-event-handling-summary"></a>Resumen de control de eventos ATL

En general, el control de eventos COM es un proceso relativamente sencillo. Hay tres pasos principales:

- Implemente la interfaz de eventos en el objeto.

- Notificar al origen de eventos que su objeto quiere recibir eventos.

- No notificar el origen del evento cuando el objeto ya no necesita recibir eventos.

## <a name="implementing-the-interface"></a>Implementación de la interfaz

Hay cuatro maneras de implementar una interfaz mediante ATL.

|Derivar de|Adecuado para el tipo de interfaz|Exige que implemente todos los métodos *|Requiere una biblioteca de tipos en tiempo de ejecución|
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|
|La interfaz|Vtable|Sí|No|
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Dual|Sí|Sí|
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Interfaz dispinterface|No|Sí|
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Interfaz dispinterface|No|No|

\* Al usar clases de compatibilidad ATL, nunca son necesarios para implementar la `IUnknown` o `IDispatch` métodos manualmente.

## <a name="advising-and-unadvising-the-event-source"></a>Aconsejar y desaconsejar el origen del evento

Hay tres maneras principales de aconsejar y desaconsejar un origen de eventos mediante ATL.

|Función para aconsejar|No notificar (función)|Más adecuado para su uso con|Es preciso realizar un seguimiento de una cookie|Comentarios|
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [¡CComPtrBase:: Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable o interfaces duales|Sí|`AtlAdvise` es una función global de ATL. `CComPtrBase::Advise` se usa por [CComPtr](../atl/reference/ccomptr-class.md) y [CComQIPtr](../atl/reference/ccomqiptr-class.md).|
|[IDispEventSimpleImpl:: DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl:: DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) o [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|No|Menos parámetros que `AtlAdvise` puesto que la clase base realiza más trabajo.|
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|Controles ActiveX en controles compuestos|No|`CComCompositeControl::AdviseSinkMap` le informa de que todas las entradas de mapa de receptores de eventos. La misma función no notifica las entradas. Este método se llama de forma automática el `CComCompositeControl` clase.|
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|Controles ActiveX en un cuadro de diálogo|No|`CAxDialogImpl::AdviseSinkMap` aconseja y desaconseja todos los controles ActiveX en el recurso de cuadro de diálogo. Esto se hace automáticamente para usted.|

## <a name="see-also"></a>Vea también

[Control de eventos](../atl/event-handling-and-atl.md)   
[Admitir IDispEventImpl](../atl/supporting-idispeventimpl.md)

