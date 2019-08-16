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
ms.openlocfilehash: 9838a48b078cbc59a5ae86669ad9f26792d9816e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495628"
---
# <a name="ipropertynotifysinkcp-class"></a>Clase IPropertyNotifySinkCP

Esta clase expone la interfaz [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) como una interfaz de salida en un objeto conectable.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class T, class CDV = CComDynamicUnkArray>
class IPropertyNotifySinkCP
   : public IConnectionPointImpl<T, &IID_IPropertyNotifySink, CDV>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IPropertyNotifySinkCP`.

*CDV*<br/>
Una clase que administra las conexiones entre un punto de conexión y sus receptores. El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), que permite conexiones ilimitadas. También puede usar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.

## <a name="remarks"></a>Comentarios

`IPropertyNotifySinkCP`hereda todos los métodos a través de su clase base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).

La interfaz [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) permite que un objeto receptor reciba notificaciones sobre los cambios de propiedad. La `IPropertyNotifySinkCP` clase expone esta interfaz como una interfaz de salida en un objeto conectable. El cliente debe implementar los `IPropertyNotifySink` métodos en el receptor.

Derive la clase de `IPropertyNotifySinkCP` cuando desee crear un punto de conexión que represente la `IPropertyNotifySink` interfaz.

Para obtener más información sobre el uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

## <a name="see-also"></a>Vea también

[IConnectionPointImpl (clase)](../../atl/reference/iconnectionpointimpl-class.md)<br/>
[IConnectionPointContainerImpl (clase)](../../atl/reference/iconnectionpointcontainerimpl-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
