---
title: IConnectionPointContainerImpl (clase)
ms.date: 11/04/2016
f1_keywords:
- IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl
- ATLCOM/ATL::IConnectionPointContainerImpl::EnumConnectionPoints
- ATLCOM/ATL::IConnectionPointContainerImpl::FindConnectionPoint
helpviewer_keywords:
- connectable objects
- connection points [C++], container
- IConnectionPointContainerImpl class
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
ms.openlocfilehash: 06baa4dac3248d783648b8ce37e51250e0de2498
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275521"
---
# <a name="iconnectionpointcontainerimpl-class"></a>IConnectionPointContainerImpl (clase)

Esta clase implementa un contenedor de punto de conexión para administrar una colección de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objetos.

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IConnectionPointContainerImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Crea un enumerador para recorrer en iteración los puntos de conexión admitidos en el objeto conectable.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Recupera un puntero de interfaz al punto de conexión que admite el IID especificado.|

## <a name="remarks"></a>Comentarios

`IConnectionPointContainerImpl` implementa un contenedor de punto de conexión para administrar una colección de [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) objetos. `IConnectionPointContainerImpl` proporciona dos métodos que un cliente puede llamar para recuperar más información acerca de un objeto conectable:

- `EnumConnectionPoints` permite al cliente determinar qué tipo de salida el objeto admite las interfaces.

- `FindConnectionPoint` permite al cliente determinar si el objeto admite una interfaz de salida específica.

Para obtener información sobre el uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints

Crea un enumerador para recorrer en iteración los puntos de conexión admitidos en el objeto conectable.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Comentarios

Consulte [IConnectionPointContainer:: EnumConnectionPoints](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) en el SDK de Windows.

##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint

Recupera un puntero de interfaz al punto de conexión que admite el IID especificado.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Comentarios

Consulte [IConnectionPointContainer:: FindConnectionPoint](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
