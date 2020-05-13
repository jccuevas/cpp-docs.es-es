---
title: Clase CComContainedObject
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 72ba27c3be6576621995ffb8c98995c6abc9324c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320793"
---
# <a name="ccomcontainedobject-class"></a>Clase CComContainedObject

Esta clase implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) delegando en el `IUnknown`objeto propietario .

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|El constructor. Inicializa el puntero de miembro al `IUnknown`objeto propietario.|
|[CComContainedObject::-CComContainedObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto propietario.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Recupera el objeto `IUnknown`propietario .|
|[CComContainedObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada en el objeto propietario.|
|[CComContainedObject::Release](#release)|Disminuye el recuento de referencias en el objeto propietario.|

## <a name="remarks"></a>Observaciones

ATL `CComContainedObject` utiliza en las clases [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md)y [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) delegando en el objeto `IUnknown`propietario . (El propietario es el objeto externo de una agregación o el objeto para el que se crea una interfaz de desmontaje.) `CComContainedObject` `CComObjectRootEx`llamadas `OuterQueryInterface`'s , `OuterAddRef`, y `OuterRelease`, todo heredado a través `Base`de .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComContainedObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomcontainedobjectaddref"></a><a name="addref"></a>CComContainedObject::AddRef

Incrementa el recuento de referencias en el objeto propietario.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject

El constructor.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
[en] El objeto propietario `IUnknown`es .

### <a name="remarks"></a>Observaciones

Establece `m_pOuterUnknown` el puntero de `Base` miembro (heredado a través de la clase) en *pv*.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CComContainedObject::-CComContainedObject

Destructor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados.

## <a name="ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown

Devuelve `m_pOuterUnknown` el puntero de miembro (heredado a través de `IUnknown`la clase *Base)* que contiene el objeto propietario .

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Valor devuelto

El objeto propietario `IUnknown`es .

### <a name="remarks"></a>Observaciones

Este método puede `Base` ser virtual si ha declarado la [macro DECLARE_GET_CONTROLLING_UNKNOWN.](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown)

## <a name="ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CComContainedObject::QueryInterface

Recupera un puntero a la interfaz solicitada en el objeto propietario.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] Identificador de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *iid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

*Pp*<br/>
[fuera] Puntero al puntero de interfaz identificado por tipo `Q`. Si el objeto no admite esta interfaz, *pp* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccomcontainedobjectrelease"></a><a name="release"></a>CComContainedObject::Release

Disminuye el recuento de referencias en el objeto propietario.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas. En compilaciones que `Release` no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
