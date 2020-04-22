---
title: Clase CComAggObject
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
ms.openlocfilehash: b9200c9c396fc16b6df3f4c2f4c66fb7976316d4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748166"
---
# <a name="ccomaggobject-class"></a>Clase CComAggObject

Esta clase implementa la interfaz [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto agregado. Por definición, un objeto agregado está contenido dentro de un objeto externo. La `CComAggObject` clase es similar a la [Clase CComObject](../../atl/reference/ccomobject-class.md), excepto que expone una interfaz que es directamente accesible para los clientes externos.

## <a name="syntax"></a>Sintaxis

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parámetros

*Contenido*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|El constructor.|
|[CComAggObject::-CComAggObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto agregado.|
|[CComAggObject::CreateInstance](#createinstance)|Esta función estática permite crear un nuevo `contained` **>** objeto **de<CComAggObject** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Realiza la inicialización final de `m_contained`.|
|[CComAggObject::FinalRelease](#finalrelease)|Realiza la destrucción final de `m_contained`.|
|[CComAggObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComAggObject::Release](#release)|Disminuye el recuento de referencias en el objeto agregado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Los `IUnknown` delegados llaman a la incógnita externa.|

## <a name="remarks"></a>Observaciones

`CComAggObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto agregado. `CComAggObject`tiene su `IUnknown` propia interfaz, separada `IUnknown` de la interfaz del objeto externo, y mantiene su propio recuento de referencias.

Para obtener más información acerca de la agregación, vea el artículo [Fundamentos de objetos COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomaggobjectaddref"></a><a name="addref"></a>CComAggObject::AddRef

Incrementa el recuento de referencias en el objeto agregado.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a>CComAggObject::CComAggObject

El constructor.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
[en] El desconocido exterior.

### <a name="remarks"></a>Observaciones

Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained)e incrementa el recuento de bloqueos de módulo.

El destructor disminuye el recuento de bloqueos del módulo.

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a>CComAggObject::-CComAggObject

Destructor.

```
~CComAggObject();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados, llama a [FinalRelease](#finalrelease)y disminuye el recuento de bloqueos del módulo.

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a>CComAggObject::CreateInstance

Esta función estática permite crear un nuevo `contained` **>** objeto **de<CComAggObject** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parámetros

*Pp*<br/>
[fuera] Un puntero a un **\<CComAggObject**<em>contenía</em> **>** puntero. Si `CreateInstance` no se realiza correctamente, *pp* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El objeto devuelto tiene un recuento `AddRef` de referencias `Release` de cero, así que llame inmediatamente y, a continuación, utilícelo para liberar la referencia en el puntero de objeto cuando haya terminado.

Si no necesita acceso directo al objeto, pero aún desea crear `CoCreateInstance`un nuevo objeto sin la sobrecarga de , utilice [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a>CComAggObject::FinalConstruct

Llamado durante las fases finales de la construcción del objeto, este método realiza cualquier inicialización final en el [miembro m_contained.](#m_contained)

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a>CComAggObject::FinalRelease

Llamado durante la destrucción de objetos, este método libera el [m_contained](#m_contained) miembro.

```cpp
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a>CComAggObject::m_contained

Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*Contenido*<br/>
[en] La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

### <a name="remarks"></a>Observaciones

Todas `IUnknown` las `m_contained` llamadas a través se delegan en el desconocido externo.

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a>CComAggObject::QueryInterface

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

### <a name="remarks"></a>Observaciones

Si la interfaz solicitada es `IUnknown`, `QueryInterface` devuelve un `IUnknown` puntero al propio objeto agregado e incrementa el recuento de referencias. De lo contrario, este método `CComContainedObject` consulta la interfaz a través del miembro, [m_contained](#m_contained).

## <a name="ccomaggobjectrelease"></a><a name="release"></a>CComAggObject::Release

Disminuye el recuento de referencias en el objeto agregado.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas. En compilaciones que `Release` no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Vea también

[Clase CComObject](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject (Clase)](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
