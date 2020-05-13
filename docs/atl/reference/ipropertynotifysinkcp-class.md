---
title: Clase IPropertyNotifySinkCP
ms.date: 11/04/2016
f1_keywords:
- IPropertyNotifySinkCP
- atlctl/ATL::IPropertyNotifySinkCP
helpviewer_keywords:
- connection points [C++], managing
- sinks, notifying of changes
- IPropertyNotifySinkCP class
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
ms.openlocfilehash: c6d98bf5a6dfe5566839eb22bcd2bab2a9c28e4d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329610"
---
# <a name="ipropertynotifysinkcp-class"></a>Clase IPropertyNotifySinkCP

Esta clase expone [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) interfaz como una interfaz saliente en un objeto conectable.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IPropertyNotifySinkCP`de .

*Cdv*<br/>
Clase que administra las conexiones entre un punto de conexión y sus receptores. El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), que permite conexiones ilimitadas. También puede utilizar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.

## <a name="remarks"></a>Observaciones

`IPropertyNotifySinkCP`hereda todos los métodos a través de su clase base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

La interfaz [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) permite que un objeto receptor reciba notificaciones sobre los cambios de propiedad. Clase `IPropertyNotifySinkCP` expone esta interfaz como una interfaz saliente en un objeto conectable. El cliente debe `IPropertyNotifySink` implementar los métodos en el receptor.

Derive la `IPropertyNotifySinkCP` clase de cuando desee crear un `IPropertyNotifySink` punto de conexión que represente la interfaz.

Para obtener más información sobre el uso de puntos de conexión en ATL, consulte el artículo [Puntos](../../atl/atl-connection-points.md)de conexión .

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="see-also"></a>Consulte también

[Clase IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[Clase IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
