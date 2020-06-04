---
title: Clase IPersistStorageImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: b235b190f237293932705e4d290ac963088722f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326471"
---
# <a name="ipersiststorageimpl-class"></a>Clase IPersistStorageImpl

Esta clase implementa la interfaz [IPersistStorage.](/windows/win32/api/objidl/nn-objidl-ipersiststorage)

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Su clase, derivada `IPersistStorageImpl`de .

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Indica al objeto que suelte todos los objetos de almacenamiento y entre en el modo HandsOff. La implementación de ATL devuelve S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicializa un nuevo almacenamiento.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Comprueba si los datos del objeto han cambiado desde la última vez que se guardó.|
|[IPersistStorageImpl::Load](#load)|Carga las propiedades del objeto desde el almacenamiento especificado.|
|[IPersistStorageImpl::Guardar](#save)|Guarda las propiedades del objeto en el almacenamiento especificado.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Notifica a un objeto que puede volver al modo Normal para escribir en su objeto de almacenamiento. La implementación de ATL devuelve S_OK.|

## <a name="remarks"></a>Observaciones

`IPersistStorageImpl`implementa la interfaz [IPersistStorage,](/windows/win32/api/objidl/nn-objidl-ipersiststorage) que permite a un cliente solicitar que el objeto cargue y guarde sus datos persistentes mediante un almacenamiento.

La implementación de esta `T` clase requiere que `IPersistStreamInit` la `QueryInterface`clase haga que una implementación de la interfaz esté disponible a través de . Normalmente, esto `T` significa que la clase debe derivar de [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), proporcionar una entrada para `IPersistStreamInit` en el mapa [COM](com-map-macros.md)y usar un mapa de [propiedades](property-map-macros.md) para describir los datos persistentes de la clase.

**Artículos relacionados** [Tutorial ATL](../../atl/active-template-library-atl-tutorial.md), [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ipersiststorageimplgetclassid"></a><a name="getclassid"></a>IPersistStorageImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Observaciones

Consulte [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) en el Windows SDK.

## <a name="ipersiststorageimplhandsoffstorage"></a><a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage

Indica al objeto que suelte todos los objetos de almacenamiento y entre en el modo HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IPersistStorage::HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) en el Windows SDK.

## <a name="ipersiststorageimplinitnew"></a><a name="initnew"></a>IPersistStorageImpl::InitNew

Inicializa un nuevo almacenamiento.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Observaciones

La implementación ATL delega en la interfaz [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Consulte [IPersistStorage:InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) en el Windows SDK.

## <a name="ipersiststorageimplisdirty"></a><a name="isdirty"></a>IPersistStorageImpl::IsDirty

Comprueba si los datos del objeto han cambiado desde la última vez que se guardó.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Observaciones

La implementación ATL delega en la interfaz [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Consulte [IPersistStorage:IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) en el Windows SDK.

## <a name="ipersiststorageimplload"></a><a name="load"></a>IPersistStorageImpl::Load

Carga las propiedades del objeto desde el almacenamiento especificado.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Observaciones

La implementación ATL delega en la interfaz [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) `Load`utiliza una secuencia denominada "Contents" para recuperar los datos del objeto. El método [Save](#save) crea originalmente esta secuencia.

Consulte [IPersistStorage:Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) en el Windows SDK.

## <a name="ipersiststorageimplsave"></a><a name="save"></a>IPersistStorageImpl::Guardar

Guarda las propiedades del objeto en el almacenamiento especificado.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Observaciones

La implementación ATL delega en la interfaz [IPersistStreamInit.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) Cuando `Save` se llama por primera vez, crea una secuencia denominada "Contents" en el almacenamiento especificado. Esta secuencia se utiliza entonces en llamadas posteriores a `Save` y en llamadas a [Load](#load).

Consulte [IPersistStorage:Guardar](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) en el Windows SDK.

## <a name="ipersiststorageimplsavecompleted"></a><a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted

Notifica a un objeto que puede volver al modo Normal para escribir en su objeto de almacenamiento.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Observaciones

Consulte [IPersistStorage:SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Almacenamientos y streams](/windows/win32/Stg/storages-and-streams)<br/>
[Clase IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[Clase IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
