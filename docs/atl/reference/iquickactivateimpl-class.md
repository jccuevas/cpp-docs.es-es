---
title: IQuickActivateImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl
- ATLCTL/ATL::IQuickActivateImpl::GetContentExtent
- ATLCTL/ATL::IQuickActivateImpl::QuickActivate
- ATLCTL/ATL::IQuickActivateImpl::SetContentExtent
helpviewer_keywords:
- activating ATL controls
- controls [ATL], activating
- IQuickActivateImpl class
- IQuickActivate ATL implementation
ms.assetid: aa80c056-1041-494e-b21d-2acca7dc27ea
ms.openlocfilehash: 2a2b11746249b6ee4f6ddd578717aacc374d53bc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265254"
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

*T*<br/>
La clase derivada de `IQuickActivateImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Recupera el tamaño de presentación actual para un control de ejecución.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Realiza la inicialización rápida de los controles que se está cargando.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informa al control de cuánto espacio tiene asignado el contenedor.|

## <a name="remarks"></a>Comentarios

El [IQuickActivate](/windows/desktop/api/ocidl/nn-ocidl-iquickactivate) interfaz ayuda a evitar retrasos al cargar los controles mediante la combinación de inicialización en una sola llamada a contenedores. El `QuickActivate` método permite al contenedor pasar un puntero a un [QACONTAINER](/windows/desktop/api/ocidl/ns-ocidl-tagqacontainer) necesita estructura que contiene punteros a todas las interfaces del control. Si la devolución, el control devuelve un puntero a un [QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol) estructura que contiene punteros a sus propias interfaces, que son utilizados por el contenedor. Clase `IQuickActivateImpl` proporciona una implementación predeterminada de `IQuickActivate` e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

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

Consulte [IQuickActivate::GetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) en el SDK de Windows.

##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate

Realiza la inicialización rápida de los controles que se está cargando.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Comentarios

La estructura contiene punteros a las interfaces que son necesarias para el control y los valores de algunas propiedades de ambientales. Tras la devolución, el control pasa un puntero a un [QACONTROL](/windows/desktop/api/ocidl/ns-ocidl-tagqacontrol) estructura que contiene punteros a sus propias interfaces que requiere el contenedor y la información de estado adicionales.

Consulte [IQuickActivate::QuickActivate](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-quickactivate) en el SDK de Windows.

##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent

Informa al control de cuánto espacio tiene asignado el contenedor.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Comentarios

El tamaño se especifica en unidades HIMETRIC.

Consulte [IQuickActivate::SetContentExtent](/windows/desktop/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
