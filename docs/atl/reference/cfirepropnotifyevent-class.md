---
title: Clase CFirePropNotifyEvent
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 1dfce42176341d74ffc7d9b42f856e71b17bf4f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326971"
---
# <a name="cfirepropnotifyevent-class"></a>Clase CFirePropNotifyEvent

Esta clase proporciona métodos para notificar el receptor del contenedor con respecto a los cambios de propiedad de control.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|(Estático) Notifica al receptor del contenedor que ha cambiado una propiedad de control.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|(Estático) Notifica al receptor del contenedor que una propiedad de control está a punto de cambiar.|

## <a name="remarks"></a>Observaciones

`CFirePropNotifyEvent`tiene dos métodos que notifican al receptor del contenedor que una propiedad de control ha cambiado o está a punto de cambiar.

Si la clase que implementa `IPropertyNotifySink`el `CFirePropNotifyEvent` control se deriva `FireOnRequestEdit` de `FireOnChanged`, los métodos se invocan al llamar o . Si la clase de control `IPropertyNotifySink`no se deriva de , las llamadas a estas funciones devuelven S_OK.

Para obtener más información sobre la creación de controles, consulte el [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged

Notifica a todas las interfaces [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) conectadas (en cada punto de conexión del objeto) que la propiedad de objeto especificada ha cambiado.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] Puntero al `IUnknown` objeto que envía la notificación.

*dispID*<br/>
[en] Identificador de la propiedad que ha cambiado.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función es segura de llamar incluso si el control no admite puntos de conexión.

## <a name="cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit

Notifica a todas las interfaces [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) conectadas (en cada punto de conexión del objeto) que la propiedad de objeto especificada está a punto de cambiar.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*Punk*<br/>
[en] Puntero al `IUnknown` objeto que envía la notificación.

*dispID*<br/>
[en] Identificador de la propiedad a punto de cambiar.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función es segura de llamar incluso si el control no admite puntos de conexión.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
