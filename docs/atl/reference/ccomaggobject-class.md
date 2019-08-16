---
title: CComAggObject (clase)
ms.date: 11/04/2016
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
ms.openlocfilehash: 8b05284104f9d2e5e7704bceaee6f8adf9a33aac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497655"
---
# <a name="ccomaggobject-class"></a>CComAggObject (clase)

Esta clase implementa la interfaz [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto agregado. Por definición, un objeto agregado está contenido dentro de un objeto externo. La `CComAggObject` clase es similar a la [clase CComObject](../../atl/reference/ccomobject-class.md), salvo que expone una interfaz que es directamente accesible a los clientes externos.

## <a name="syntax"></a>Sintaxis

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parámetros

*contained*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|El constructor.|
|[CComAggObject::~CComAggObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto agregado.|
|[CComAggObject::CreateInstance](#createinstance)|Esta función estática permite crear un nuevo objeto **CComAggObject <** `contained` **>** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Realiza la inicialización `m_contained`final de.|
|[CComAggObject::FinalRelease](#finalrelease)|Realiza la destrucción final `m_contained`de.|
|[CComAggObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComAggObject::Release](#release)|Disminuye el recuento de referencias en el objeto agregado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Delega `IUnknown` las llamadas a la desconocida externa.|

## <a name="remarks"></a>Comentarios

`CComAggObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto agregado. `CComAggObject`tiene su propia `IUnknown` interfaz, independiente de la interfaz del `IUnknown` objeto externo, y mantiene su propio recuento de referencias.

Para obtener más información acerca de la agregación, vea el artículo [fundamentos de objetos COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="addref"></a>  CComAggObject::AddRef

Incrementa el recuento de referencias en el objeto agregado.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject

El constructor.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*pv*<br/>
de Desconocido externo.

### <a name="remarks"></a>Comentarios

Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained)e incrementa el recuento de bloqueos del módulo.

El destructor reduce el número de bloqueos del módulo.

##  <a name="dtor"></a>  CComAggObject::~CComAggObject

Destructor.

```
~CComAggObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados, llama a [FinalRelease](#finalrelease)y disminuye el recuento de bloqueos del módulo.

##  <a name="createinstance"></a>  CComAggObject::CreateInstance

Esta función estática permite crear un nuevo objeto **CComAggObject <** `contained` **>** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parámetros

*pp*<br/>
enuncia Un puntero a un puntero<em>contenido</em> **>** de **CComAggObject\<** . Si `CreateInstance` no se realiza correctamente, *PP* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El objeto devuelto tiene un recuento de referencias de cero `AddRef` , por lo que `Release` debe llamar a inmediatamente y después usar para liberar la referencia en el puntero de objeto cuando haya terminado.

Si no necesita acceso directo al objeto, pero aún desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, use [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.

##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct

Se llama durante la fase final de la construcción de un objeto, este método realiza cualquier inicialización final en el miembro [m_contained](#m_contained) .

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="finalrelease"></a>  CComAggObject::FinalRelease

Se llama durante la destrucción del objeto, este método libera el miembro [m_contained](#m_contained) .

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComAggObject::m_contained

Objeto [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) derivado de la clase.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*contained*<br/>
de La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

### <a name="remarks"></a>Comentarios

Todas `IUnknown` las llamadas `m_contained` a través de se delegan al desconocido externo.

##  <a name="queryinterface"></a>  CComAggObject::QueryInterface

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

### <a name="remarks"></a>Comentarios

Si la interfaz solicitada `IUnknown`es `QueryInterface` , devuelve un puntero al propio `IUnknown` objeto agregado e incrementa el recuento de referencias. De lo contrario, este método consulta la interfaz a `CComContainedObject` través del miembro, [m_contained](#m_contained).

##  <a name="release"></a>  CComAggObject::Release

Disminuye el recuento de referencias en el objeto agregado.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas. En las compilaciones que `Release` no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Vea también

[CComObject (clase)](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject (clase)](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
