---
title: Clase ICollectionOnSTLImpl
ms.date: 11/04/2016
f1_keywords:
- ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl
- ATLCOM/ATL::ICollectionOnSTLImpl::get__NewEnum
- ATLCOM/ATL::ICollectionOnSTLImpl::getcount
- ATLCOM/ATL::ICollectionOnSTLImpl::get_Item
- ATLCOM/ATL::ICollectionOnSTLImpl::m_coll
helpviewer_keywords:
- ICollectionOnSTLImpl class
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
ms.openlocfilehash: a8ccab08b89da8c1b8ef56c8932e27a6c74e62aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329906"
---
# <a name="icollectiononstlimpl-class"></a>Clase ICollectionOnSTLImpl

Esta clase proporciona métodos utilizados por una clase de colección.

## <a name="syntax"></a>Sintaxis

```
template <class T, class CollType, class ItemType, class CopyItem, class EnumType>
class ICollectionOnSTLImpl : public T
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Una interfaz de colección COM.

*CollType*<br/>
Una clase contenedora de biblioteca estándar C++ .

*ItemType*<br/>
El tipo de elemento expuesto por la interfaz contenedora.

*CopyItem*<br/>
Una clase de política de [copia](../../atl/atl-copy-policy-classes.md).

*EnumType*<br/>
Una clase de enumerador compatible con [CComEnumOnSTL.](../../atl/reference/ccomenumonstl-class.md)

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ICollectionOnSTLImpl::get__NewEnum](#newenum)|Devuelve un objeto enumerador para la colección.|
|[ICollectionOnSTLImpl::getcount](#get_count)|Devuelve el número de elementos de la colección.|
|[ICollectionOnSTLImpl::get_Item](#get_item)|Devuelve el elemento solicitado de la colección.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ICollectionOnSTLImpl::m_coll](#m_coll)|La colección.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona la implementación para tres métodos de una interfaz de colección: [getcount](#get_count), [get_Item](#get_item)y [get__NewEnum](#newenum).

Para utilizar esta clase:

- Defina (o preste) una interfaz de colección que desee implementar.

- Derive su clase de `ICollectionOnSTLImpl` una especialización de basada en esta interfaz de colección.

- Utilice la clase derivada para implementar cualquier método de `ICollectionOnSTLImpl`la interfaz de colección no controlado por .

> [!NOTE]
> Si la interfaz de colección es una interfaz dual, derive la clase de [IDispatchImpl](../../atl/reference/idispatchimpl-class.md), pasando la `ICollectionOnSTLImpl` especialización como el primer parámetro de plantilla si desea que ATL proporcione la implementación de los `IDispatch` métodos.

- Agregue elementos al [miembro m_coll](#m_coll) para rellenar la colección.

Para obtener más información y ejemplos, vea [ATL Collections and Enumerators](../../atl/atl-collections-and-enumerators.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`T`

`ICollectionOnSTLImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="icollectiononstlimplgetcount"></a><a name="get_count"></a>ICollectionOnSTLImpl::getcount

Este método devuelve el número de elementos de la colección.

```
STDMETHOD(getcount)(long* pcount);
```

### <a name="parameters"></a>Parámetros

*pcount*<br/>
[fuera] El número de elementos de la colección.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="icollectiononstlimplget_item"></a><a name="get_item"></a>ICollectionOnSTLImpl::get_Item

Este método devuelve el elemento especificado de la colección.

```
STDMETHOD(get_Item)(long Index, ItemType* pvar);
```

### <a name="parameters"></a>Parámetros

*Índice*<br/>
[en] El índice basado en 1 de un elemento de la colección.

*pvar*<br/>
[fuera] El elemento correspondiente a *Index*.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El elemento se obtiene copiando los datos en la posición especificada en [m_coll](#m_coll) mediante el método `ICollectionOnSTLImpl` copy de la clase de directiva de [copia](../../atl/atl-copy-policy-classes.md) pasada como argumento de plantilla en la especialización.

## <a name="icollectiononstlimplget__newenum"></a><a name="newenum"></a>ICollectionOnSTLImpl::get__NewEnum

Devuelve un objeto enumerador para la colección.

```
STDMETHOD(get__NewEnum)(IUnknown** ppUnk);
```

### <a name="parameters"></a>Parámetros

*ppUnk*<br/>
[fuera] El puntero **IUnknown** de un objeto enumerador recién creado.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El enumerador recién creado mantiene un `m_coll`iterador en la colección original, , (por lo que no se realiza ninguna copia) y contiene una referencia COM en el objeto de colección para asegurarse de que la colección permanece activa mientras hay enumeradores excepcionales.

## <a name="icollectiononstlimplm_coll"></a><a name="m_coll"></a>ICollectionOnSTLImpl::m_coll

Este miembro contiene los elementos representados por la colección.

```
CollType m_coll;
```

## <a name="see-also"></a>Consulte también

[Ejemplo de ATLCollections](../../overview/visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
