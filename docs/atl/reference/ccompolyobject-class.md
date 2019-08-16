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
ms.openlocfilehash: deed29b5fb80ea8bbd06b3d50f45e38740b1619f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497149"
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

*contained*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|El constructor.|
|[CComPolyObject::~CComPolyObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Incrementa el recuento de referencias del objeto.|
|[CComPolyObject::CreateInstance](#createinstance)|Estático Permite crear un nuevo objeto **CComPolyObject <** `contained` **>** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Realiza la inicialización `m_contained`final de.|
|[CComPolyObject::FinalRelease](#finalrelease)|Realiza la destrucción final `m_contained`de.|
|[CComPolyObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComPolyObject::Release](#release)|Disminuye el recuento de referencias del objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Delega `IUnknown` las llamadas a la desconocida externa si el objeto se agrega o `IUnknown` al del objeto si no se agrega el objeto.|

## <a name="remarks"></a>Comentarios

`CComPolyObject`implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto agregado o no agregado.

Cuando se crea una `CComPolyObject` instancia de, se comprueba el valor de la desconocida externa. Si es null, `IUnknown` se implementa para un objeto no agregado. Si el desconocido externo no es null, `IUnknown` se implementa para un objeto agregado.

La ventaja de usar `CComPolyObject` es que evita tener [CComAggObject](../../atl/reference/ccomaggobject-class.md) y [CComObject](../../atl/reference/ccomobject-class.md) en el módulo para controlar los casos agregados y no agregados. Un solo `CComPolyObject` objeto controla ambos casos. Esto significa que solo hay una copia de la tabla vtable y una copia de las funciones en el módulo. Si su vtable es grande, esto puede reducir considerablemente el tamaño del módulo. Sin embargo, si la tabla vtable es pequeña `CComPolyObject` , el uso de puede dar lugar a un tamaño de módulo ligeramente mayor porque no está optimizado para un objeto agregado o no `CComAggObject` agregado `CComObject`, como son y.

Si se especifica la macro DECLARE_POLY_AGGREGATABLE en la definición de clase del objeto `CComPolyObject` , se usará para crear el objeto. DECLARE_POLY_AGGREGATABLE se declarará automáticamente si utiliza el Asistente para proyectos ATL para crear un control total o un control de Internet Explorer.

Si se agrega, el `CComPolyObject` objeto tiene su propio `IUnknown`, independiente de los del `IUnknown`objeto externo y mantiene su propio recuento de referencias. `CComPolyObject`usa [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) para delegar en el desconocido externo.

Para obtener más información acerca de la agregación, vea el artículo [fundamentos de objetos COM ATL](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="addref"></a>  CComPolyObject::AddRef

Incrementa el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

##  <a name="ccompolyobject"></a>  CComPolyObject::CComPolyObject

El constructor.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*pv*<br/>
de Puntero al externo desconocido si se va a agregar el objeto, o NULL si el objeto no se ha agregado.

### <a name="remarks"></a>Comentarios

Inicializa el `CComContainedObject` miembro de datos, [m_contained](#m_contained)e incrementa el recuento de bloqueos del módulo.

El destructor reduce el número de bloqueos del módulo.

##  <a name="dtor"></a>  CComPolyObject::~CComPolyObject

Destructor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados, llama a [FinalRelease](#finalrelease)y disminuye el recuento de bloqueos del módulo.

##  <a name="createinstance"></a>  CComPolyObject::CreateInstance

Permite crear un nuevo objeto **CComPolyObject <** `contained` **>** sin la sobrecarga de [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parámetros

*pp*<br/>
enuncia Puntero a un puntero de **<** `contained` **>** CComPolyObject. Si `CreateInstance` no se realiza correctamente, *PP* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El objeto devuelto tiene un recuento de referencias de cero `AddRef` , por lo que `Release` debe llamar a inmediatamente y después usar para liberar la referencia en el puntero de objeto cuando haya terminado.

Si no necesita acceso directo al objeto, pero aún desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, use [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.

##  <a name="finalconstruct"></a>  CComPolyObject::FinalConstruct

Se llama durante la fase final de la construcción de un objeto, este método realiza cualquier inicialización final en el miembro de datos [m_contained](#m_contained) .

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="finalrelease"></a>  CComPolyObject::FinalRelease

Se llama durante la destrucción del objeto, este método libera el miembro de datos [m_contained](#m_contained) .

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComPolyObject::m_contained

Objeto [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) derivado de la clase.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*contained*<br/>
de La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

### <a name="remarks"></a>Comentarios

`IUnknown`las llamadas `m_contained` a través de se delegan al desconocido externo si el objeto se agrega, o `IUnknown` al de este objeto si no se agrega el objeto.

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

*iid*<br/>
de Identificador de la interfaz que se solicita.

*ppvObject*<br/>
enuncia Puntero al puntero de interfaz identificado por *IID*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

*pp*<br/>
enuncia Puntero a la interfaz identificada por `__uuidof(Q)`.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Para un objeto agregado, si la interfaz solicitada es `IUnknown`, `QueryInterface` devuelve un puntero al propio `IUnknown` objeto agregado y aumenta el recuento de referencias. De lo contrario, este método consulta la interfaz a `CComContainedObject` través del miembro de datos, [m_contained](#m_contained).

##  <a name="release"></a>  CComPolyObject::Release

Disminuye el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas. En las compilaciones `Release` que no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Vea también

[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
