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
ms.openlocfilehash: d993a349d38342bda30a83dfdbe25577953799b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497534"
---
# <a name="ccomcachedtearoffobject-class"></a>Clase CComCachedTearOffObject

Esta clase implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para una interfaz de recorte.

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

*contained*<br/>
La clase de recorte, derivada de `CComTearOffObjectBase` y las interfaces que desea que admita el objeto de recorte.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|El constructor.|
|[CComCachedTearOffObject::~CComCachedTearOffObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Incrementa el recuento de referencias de `CComCachedTearOffObject` un objeto.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Llama al `m_contained::FinalConstruct` método de la clase de recorte.|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Llama al `m_contained::FinalRelease` método de la clase de recorte.|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero al `IUnknown` `CComCachedTearOffObject` del objeto o a la interfaz solicitada en la clase de recorte (la clase `contained`).|
|[CComCachedTearOffObject::Release](#release)|Disminuye el recuento de referencias para `CComCachedTearOffObject` un objeto y lo destruye si el recuento de referencias es 0.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Objeto derivado de la clase Tear (la clase `contained`). `CComContainedObject`|

## <a name="remarks"></a>Comentarios

`CComCachedTearOffObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para una interfaz de recorte. Esta clase difiere `CComTearOffObject` de en que `CComCachedTearOffObject` tiene su propio `IUnknown`, independiente de la del objeto del `IUnknown` propietario (el propietario es el objeto para el que se crea el recorte). `CComCachedTearOffObject`mantiene su propio recuento de referencias `IUnknown` en su y se elimina una vez que su recuento de referencias es cero. Sin embargo, si realiza una consulta para cualquiera de las interfaces interrumpidas, se incrementará el recuento de `IUnknown` referencias del objeto del propietario.

Si ya `CComCachedTearOffObject` se ha creado una instancia del objeto que implementa el recorte y la interfaz de recorte se consulta de nuevo, se `CComCachedTearOffObject` reutiliza el mismo objeto. En cambio, si `CComTearOffObject` se consulta de nuevo una interfaz de recorte implementada por mediante el objeto propietario, se creará una instancia de otra. `CComTearOffObject`

La clase propietaria debe implementar `FinalRelease` y llamar `Release` a en `CComCachedTearOffObject`la memoria `IUnknown` caché para, lo que disminuirá su recuento de referencias. Esto hará `CComCachedTearOffObject` `FinalRelease` que se llame a y se elimine el recorte.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="addref"></a>  CComCachedTearOffObject::AddRef

Incrementa el recuento de referencias del `CComCachedTearOffObject` objeto en 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para los diagnósticos y las pruebas.

##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject

El constructor.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*pv*<br/>
de Puntero a la `IUnknown` `CComCachedTearOffObject`de.

### <a name="remarks"></a>Comentarios

Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained).

##  <a name="dtor"></a>  CComCachedTearOffObject::~CComCachedTearOffObject

Destructor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados y llama a [FinalRelease](#finalrelease).

##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct

Llamadas `m_contained::FinalConstruct` a Create `m_contained`, el `CComContainedObject` objeto>que`contained`se usa para tener acceso a la interfaz implementada por la clase Tear. < 

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease

Llamadas `m_contained::FinalRelease` a Free `m_contained`, el `CComContainedObject` < objeto >. `contained`

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained

Objeto [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) derivado de la clase Tear.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*contained*<br/>
de La clase de recorte, derivada de `CComTearOffObjectBase` y las interfaces que desea que admita el objeto de recorte.

### <a name="remarks"></a>Comentarios

Los métodos `m_contained` heredados se usan para tener acceso a la interfaz de recorte en la clase de recorte a través de los objetos, `FinalConstruct`y `QueryInterface` `FinalRelease`del objeto recortado en caché.

##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
de GUID de la interfaz que se solicita.

*ppvObject*<br/>
enuncia Puntero al puntero de interfaz identificado por *IID*, o null si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si la interfaz solicitada `IUnknown`es, devuelve un puntero `CComCachedTearOffObject`a su propio `IUnknown` e incrementa el recuento de referencias. De lo contrario, consulta la interfaz en la clase de recorte mediante el método [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) heredado de `CComObjectRootEx`.

##  <a name="release"></a>  CComCachedTearOffObject::Release

Disminuye el recuento de referencias en 1 y, si el recuento de referencias es 0, `CComCachedTearOffObject` elimina el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En las compilaciones que no son de depuración, siempre devuelve 0. En compilaciones de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas.

## <a name="see-also"></a>Vea también

[CComTearOffObject (clase)](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
