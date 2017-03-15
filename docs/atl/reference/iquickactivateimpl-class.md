---
title: Clase IQuickActivateImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IQuickActivateImpl
- ATL::IQuickActivateImpl<T>
- ATL.IQuickActivateImpl
- ATL.IQuickActivateImpl<T>
- IQuickActivateImpl
dev_langs:
- C++
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4f6b75da64efa12e43fa160c57da4291acae03ca
ms.lasthandoff: 02/24/2017

---
# <a name="iquickactivateimpl-class"></a>Clase IQuickActivateImpl
Esta clase combina la inicialización del control contenedor en una sola llamada.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Recupera el tamaño de presentación actual para un control de ejecución.|  
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Realiza la inicialización rápida de controles que se está cargando.|  
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informa al control de cuánto espacio tiene asignado el contenedor.|  
  
## <a name="remarks"></a>Comentarios  
 El [IQuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms690146) interfaz evita contenedores retrasos al cargar controles mediante la combinación de inicialización en una sola llamada. El `QuickActivate` método permite que el contenedor pasar un puntero a un [QACONTAINER](http://msdn.microsoft.com/library/windows/desktop/ms688630) tiene la estructura que contiene punteros a todas las interfaces del control. En la devolución, el control pase un puntero a un [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) estructura que contiene punteros a sus propias interfaces, que son utilizados por el contenedor. Clase `IQuickActivateImpl` proporciona una implementación predeterminada de **IQuickActivate** e implementa **IUnknown** mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.  
  
 **Artículos relacionados con** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IQuickActivate`  
  
 `IQuickActivateImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="a-namegetcontentextenta--iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent  
 Recupera el tamaño de presentación actual para un control de ejecución.  
  
```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Comentarios  
 El tamaño es para una representación completa del control y se especifica en unidades HIMETRIC.  
  
 Consulte [IQuickActivate::GetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms693792) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namequickactivatea--iquickactivateimplquickactivate"></a><a name="quickactivate"></a>IQuickActivateImpl::QuickActivate  
 Realiza la inicialización rápida de controles que se está cargando.  
  
```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```  
  
### <a name="remarks"></a>Comentarios  
 La estructura contiene punteros a las interfaces necesarias para el control y los valores de algunas propiedades de ambientales. Tras la devolución, el control pasa un puntero a un [QACONTROL](http://msdn.microsoft.com/library/windows/desktop/ms693721) estructura que contiene punteros a sus propias interfaces que requiere el contenedor y la información de estado adicional.  
  
 Consulte [IQuickActivate::QuickActivate](http://msdn.microsoft.com/library/windows/desktop/ms682421) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetcontentextenta--iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent  
 Informa al control de cuánto espacio tiene asignado el contenedor.  
  
```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```  
  
### <a name="remarks"></a>Comentarios  
 El tamaño se especifica en unidades HIMETRIC.  
  
 Consulte [IQuickActivate::SetContentExtent](http://msdn.microsoft.com/library/windows/desktop/ms678806) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

