---
title: Clase CComCachedTearOffObject
ms.date: 11/04/2016
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
ms.openlocfilehash: 019b90c932de144d05fbf05f3ca339f4e5d6edd1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748104"
---
# <a name="ccomcachedtearoffobject-class"></a>Clase CComCachedTearOffObject

Esta clase implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para una interfaz de desmontaje.

## <a name="syntax"></a>Sintaxis

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parámetros

*Contenido*<br/>
Su clase de desmontaje, derivada de `CComTearOffObjectBase` y las interfaces que desea que su objeto de desmontaje para admitir.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CcomCachedTearOffObject::ccomCachedTearOffObject](#ccomcachedtearoffobject)|El constructor.|
|[CComCachedTearOffObject::-CcomCachedTearOffObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Incrementa el recuento `CComCachedTearOffObject` de referencias de un objeto.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Llama `m_contained::FinalConstruct` al método (método de la clase tear-off").|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Llama `m_contained::FinalRelease` al método (método de la clase tear-off").|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero `IUnknown` al `CComCachedTearOffObject` objeto o a la interfaz solicitada en `contained`la clase de desmontaje (la clase ).|
|[CComCachedTearOffObject::Release](#release)|Disminuye el recuento de referencias `CComCachedTearOffObject` de un objeto y lo destruye si el recuento de referencias es 0.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CcomCachedTearOffObject::m_contained](#m_contained)|Objeto `CComContainedObject` derivado de la clase tear-off `contained`(la clase ).|

## <a name="remarks"></a>Observaciones

`CComCachedTearOffObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para una interfaz de desmontaje. Esta clase difiere `CComTearOffObject` de `CComCachedTearOffObject` que `IUnknown`tiene su propio , `IUnknown` independiente del objeto propietario (el propietario es el objeto para el que se crea el desmontaje). `CComCachedTearOffObject`mantiene su propio recuento `IUnknown` de referencias en su y se elimina a sí mismo una vez que su recuento de referencias es cero. Sin embargo, si consulta cualquiera de sus interfaces de desmontaje, se incrementará el recuento de referencias de los objetos propietarios. `IUnknown`

Si `CComCachedTearOffObject` el objeto que implementa el desmontaje ya se ha creado una `CComCachedTearOffObject` instancia y se vuelve a consultar la interfaz de desmontaje, se reutiliza el mismo objeto. En cambio, si se vuelve a `CComTearOffObject` consultar una interfaz de desmontaje implementada por a a a través del objeto propietario, se creará una instancia de otra. `CComTearOffObject`

La clase de `FinalRelease` propietario `Release` debe `IUnknown` implementar `CComCachedTearOffObject`y llamar a la caché para el , lo que disminuirá su recuento de referencias. Esto hará `CComCachedTearOffObject`que `FinalRelease` se llame y elimine el desmontaje.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomcachedtearoffobjectaddref"></a><a name="addref"></a>CComCachedTearOffObject::AddRef

Incrementa el recuento `CComCachedTearOffObject` de referencias del objeto en 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos y pruebas.

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="ccomcachedtearoffobject"></a>CcomCachedTearOffObject::ccomCachedTearOffObject

El constructor.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
[en] Puntero a `IUnknown` la `CComCachedTearOffObject`de la .

### <a name="remarks"></a>Observaciones

Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained).

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="dtor"></a>CComCachedTearOffObject::-CcomCachedTearOffObject

Destructor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados y llama a [FinalRelease](#finalrelease).

## <a name="ccomcachedtearoffobjectfinalconstruct"></a><a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct

`m_contained::FinalConstruct` Llamadas `m_contained`para `CComContainedObject` <  `contained` crear , el objeto> utilizado para tener acceso a la interfaz implementada por la clase de desmontaje.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccomcachedtearoffobjectfinalrelease"></a><a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

`m_contained::FinalRelease` Llamadas `m_contained`a `CComContainedObject` <  `contained` free , el objeto>.

```cpp
void FinalRelease();
```

## <a name="ccomcachedtearoffobjectm_contained"></a><a name="m_contained"></a>CcomCachedTearOffObject::m_contained

Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase de desmontaje.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*Contenido*<br/>
[en] Su clase de desmontaje, derivada de `CComTearOffObjectBase` y las interfaces que desea que su objeto de desmontaje para admitir.

### <a name="remarks"></a>Observaciones

Los `m_contained` métodos heredados se utilizan para tener acceso a la interfaz de desmontaje de la clase de desmontaje a través de los objetos de desmontaje almacenados en `QueryInterface`caché, `FinalConstruct`, y `FinalRelease`.

## <a name="ccomcachedtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] GUID de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *iid*, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si la interfaz solicitada es `IUnknown` `CComCachedTearOffObject`, devuelve `IUnknown` un puntero a 's own e incrementa el recuento de referencias. De lo contrario, consulta la interfaz de la clase de `CComObjectRootEx`desmontaje mediante el método [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) heredado de .

## <a name="ccomcachedtearoffobjectrelease"></a><a name="release"></a>CComCachedTearOffObject::Release

Disminuye el recuento de referencias en 1 y, si el `CComCachedTearOffObject` recuento de referencias es 0, elimina el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones que no son de depuración, siempre devuelve 0. En compilaciones de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas.

## <a name="see-also"></a>Vea también

[Clase CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)<br/>
[Clase CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
