---
title: Clase IQuickActivateImpl | Documentos de Microsoft
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
ms.openlocfilehash: b87427408483a60cf33b46a1a670095d211b3d80
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362809"
---
# <a name="iquickactivateimpl-class"></a>Clase IQuickActivateImpl
Esta clase combina la inicialización del control de contenedores en una única llamada.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IQuickActivateImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Recupera el tamaño de presentación actual para un control que se ejecuta.|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Realiza la inicialización rápida de controles que se va a cargar.|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informa al control de cuánto espacio de visualización tiene asignado el contenedor.|  
  
## <a name="remarks"></a>Comentarios  
 El [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) interfaz evita contenedores retrasos al cargar los controles mediante la combinación de inicialización en una sola llamada. El `QuickActivate` método permite al contenedor pasar un puntero a un [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) necesita estructura que contiene punteros a todas las interfaces del control. Una vez devuelta, el control pase un puntero a un [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) estructura que contiene punteros a sus propias interfaces, que son utilizados por el contenedor. Clase `IQuickActivateImpl` proporciona una implementación predeterminada de **IQuickActivate** e implementa **IUnknown** mediante el envío de información para el volcado de memoria compilaciones dispositivo en versiones de depuración.  
  
 **Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent  
 Recupera el tamaño de presentación actual para un control que se ejecuta.  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Comentarios  
 El tamaño es en una representación completa del control y se especifica en unidades HIMETRIC.  
  
 Vea [IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) en el SDK de Windows.  
  
##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate  
 Realiza la inicialización rápida de controles que se va a cargar.  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>Comentarios  
 La estructura contiene punteros a las interfaces que son necesarias para el control y los valores de algunas propiedades de ambiente. Al volver, el control pasa un puntero a un [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) estructura que contiene punteros a sus propias interfaces de que el contenedor requiere e información de estado adicionales.  
  
 Vea [IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) en el SDK de Windows.  
  
##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent  
 Informa al control de cuánto espacio de visualización tiene asignado el contenedor.  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Comentarios  
 El tamaño se especifica en unidades HIMETRIC.  
  
 Vea [IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
