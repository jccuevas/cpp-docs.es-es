---
title: IPersistStorageImpl (clase)
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
ms.openlocfilehash: 3239ed22e37ff694c9f399b05e765d63e97e99ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276151"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl (clase)

Esta clase implementa la [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) interfaz.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IPersistStorageImpl`.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Recupera el CLSID del objeto.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Indica al objeto para liberar todos los objetos de almacenamiento y entrar en modo de HandsOff. La implementación de ATL devuelve S_OK.|
|[IPersistStorageImpl::InitNew](#initnew)|Inicializa un nuevo almacenamiento.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Comprueba si los datos del objeto ha cambiado desde que se guardó por última vez.|
|[IPersistStorageImpl::Load](#load)|Carga las propiedades del objeto desde el almacenamiento especificado.|
|[IPersistStorageImpl::Save](#save)|Guarda las propiedades del objeto en el almacenamiento especificado.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Notifica a un objeto que puede volver al modo Normal para escribir en su objeto de almacenamiento. La implementación de ATL devuelve S_OK.|

## <a name="remarks"></a>Comentarios

`IPersistStorageImpl` implementa el [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) interfaz, que permite que un cliente para solicitar que la carga del objeto y guardar sus datos persistentes con una de almacenamiento.

La implementación de esta clase requiere la clase `T` para realizar una implementación de la `IPersistStreamInit` disponible a través de la interfaz `QueryInterface`. Normalmente, esto significa que esa clase `T` debe derivar de [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), proporcione una entrada para `IPersistStreamInit` en el [mapa COM](com-map-macros.md)y usar un [deasignacióndepropiedad](property-map-macros.md) para describir los datos persistentes de la clase.

**Artículos relacionados con** [Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID

Recupera el CLSID del objeto.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Comentarios

Consulte [IPersist:: GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) en el SDK de Windows.

##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage

Indica al objeto para liberar todos los objetos de almacenamiento y entrar en modo de HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IPersistStorage::HandsOffStorage](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) en el SDK de Windows.

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

Inicializa un nuevo almacenamiento.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Comentarios

La implementación de ATL se delega en el [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfaz.

Consulte [IPersistStorage:InitNew](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-initnew) en el SDK de Windows.

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

Comprueba si los datos del objeto ha cambiado desde que se guardó por última vez.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Comentarios

La implementación de ATL se delega en el [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfaz.

Consulte [IPersistStorage:IsDirty](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-isdirty) en el SDK de Windows.

##  <a name="load"></a>  IPersistStorageImpl::Load

Carga las propiedades del objeto desde el almacenamiento especificado.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Comentarios

La implementación de ATL se delega en el [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfaz. `Load` usa un flujo denominado "Contenido" para recuperar los datos del objeto. El [guardar](#save) método originalmente crea esta secuencia.

Consulte [IPersistStorage:Load](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-load) en el SDK de Windows.

##  <a name="save"></a>  IPersistStorageImpl::Save

Guarda las propiedades del objeto en el almacenamiento especificado.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Comentarios

La implementación de ATL se delega en el [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) interfaz. Cuando `Save` es el primero se llama, crea una secuencia denominada "Contenido" en el almacenamiento especificado. Este flujo, a continuación, se utiliza en las llamadas posteriores a `Save` y en las llamadas a [carga](#load).

Consulte [IPersistStorage:Save](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-save) en el SDK de Windows.

##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted

Notifica a un objeto que puede volver al modo Normal para escribir en su objeto de almacenamiento.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK.

### <a name="remarks"></a>Comentarios

Consulte [IPersistStorage:SaveCompleted](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-savecompleted) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Secuencias y almacenamientos](/windows/desktop/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl (clase)](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl (clase)](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
