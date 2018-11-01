---
title: CComPolyObject (clase)
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
ms.openlocfilehash: 9f84c022ac1dee34b6dca2931abb349eefb7d690
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495893"
---
# <a name="ccompolyobject-class"></a>CComPolyObject (clase)

Esta clase implementa `IUnknown` para un objeto agregado o no agregado.

## <a name="syntax"></a>Sintaxis

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parámetros

*contenidos*<br/>
La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|El constructor.|
|[CComPolyObject:: ~ CComPolyObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Incrementa el recuento de referencias del objeto.|
|[CComPolyObject::CreateInstance](#createinstance)|(Estático) Le permite crear un nuevo **CComPolyObject <** `contained` **>** objeto sin la sobrecarga de [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Realiza la inicialización final de `m_contained`.|
|[CComPolyObject::FinalRelease](#finalrelease)|Realiza la destrucción final de `m_contained`.|
|[CComPolyObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComPolyObject::Release](#release)|Reduce el recuento de referencia del objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Los delegados `IUnknown` llama al desconocido externo si el objeto es agregado o en la `IUnknown` del objeto si no se agrega el objeto.|

## <a name="remarks"></a>Comentarios

`CComPolyObject` implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) para un objeto agregado o no agregado.

Cuando una instancia de `CComPolyObject` creada, el valor de la externa desconocido está activada. Si es NULL, `IUnknown` se implementa para un objeto no agregado. Si no es NULL, el desconocido externo `IUnknown` se implementa para un objeto agregado.

La ventaja de usar `CComPolyObject` es que no tenga ambos [CComAggObject](../../atl/reference/ccomaggobject-class.md) y [CComObject](../../atl/reference/ccomobject-class.md) en el módulo para controlar los casos agregados y no agregados. Una sola `CComPolyObject` objeto administra ambos casos. Esto significa que existen solo una copia de la tabla vtable y una copia de las funciones del módulo. Si su tabla vtable es grande, puede reducir sustancialmente el tamaño del módulo. Sin embargo, si su tabla vtable es pequeña, usando `CComPolyObject` puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no agregado, como son `CComAggObject` y `CComObject`.

Si la macro DECLARE_POLY_AGGREGATABLE se especifica en la definición de clase del objeto, `CComPolyObject` se usará para crear el objeto. Automáticamente se declarará DECLARE_POLY_AGGREGATABLE si usa al Asistente para proyectos ATL para crear un control total o un control de Internet Explorer.

Si se agregan, el `CComPolyObject` objeto tiene su propio `IUnknown`independiente desde el objeto externo `IUnknown`y mantiene su propio número de referencias. `CComPolyObject` usa [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) delegar en el desconocido externo.

Para obtener más información acerca de la agregación, vea el artículo [aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="addref"></a>  CComPolyObject::AddRef

Incrementa el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para el diagnóstico o de pruebas.

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

El constructor.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
[in] Un puntero para el desconocido externo si el objeto es para agregarse o NULL si el objeto si no se agrega el objeto.

### <a name="remarks"></a>Comentarios

Inicializa el `CComContainedObject` miembro de datos, [m_contained](#m_contained)e incrementa el recuento de bloqueos del módulo.

El destructor disminuye el módulo recuento de bloqueos.

##  <a name="dtor"></a>  CComPolyObject:: ~ CComPolyObject

Destructor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados, llamadas [FinalRelease](#finalrelease), y reduce el módulo recuento de bloqueos.

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

Le permite crear un nuevo **CComPolyObject <** `contained` **>** objeto sin la sobrecarga de [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parámetros

*perfil de puerto*<br/>
[out] Un puntero a un **CComPolyObject <** `contained` **>** puntero. Si `CreateInstance` es incorrecta, *pp* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El objeto devuelto tiene un recuento de referencias de cero, puede llamarlo `AddRef` inmediatamente, use `Release` para liberar la referencia en el puntero de objeto cuando haya terminado.

Si no necesita acceso directo a los objetos, pero todavía desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, utilice [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

Se llama durante la fase final de la construcción de objetos, este método realiza cualquier inicialización final en el [m_contained](#m_contained) miembro de datos.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

Se llama durante la destrucción de objetos, este método libera el [m_contained](#m_contained) miembro de datos.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*contenidos*<br/>
[in] La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir en el objeto.

### <a name="remarks"></a>Comentarios

`IUnknown` llama a través de `m_contained` se delegan al desconocido externo si el objeto es agregado, así como la `IUnknown` de este objeto si el objeto no se ha agregado.

##  <a name="queryinterface"></a>  CComPolyObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parámetros

*Q*<br/>
La interfaz COM.

*IID*<br/>
[in] El identificador de la interfaz que se solicita.

*ppvObject*<br/>
[out] Un puntero al puntero de interfaz identificado por *iid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

*perfil de puerto*<br/>
[out] Un puntero a la interfaz identificada por `__uuidof(Q)`.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Para un objeto agregado, si la interfaz solicitada es `IUnknown`, `QueryInterface` devuelve un puntero para el objeto agregado propio `IUnknown` e incrementa el recuento de referencias. En caso contrario, este método consulta para la interfaz a través de la `CComContainedObject` miembro de datos, [m_contained](#m_contained).

##  <a name="release"></a>  CComPolyObject::Release

Disminuye el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En las compilaciones de depuración, `Release` devuelve un valor que puede ser útil para el diagnóstico o de pruebas. En las compilaciones de nondebug `Release` siempre devuelve 0.

## <a name="see-also"></a>Vea también

[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
