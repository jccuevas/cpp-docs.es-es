---
title: Clase CComObject
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: de6ffb45fe5c6f73ab656d5c6185b70d9f5edd38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327646"
---
# <a name="ccomobject-class"></a>Clase CComObject

Esta clase `IUnknown` se implementa para un objeto no agregado.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|El constructor.|
|[CComObject::-CComObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto.|
|[CComObject::CreateInstance](#createinstance)|(Estático) Crea un `CComObject` nuevo objeto.|
|[CComObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComObject::Release](#release)|Disminuye el recuento de referencias en el objeto.|

## <a name="remarks"></a>Observaciones

`CComObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto no agregado. Sin embargo, `AddRef`las `Release` llamadas `CComObjectRootEx`a `QueryInterface`, , y se delegan a .

Para obtener más `CComObject`información sobre el uso de , vea el artículo [Fundamentos de objetos COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomobjectaddref"></a><a name="addref"></a>CComObject::AddRef

Incrementa el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Esta función devuelve el nuevo recuento de referencias incrementado en el objeto. Este valor puede ser útil para diagnósticos o pruebas.

## <a name="ccomobjectccomobject"></a><a name="ccomobject"></a>CComObject::CComObject

El constructor incrementa el recuento de bloqueos de módulo.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Parámetros

<em>void\*</em><br/>
[en] Este parámetro sin nombre no se utiliza. Existe para la simetría `CComXXXObjectXXX` con otros constructores.

### <a name="remarks"></a>Observaciones

El destructor lo decremento.

Si `CComObject`un objeto derivado se construye correctamente mediante el operador **new,** el recuento de referencias inicial es 0. Para establecer el recuento de referencias en el valor adecuado (1), realice una llamada a la función [AddRef.](#addref)

## <a name="ccomobjectccomobject"></a><a name="dtor"></a>CComObject::-CComObject

Destructor.

```
CComObject();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados, llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease)y disminuye el recuento de bloqueos del módulo.

## <a name="ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject::CreateInstance

Esta función estática permite crear un nuevo `Base` **>** objeto **de<CComObject,** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Parámetros

*Pp*<br/>
[fuera] Un puntero a un **CComObject puntero de<.** `Base` **>** Si `CreateInstance` no se realiza correctamente, *pp* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El objeto devuelto tiene un recuento `AddRef` de referencias `Release` de cero, así que llame inmediatamente y, a continuación, utilícelo para liberar la referencia en el puntero de objeto cuando haya terminado.

Si no necesita acceso directo al objeto, pero aún desea crear `CoCreateInstance`un nuevo objeto sin la sobrecarga de , utilice [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

## <a name="ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

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

## <a name="ccomobjectrelease"></a><a name="release"></a>CComObject::Release

Disminuye el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

Esta función devuelve el nuevo recuento de referencias decrementados en el objeto. En compilaciones de depuración, el valor devuelto puede ser útil para diagnósticos o pruebas. En compilaciones que `Release` no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Consulte también

[Clase CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject (Clase)](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
