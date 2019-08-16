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
ms.openlocfilehash: c5e2fa64cc0938e632a37eac7dd1d6e9111c3d98
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497318"
---
# <a name="ccomcontainedobject-class"></a>Clase CComContainedObject

Esta clase implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) delegando en el del `IUnknown`objeto propietario.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parámetros

*Básica*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|El constructor. Inicializa el puntero de miembro a la propiedad del objeto `IUnknown`del propietario.|
|[CComContainedObject::~CComContainedObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto propietario.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Recupera el del objeto del `IUnknown`propietario.|
|[CComContainedObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada en el objeto propietario.|
|[CComContainedObject::Release](#release)|Disminuye el recuento de referencias en el objeto propietario.|

## <a name="remarks"></a>Comentarios

ATL usa `CComContainedObject` en las clases [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md)y [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) delegando en el del `IUnknown`objeto propietario. (El propietario es el objeto externo de una agregación o el objeto para el que se crea una interfaz de recorte). `OuterAddRef` `OuterQueryInterface` `CComObjectRootEx`, y todas`OuterRelease`las llamadas se heredan a través`Base`de. `CComContainedObject`

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComContainedObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="addref"></a>  CComContainedObject::AddRef

Incrementa el recuento de referencias en el objeto propietario.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

##  <a name="ccomcontainedobject"></a>  CComContainedObject::CComContainedObject

El constructor.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*pv*<br/>
de Del `IUnknown`objeto propietario.

### <a name="remarks"></a>Comentarios

Establece el `m_pOuterUnknown` puntero de miembro (heredado `Base` a través de la clase) en *PV*.

##  <a name="dtor"></a>  CComContainedObject::~CComContainedObject

Destructor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="getcontrollingunknown"></a>  CComContainedObject::GetControllingUnknown

Devuelve el `m_pOuterUnknown` puntero de miembro (heredado a través de la clase *base* ) que contiene `IUnknown`la propiedad del objeto propietario.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Valor devuelto

Del `IUnknown`objeto propietario.

### <a name="remarks"></a>Comentarios

Este método puede ser virtual si `Base` ha declarado la macro [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) .

##  <a name="queryinterface"></a>  CComContainedObject::QueryInterface

Recupera un puntero a la interfaz solicitada en el objeto propietario.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
de Identificador de la interfaz que se solicita.

*ppvObject*<br/>
enuncia Puntero al puntero de interfaz identificado por *IID*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

*pp*<br/>
enuncia Puntero al puntero de interfaz identificado por el tipo `Q`. Si el objeto no admite esta interfaz, *PP* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="release"></a>  CComContainedObject::Release

Disminuye el recuento de referencias en el objeto propietario.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas. En las compilaciones que `Release` no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
