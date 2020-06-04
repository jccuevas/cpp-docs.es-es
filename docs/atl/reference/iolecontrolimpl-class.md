---
title: Clase IOleControlImpl
ms.date: 11/04/2016
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
ms.openlocfilehash: 947ec16e91b99cc42cff90abe7df4a5d13576e98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329621"
---
# <a name="iolecontrolimpl-class"></a>Clase IOleControlImpl

Esta clase proporciona una `IOleControl` implementación predeterminada `IUnknown`de la interfaz e implementa .

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IOleControlImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indica si el contenedor omite o acepta eventos del control.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Rellena información sobre el comportamiento del teclado del control. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informa a un control de que una o varias de las propiedades ambientales del contenedor han cambiado. La implementación de ATL devuelve S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informa al control de que un usuario ha presionado una pulsación de tecla especificada. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Observaciones

Clase `IOleControlImpl` proporciona una implementación predeterminada de la `IUnknown` [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) interfaz e implementa mediante el envío de información al dispositivo de volcado en compilaciones de depuración.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="iolecontrolimplfreezeevents"></a><a name="freezeevents"></a>IOleControlImpl::FreezeEvents

En la implementación `FreezeEvents` de ATL, incrementa `m_nFreezeEvents` el miembro de datos de la clase de control `bFreeze` si es TRUE y disminuye `m_nFreezeEvents` si `bFreeze` es FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Observaciones

`FreezeEvents`luego devuelve S_OK.

Consulte [IOleControl::FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) en el Windows SDK.

## <a name="iolecontrolimplgetcontrolinfo"></a><a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo

Rellena información sobre el comportamiento del teclado del control.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Observaciones

Consulte [IOleControl:GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

## <a name="iolecontrolimplonambientpropertychange"></a><a name="onambientpropertychange"></a>IOleControlImpl::OnAmbientPropertyChange

Informa a un control de que una o varias de las propiedades ambientales del contenedor han cambiado.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Vea [IOleControl::OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) en el Windows SDK.

## <a name="iolecontrolimplonmnemonic"></a><a name="onmnemonic"></a>IOleControlImpl::OnMnemonic

Informa al control de que un usuario ha presionado una pulsación de tecla especificada.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Consulte [IOleControl::OnMnemonic](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Clase IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Interfaces de controles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
