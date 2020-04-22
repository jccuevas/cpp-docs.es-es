---
title: CComPolyObject (Clase)
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: c880d170a03196d0e15ea8741c786e560d90ddc4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747771"
---
# <a name="ccompolyobject-class"></a>CComPolyObject (Clase)

Esta clase `IUnknown` se implementa para un objeto agregado o no agregado.

## <a name="syntax"></a>Sintaxis

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parámetros

*Contenido*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|El constructor.|
|[CComPolyObject::-CCompolyObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Incrementa el recuento de referencias del objeto.|
|[CComPolyObject::CreateInstance](#createinstance)|(Estático) Permite crear un nuevo `contained` **>** objeto **de<CComPolyObject** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Realiza la inicialización final de `m_contained`.|
|[CComPolyObject::FinalRelease](#finalrelease)|Realiza la destrucción final de `m_contained`.|
|[CComPolyObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComPolyObject::Release](#release)|Disminuye el recuento de referencias del objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Delega las llamadas `IUnknown` al desconocido externo si `IUnknown` el objeto se agrega o al del objeto si el objeto no se agrega.|

## <a name="remarks"></a>Observaciones

`CComPolyObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto agregado o no agregado.

Cuando se `CComPolyObject` crea una instancia de, se comprueba el valor de la incógnita externa. Si es NULL, `IUnknown` se implementa para un objeto no agregado. Si el desconocido externo `IUnknown` no es NULL, se implementa para un objeto agregado.

La ventaja `CComPolyObject` de usar es que evita tener [CComAggObject](../../atl/reference/ccomaggobject-class.md) y [CComObject](../../atl/reference/ccomobject-class.md) en el módulo para controlar los casos agregados y no agregados. Un `CComPolyObject` solo objeto controla ambos casos. Esto significa que sólo una copia de la vtable y una copia de las funciones existen en el módulo. Si su vtable es grande, esto puede disminuir sustancialmente el tamaño del módulo. Sin embargo, si la `CComPolyObject` vtable es pequeña, el uso puede dar lugar a un tamaño de `CComAggObject` `CComObject`módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, tal como son y .

Si la macro DECLARE_POLY_AGGREGATABLE se especifica en la `CComPolyObject` definición de clase del objeto, se usará para crear el objeto. DECLARE_POLY_AGGREGATABLE se declarará automáticamente si usa el Asistente para proyectos ATL para crear un control completo o un control de Internet Explorer.

Si se agrega, el `CComPolyObject` `IUnknown`objeto tiene su propio `IUnknown`, independiente del objeto externo y mantiene su propio recuento de referencias. `CComPolyObject`utiliza [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) para delegar en el desconocido externo.

Para obtener más información acerca de la agregación, vea el artículo [Fundamentos de objetos COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a>CComPolyObject::AddRef

Incrementa el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CComPolyObject::CComPolyObject

El constructor.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*Pv*<br/>
[en] Un puntero al desconocido externo si se va a agregar el objeto, o NULL si el objeto si el objeto no se agrega.

### <a name="remarks"></a>Observaciones

Inicializa el `CComContainedObject` miembro de datos, [m_contained](#m_contained)e incrementa el recuento de bloqueos de módulo.

El destructor disminuye el recuento de bloqueos del módulo.

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a>CComPolyObject::-CCompolyObject

Destructor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados, llama a [FinalRelease](#finalrelease)y disminuye el recuento de bloqueos del módulo.

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPolyObject::CreateInstance

Permite crear un nuevo `contained` **>** objeto **de<CComPolyObject** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parámetros

*Pp*<br/>
[fuera] Un puntero a un **CComPolyObject puntero de<.** `contained` **>** Si `CreateInstance` no se realiza correctamente, *pp* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El objeto devuelto tiene un recuento `AddRef` de referencias `Release` de cero, así que llame inmediatamente y, a continuación, utilícelo para liberar la referencia en el puntero de objeto cuando haya terminado.

Si no necesita acceso directo al objeto, pero aún desea crear un `CoCreateInstance`nuevo objeto sin la sobrecarga de , utilice [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPolyObject::FinalConstruct

Llamado durante las fases finales de la construcción del objeto, este método realiza cualquier inicialización final en el [m_contained](#m_contained) miembro de datos.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPolyObject::FinalRelease

Llamado durante la destrucción de objetos, este método libera el [m_contained](#m_contained) miembro de datos.

```cpp
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a>CComPolyObject::m_contained

Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*Contenido*<br/>
[en] La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

### <a name="remarks"></a>Observaciones

`IUnknown`Las `m_contained` llamadas a través se delegan en el `IUnknown` desconocido externo si se agrega el objeto, o en el de este objeto si el objeto no se agrega.

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPolyObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parámetros

*Q*<br/>
La interfaz COM.

*Iid*<br/>
[en] Identificador de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *iid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

*Pp*<br/>
[fuera] Un puntero a la `__uuidof(Q)`interfaz identificada por .

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para un objeto agregado, si `IUnknown`la `QueryInterface` interfaz solicitada es , devuelve `IUnknown` un puntero al propio objeto agregado e incrementa el recuento de referencias. De lo contrario, este método `CComContainedObject` consulta la interfaz a través del miembro de datos, [m_contained](#m_contained).

## <a name="ccompolyobjectrelease"></a><a name="release"></a>CComPolyObject::Release

Disminuye el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas. En las compilaciones `Release` no de depuración, siempre devuelve 0.

## <a name="see-also"></a>Vea también

[Clase CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
