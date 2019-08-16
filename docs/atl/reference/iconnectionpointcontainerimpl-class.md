---
title: Clase IConnectionPointContainerImpl
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
ms.openlocfilehash: 278ca6b1b9aac9539680d90b6fa0b18df22fc2f0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496023"
---
# <a name="iconnectionpointcontainerimpl-class"></a>Clase IConnectionPointContainerImpl

Esta clase implementa un contenedor de puntos de conexión para administrar una colección de objetos [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .

## <a name="syntax"></a>Sintaxis

```
template<class T>
class ATL_NO_VTABLE IConnectionPointContainerImpl
   : public IConnectionPointContainer
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IConnectionPointContainerImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IConnectionPointContainerImpl::EnumConnectionPoints](#enumconnectionpoints)|Crea un enumerador para recorrer en iteración los puntos de conexión admitidos en el objeto conectable.|
|[IConnectionPointContainerImpl::FindConnectionPoint](#findconnectionpoint)|Recupera un puntero de interfaz al punto de conexión que admite el IID especificado.|

## <a name="remarks"></a>Comentarios

`IConnectionPointContainerImpl`implementa un contenedor de puntos de conexión para administrar una colección de objetos [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) . `IConnectionPointContainerImpl`proporciona dos métodos a los que un cliente puede llamar para recuperar más información sobre un objeto conectable:

- `EnumConnectionPoints`permite al cliente determinar qué interfaces de salida admite el objeto.

- `FindConnectionPoint`permite al cliente determinar si el objeto admite una interfaz de salida específica.

Para obtener información sobre el uso de puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IConnectionPointContainer`

`IConnectionPointContainerImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="enumconnectionpoints"></a>  IConnectionPointContainerImpl::EnumConnectionPoints

Crea un enumerador para recorrer en iteración los puntos de conexión admitidos en el objeto conectable.

```
STDMETHOD(EnumConnectionPoints)(IEnumConnectionPoints** ppEnum);
```

### <a name="remarks"></a>Comentarios

Vea [IConnectionPointContainer:: EnumConnectionPoints](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-enumconnectionpoints) en el Windows SDK.

##  <a name="findconnectionpoint"></a>  IConnectionPointContainerImpl::FindConnectionPoint

Recupera un puntero de interfaz al punto de conexión que admite el IID especificado.

```
STDMETHOD(FindConnectionPoint)(REFIID riid, IConnectionPoint** ppCP);
```

### <a name="remarks"></a>Comentarios

Vea [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) en el Windows SDK.

## <a name="see-also"></a>Vea también

[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
