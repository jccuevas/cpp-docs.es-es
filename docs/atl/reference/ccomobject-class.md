---
title: CComObject (clase)
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
ms.openlocfilehash: a2051932413d8658eb7cedb67ed0eab2077b599d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497133"
---
# <a name="ccomobject-class"></a>CComObject (clase)

Esta clase implementa `IUnknown` para un objeto no agregado.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Parámetros

*Básica*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|El constructor.|
|[CComObject::~CComObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto.|
|[CComObject::CreateInstance](#createinstance)|Estático Crea un nuevo `CComObject` objeto.|
|[CComObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComObject::Release](#release)|Disminuye el recuento de referencias en el objeto.|

## <a name="remarks"></a>Comentarios

`CComObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto no agregado. Sin embargo, las `QueryInterface`llamadas `AddRef`a, `Release` y se delegan `CComObjectRootEx`a.

Para obtener más información sobre `CComObject`el uso de, vea el artículo [fundamentos de objetos COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="addref"></a>  CComObject::AddRef

Incrementa el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Esta función devuelve el nuevo recuento de referencias incrementadas en el objeto. Este valor puede ser útil para diagnósticos o pruebas.

##  <a name="ccomobject"></a>  CComObject::CComObject

El constructor incrementa el recuento de bloqueos del módulo.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Parámetros

<em>void\*</em><br/>
de No se usa este parámetro sin nombre. Existe para la simetría con otros `CComXXXObjectXXX` constructores.

### <a name="remarks"></a>Comentarios

El destructor lo reduce.

Si un `CComObject`objeto derivado de se construye correctamente mediante el operador **New** , el recuento de referencias inicial es 0. Para establecer el recuento de referencias en el valor adecuado (1), realice una llamada a la función [AddRef](#addref) .

##  <a name="dtor"></a>  CComObject::~CComObject

Destructor.

```
CComObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados, llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease)y disminuye el recuento de bloqueos del módulo.

##  <a name="createinstance"></a>  CComObject::CreateInstance

Esta función estática permite crear un nuevo objeto **CComObject <** `Base` **>** , sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Parámetros

*pp*<br/>
enuncia Puntero a un puntero de **<** `Base` **>** CComObject. Si `CreateInstance` no se realiza correctamente, *PP* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El objeto devuelto tiene un recuento de referencias de cero `AddRef` , por lo que `Release` debe llamar a inmediatamente y después usar para liberar la referencia en el puntero de objeto cuando haya terminado.

Si no necesita acceso directo al objeto, pero aún desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, use [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>  CComObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

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

##  <a name="release"></a>  CComObject::Release

Disminuye el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

Esta función devuelve el nuevo recuento de referencias disminuido en el objeto. En las compilaciones de depuración, el valor devuelto puede ser útil para diagnósticos o pruebas. En las compilaciones que `Release` no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Vea también

[CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject (clase)](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
