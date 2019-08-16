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
ms.openlocfilehash: a5b5dd4e5be43d01f00687ed9b96a3f27abcad0f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495690"
---
# <a name="ipersiststorageimpl-class"></a>Clase IPersistStorageImpl

Esta clase implementa la interfaz [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) .

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IPersistStorageImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Indica al objeto que libere todos los objetos de almacenamiento y especifique el modo HandsOff. La implementación de ATL Devuelve S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicializa un nuevo almacenamiento.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Comprueba si los datos del objeto han cambiado desde que se guardó por última vez.|
|[IPersistStorageImpl::Load](#load)|Carga las propiedades del objeto desde el almacenamiento especificado.|
|[IPersistStorageImpl::Save](#save)|Guarda las propiedades del objeto en el almacenamiento especificado.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Notifica a un objeto que puede volver al modo normal para escribir en su objeto de almacenamiento. La implementación de ATL Devuelve S_OK.|

## <a name="remarks"></a>Comentarios

`IPersistStorageImpl`implementa la interfaz [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage) , que permite a un cliente solicitar que el objeto cargue y guarde sus datos persistentes mediante un almacenamiento.

La implementación de esta clase requiere que `T` la clase realice una implementación de `IPersistStreamInit` la interfaz disponible `QueryInterface`a través de. Normalmente esto significa que la `T` clase debe derivar de [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), proporcionar una `IPersistStreamInit` entrada para en el [mapa com](com-map-macros.md)y utilizar una [asignación de propiedad](property-map-macros.md) para describir los datos persistentes de la clase.

**Artículos relacionados** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Comentarios

Vea [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) en el Windows SDK.

##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage

Indica al objeto que libere todos los objetos de almacenamiento y especifique el modo HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IPersistStorage:: HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) en el Windows SDK.

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

Inicializa un nuevo almacenamiento.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Comentarios

La implementación de ATL delega en la interfaz [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

Consulte [IPersistStorage: InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) en el Windows SDK.

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

Comprueba si los datos del objeto han cambiado desde que se guardó por última vez.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Comentarios

La implementación de ATL delega en la interfaz [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) .

Consulte [IPersistStorage: IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) en el Windows SDK.

##  <a name="load"></a>  IPersistStorageImpl::Load

Carga las propiedades del objeto desde el almacenamiento especificado.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Comentarios

La implementación de ATL delega en la interfaz [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) . `Load`usa una secuencia denominada "contents" para recuperar los datos del objeto. El método [Save](#save) crea originalmente esta secuencia.

Consulte [IPersistStorage: Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) en el Windows SDK.

##  <a name="save"></a>  IPersistStorageImpl::Save

Guarda las propiedades del objeto en el almacenamiento especificado.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Comentarios

La implementación de ATL delega en la interfaz [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) . Cuando `Save` se llama por primera vez, se crea una secuencia denominada "Content" en el almacenamiento especificado. Después, esta secuencia se usa en llamadas posteriores `Save` a y en llamadas a [Load](#load).

Consulte [IPersistStorage: Save](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) en el Windows SDK.

##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted

Notifica a un objeto que puede volver al modo normal para escribir en su objeto de almacenamiento.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IPersistStorage: SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Almacenamiento y secuencias](/windows/win32/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl (clase)](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl (clase)](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
