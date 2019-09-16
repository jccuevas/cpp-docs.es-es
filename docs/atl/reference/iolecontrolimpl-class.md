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
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495821"
---
# <a name="iolecontrolimpl-class"></a>Clase IOleControlImpl

Esta clase proporciona una implementación predeterminada de la `IOleControl` interfaz e `IUnknown`implementa.

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

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IOleControlImpl::FreezeEvents](#freezeevents)|Indica si el contenedor omite o acepta eventos del control.|
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|Rellena la información sobre el comportamiento del teclado del control. La implementación de ATL devuelve E_NOTIMPL.|
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|Informa a un control de que una o varias de las propiedades de ambiente del contenedor han cambiado. La implementación de ATL Devuelve S_OK.|
|[IOleControlImpl::OnMnemonic](#onmnemonic)|Informa al control de que un usuario ha presionado una pulsación de tecla especificada. La implementación de ATL devuelve E_NOTIMPL.|

## <a name="remarks"></a>Comentarios

La clase `IOleControlImpl` proporciona una implementación predeterminada de la interfaz [IOleControl](/windows/win32/api/ocidl/nn-ocidl-iolecontrol) e implementa `IUnknown` enviando información al dispositivo de volcado en las compilaciones de depuración.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IOleControl`

`IOleControlImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="freezeevents"></a>  IOleControlImpl::FreezeEvents

En la implementación de ATL `FreezeEvents` , incrementa el miembro de datos `m_nFreezeEvents` de la clase `bFreeze` de control si es true y `m_nFreezeEvents` disminuye `bFreeze` si es false.

```
HRESULT FreezeEvents(BOOL bFreeze);
```

### <a name="remarks"></a>Comentarios

`FreezeEvents`Devuelve S_OK.

Vea [IOleControl:: FreezeEvents](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-freezeevents) en el Windows SDK.

##  <a name="getcontrolinfo"></a>  IOleControlImpl::GetControlInfo

Rellena la información sobre el comportamiento del teclado del control.

```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```

### <a name="remarks"></a>Comentarios

Consulte [IOleControl: GetControlInfo](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-getcontrolinfo) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

##  <a name="onambientpropertychange"></a>  IOleControlImpl::OnAmbientPropertyChange

Informa a un control de que una o varias de las propiedades de ambiente del contenedor han cambiado.

```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Vea [IOleControl:: OnAmbientPropertyChange](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onambientpropertychange) en el Windows SDK.

##  <a name="onmnemonic"></a>  IOleControlImpl::OnMnemonic

Informa al control de que un usuario ha presionado una pulsación de tecla especificada.

```
HRESULT OnMnemonic(LPMSG pMsg);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOTIMPL.

### <a name="remarks"></a>Comentarios

Vea [IOleControl::](/windows/win32/api/ocidl/nf-ocidl-iolecontrol-onmnemonic) en el Windows SDK.

## <a name="see-also"></a>Vea también

[IOleObjectImpl (clase)](../../atl/reference/ioleobjectimpl-class.md)<br/>
[Interfaces de controles ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
