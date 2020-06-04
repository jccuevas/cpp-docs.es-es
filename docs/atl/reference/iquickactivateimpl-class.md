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
ms.openlocfilehash: 7e1984249caf66e2986341f9c9f7a939d7039125
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329551"
---
# <a name="iquickactivateimpl-class"></a>Clase IQuickActivateImpl

Esta clase combina la inicialización del control de contenedores en una sola llamada.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IQuickActivateImpl : public IQuickActivate
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IQuickActivateImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IQuickActivateImpl::GetContentExtent](#getcontentextent)|Recupera el tamaño de visualización actual de un control en ejecución.|
|[IQuickActivateImpl::QuickActivate](#quickactivate)|Realiza una inicialización rápida de los controles que se están cargando.|
|[IQuickActivateImpl::SetContentExtent](#setcontentextent)|Informa al control de cuánto espacio de visualización le ha asignado el contenedor.|

## <a name="remarks"></a>Observaciones

La interfaz [IQuickActivate](/windows/win32/api/ocidl/nn-ocidl-iquickactivate) ayuda a los contenedores a evitar retrasos al cargar controles combinando la inicialización en una sola llamada. El `QuickActivate` método permite que el contenedor pase un puntero a una estructura [QACONTAINER](/windows/win32/api/ocidl/ns-ocidl-qacontainer) que contiene punteros a todas las interfaces que necesita el control. Al volver, el control devuelve un puntero a una estructura [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) que contiene punteros a sus propias interfaces, que se usan en el contenedor. Clase `IQuickActivateImpl` proporciona una `IQuickActivate` implementación `IUnknown` predeterminada e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IQuickActivate`

`IQuickActivateImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="iquickactivateimplgetcontentextent"></a><a name="getcontentextent"></a>IQuickActivateImpl::GetContentExtent

Recupera el tamaño de visualización actual de un control en ejecución.

```
STDMETHOD(GetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Observaciones

El tamaño es para una representación completa del control y se especifica en unidades HIMETRIC.

Consulte [IQuickActivate::GetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-getcontentextent) en el Windows SDK.

## <a name="iquickactivateimplquickactivate"></a><a name="quickactivate"></a>IQuickActivateImpl::QuickActivate

Realiza una inicialización rápida de los controles que se están cargando.

```
STDMETHOD(QuickActivate)(
    QACONTAINER* pQACont,
    QACONTROL* pQACtrl);
```

### <a name="remarks"></a>Observaciones

La estructura contiene punteros a las interfaces necesarias para el control y los valores de algunas propiedades ambientales. Al volver, el control pasa un puntero a una estructura [QACONTROL](/windows/win32/api/ocidl/ns-ocidl-qacontrol) que contiene punteros a sus propias interfaces que requiere el contenedor e información de estado adicional.

Consulte [IQuickActivate::QuickActivate](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-quickactivate) en el Windows SDK.

## <a name="iquickactivateimplsetcontentextent"></a><a name="setcontentextent"></a>IQuickActivateImpl::SetContentExtent

Informa al control de cuánto espacio de visualización le ha asignado el contenedor.

```
STDMETHOD(SetContentExtent)(LPSIZEL pSize);
```

### <a name="remarks"></a>Observaciones

El tamaño se especifica en unidades HIMETRIC.

Consulte [IQuickActivate::SetContentExtent](/windows/win32/api/ocidl/nf-ocidl-iquickactivate-setcontentextent) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
