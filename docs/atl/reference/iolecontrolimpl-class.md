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
ms.openlocfilehash: 3bdb501d8210c98ce982719358564c4937991e12
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864972"
---
# <a name="iolecontrolimpl-class"></a>Clase IOleControlImpl

Esta clase proporciona una implementación predeterminada de la interfaz `IOleControl` e implementa `IUnknown`.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class IOleControlImpl
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IOleControlImpl`.

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indica si el contenedor omite o acepta eventos del control.|
|[IOleControlImpl:: GetControlInfo](#getcontrolinfo)|Rellena la información sobre el comportamiento del teclado del control. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleControlImpl:: OnAmbientPropertyChange](#onambientpropertychange)|Informa a un control de que una o varias de las propiedades de ambiente del contenedor han cambiado. La implementación de ATL Devuelve S_OK.|
|[IOleControlImpl::](#onmnemonic)|Informa al control de que un usuario ha presionado una pulsación de tecla especificada. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Observaciones

La clase `IOleControlImpl` proporciona una implementación predeterminada de la interfaz [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) e implementa `IUnknown` enviando información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="freezeevents"></a>IOleControlImpl::FreezeEvents

En la implementación de ATL, `FreezeEvents` incrementa el miembro de datos `m_nFreezeEvents` de la clase de control si `bFreeze` es TRUE y disminuye `m_nFreezeEvents` si `bFreeze` es FALSE.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Observaciones

`FreezeEvents` Devuelve S_OK.

Vea [IOleControl:: FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) en el Windows SDK.

##  <a name="getcontrolinfo"></a>IOleControlImpl:: GetControlInfo

Rellena la información sobre el comportamiento del teclado del control.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Observaciones

Consulte [IOleControl: GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="onambientpropertychange"></a>IOleControlImpl:: OnAmbientPropertyChange

Informa a un control de que una o varias de las propiedades de ambiente del contenedor han cambiado.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Vea [IOleControl:: OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) en el Windows SDK.

##  <a name="onmnemonic"></a>IOleControlImpl::

Informa al control de que un usuario ha presionado una pulsación de tecla especificada.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Observaciones

Vea [IOleControl::](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[IOleObjectImpl (clase)](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Interfaces de controles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
