---
title: IOleControlImpl (clase)
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
ms.openlocfilehash: 50119d21b041f37f03ca416a9a56ca9e29ae3344
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263538"
---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl (clase)

Esta clase proporciona una implementación predeterminada de la `IOleControl` interfaz e implementa `IUnknown`.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IOleControlImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indica si el contenedor pasa por alto o acepta eventos del control.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Rellena la información sobre el comportamiento de teclado del control. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informa a un control que ha cambiado una o varias de las propiedades de ambiente del contenedor. La implementación de ATL devuelve S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informa al control que un usuario ha presionado una pulsación de tecla especificada. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

Clase `IOleControlImpl` proporciona una implementación predeterminada de la [IOleControl](/windows/desktop/api/ocidl/nn-ocidl-iolecontrol) interfaz e implementa `IUnknown` mediante el envío de información para el volcado de memoria se basa el dispositivo en modo de depuración.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents

En la implementación de ATL, `FreezeEvents` incrementa la clase control `m_nFreezeEvents` miembro de datos si `bFreeze` es verdadero y disminuye `m_nFreezeEvents` si `bFreeze` es FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Comentarios

`FreezeEvents` a continuación, devuelve S_OK.

Consulte [IOleControl::FreezeEvents](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-freezeevents) en el SDK de Windows.

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

Rellena la información sobre el comportamiento de teclado del control.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleControl:GetControlInfo](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

Informa a un control que ha cambiado una o varias de las propiedades de ambiente del contenedor.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IOleControl::OnAmbientPropertyChange](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) en el SDK de Windows.

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

Informa al control que un usuario ha presionado una pulsación de tecla especificada.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Consulte [IOleControl::OnMnemonic](/windows/desktop/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[IOleObjectImpl (clase)](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Interfaces de controles ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
