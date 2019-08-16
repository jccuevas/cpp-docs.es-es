---
title: Clase IQuickActivateImpl
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
ms.openlocfilehash: 2169686ebbf756c5caf9232f5031532c62ac8265
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495515"
---
# <a name="iquickactivateimpl-class"></a>Clase IQuickActivateImpl

Esta clase combina la inicialización del control de los contenedores en una sola llamada.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IQuickActivateImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Recupera el tamaño de presentación actual para un control en ejecución.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Realiza una inicialización rápida de los controles que se están cargando.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informa al control de cuánto espacio para mostrar tiene asignado el contenedor.|

## <a name="remarks"></a>Comentarios

La interfaz [IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) ayuda a los contenedores a evitar retrasos al cargar controles mediante la combinación de la inicialización en una sola llamada. El `QuickActivate` método permite al contenedor pasar un puntero a una estructura [QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer) que contiene punteros a todas las interfaces que necesita el control. En la devolución, el control devuelve un puntero a una estructura [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) que contiene punteros a sus propias interfaces, que son usadas por el contenedor. La `IQuickActivateImpl` clase proporciona una implementación predeterminada `IQuickActivate` de e implementa `IUnknown` mediante el envío de información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="getcontentextent"></a>  IQuickActivateImpl::GetContentExtent

Recupera el tamaño de presentación actual para un control en ejecución.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Comentarios

El tamaño es para una representación completa del control y se especifica en unidades de HIMETRIC.

Vea [IQuickActivate:: GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) en el Windows SDK.

##  <a name="quickactivate"></a>  IQuickActivateImpl::QuickActivate

Realiza una inicialización rápida de los controles que se están cargando.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Comentarios

La estructura contiene punteros a las interfaces que necesita el control y los valores de algunas propiedades de ambiente. Al devolverse, el control pasa un puntero a una estructura [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) que contiene punteros a sus propias interfaces que requiere el contenedor e información de estado adicional.

Vea [IQuickActivate:: QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) en el Windows SDK.

##  <a name="setcontentextent"></a>  IQuickActivateImpl::SetContentExtent

Informa al control de cuánto espacio para mostrar tiene asignado el contenedor.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Comentarios

El tamaño se especifica en unidades de HIMETRIC.

Vea [IQuickActivate:: SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) en el Windows SDK.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
