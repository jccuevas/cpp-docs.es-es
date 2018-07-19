---
title: IQuickActivateImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
dev_langs:
- C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9131a1cc1f8d0c66f2eb3616f4903db74ea4bdf0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881378"
---
# <a name="iquickactivateimpl-class"></a>IQuickActivateImpl (clase)
Esta clase combina la inicialización del control de contenedores en una sola llamada.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IQuickActivateImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Recupera el tamaño de presentación actual para un control de ejecución.|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Realiza la inicialización rápida de los controles que se está cargando.|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informa al control de cuánto espacio tiene asignado el contenedor.|  
  
## <a name="remarks"></a>Comentarios  
 El [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) interfaz ayuda a evitar retrasos al cargar los controles mediante la combinación de inicialización en una sola llamada a contenedores. El `QuickActivate` método permite al contenedor pasar un puntero a un [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) necesita estructura que contiene punteros a todas las interfaces del control. Si la devolución, el control devuelve un puntero a un [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) estructura que contiene punteros a sus propias interfaces, que son utilizados por el contenedor. Clase `IQuickActivateImpl` proporciona una implementación predeterminada de `IQuickActivate` e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent  
 Recupera el tamaño de presentación actual para un control de ejecución.  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Comentarios  
 El tamaño es para una representación completa del control y se especifica en unidades HIMETRIC.  
  
 Consulte [IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) en el SDK de Windows.  
  
##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate  
 Realiza la inicialización rápida de los controles que se está cargando.  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>Comentarios  
 La estructura contiene punteros a las interfaces que son necesarias para el control y los valores de algunas propiedades de ambientales. Tras la devolución, el control pasa un puntero a un [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) estructura que contiene punteros a sus propias interfaces que requiere el contenedor y la información de estado adicionales.  
  
 Consulte [IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) en el SDK de Windows.  
  
##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent  
 Informa al control de cuánto espacio tiene asignado el contenedor.  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Comentarios  
 El tamaño se especifica en unidades HIMETRIC.  
  
 Consulte [IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [CComControl (clase)](../../atl/reference/ccomcontrol-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
