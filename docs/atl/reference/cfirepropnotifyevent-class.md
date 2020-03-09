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
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864923"
---
# <a name="cfirepropnotifyevent-class"></a>Clase CFirePropNotifyEvent

Esta clase proporciona métodos para notificar al receptor del contenedor con respecto a los cambios de propiedad del control.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|Estático Notifica al receptor del contenedor que una propiedad de control ha cambiado.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|Estático Notifica al receptor del contenedor que una propiedad de control está a punto de cambiar.|

## <a name="remarks"></a>Observaciones

`CFirePropNotifyEvent` tiene dos métodos que notifican al receptor del contenedor que una propiedad de control ha cambiado o está a punto de cambiar.

Si la clase que implementa el control se deriva de `IPropertyNotifySink`, se invocan los métodos de `CFirePropNotifyEvent` cuando se llama a `FireOnRequestEdit` o `FireOnChanged`. Si la clase de control no se deriva de `IPropertyNotifySink`, las llamadas a estas funciones devuelven S_OK.

Para obtener más información sobre la creación de controles, vea el [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged

Notifica a todas las interfaces de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) conectadas (en cada punto de conexión del objeto) que la propiedad de objeto especificada ha cambiado.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero al `IUnknown` del objeto que envía la notificación.

*dispID*<br/>
de Identificador de la propiedad que ha cambiado.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

La llamada a esta función es segura aunque el control no admita puntos de conexión.

##  <a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit

Notifica a todas las interfaces de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) conectadas (en cada punto de conexión del objeto) que está a punto de cambiar la propiedad de objeto especificada.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero al `IUnknown` del objeto que envía la notificación.

*dispID*<br/>
de Identificador de la propiedad que se va a cambiar.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

La llamada a esta función es segura aunque el control no admita puntos de conexión.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../../atl/atl-class-overview.md)
