---
title: CComAggObject (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ffe21526dd106ad067c68da49d6b07bb9e50cf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039834"
---
# <a name="ccomaggobject-class"></a>CComAggObject (clase)

Esta clase implementa la [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) interfaz para un objeto agregado. Por definición, un objeto agregado está dentro de un objeto externo. El `CComAggObject` clase es similar a la [CComObject (clase)](../../atl/reference/ccomobject-class.md), salvo que expone una interfaz que es accesible directamente a los clientes externos.

## <a name="syntax"></a>Sintaxis

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parámetros

*contenidos*<br/>
La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|El constructor.|
|[CComAggObject:: ~ CComAggObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Incrementa el recuento de referencias en el objeto agregado.|
|[CComAggObject::CreateInstance](#createinstance)|Esta función estática le permite crear un nuevo **CComAggObject <** `contained` **>** objeto sin la sobrecarga de [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Realiza la inicialización final de `m_contained`.|
|[CComAggObject::FinalRelease](#finalrelease)|Realiza la destrucción final de `m_contained`.|
|[CComAggObject::QueryInterface](#queryinterface)|Recupera un puntero a la interfaz solicitada.|
|[CComAggObject::Release](#release)|Disminuye el recuento de referencias en el objeto agregado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Los delegados `IUnknown` las llamadas al desconocido externo.|

## <a name="remarks"></a>Comentarios

`CComAggObject` implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) para un objeto agregado. `CComAggObject` tiene su propio `IUnknown` interfaz, de forma independiente desde el objeto externo `IUnknown` interfaz y mantiene su propio número de referencias.

Para obtener más información acerca de la agregación, vea el artículo [aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="addref"></a>  CComAggObject::AddRef

Incrementa el recuento de referencias en el objeto agregado.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para el diagnóstico o de pruebas.

##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject

El constructor.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
[in] El desconocido externo.

### <a name="remarks"></a>Comentarios

Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained)e incrementa el recuento de bloqueos del módulo.

El destructor disminuye el módulo recuento de bloqueos.

##  <a name="dtor"></a>  CComAggObject:: ~ CComAggObject

Destructor.

```
~CComAggObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados, llamadas [FinalRelease](#finalrelease), y reduce el módulo recuento de bloqueos.

##  <a name="createinstance"></a>  CComAggObject::CreateInstance

Esta función estática le permite crear un nuevo **CComAggObject <** `contained` **>** objeto sin la sobrecarga de [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parámetros

*perfil de puerto*<br/>
[out] Un puntero a un **CComAggObject\<**<em>contenidos</em> **>** puntero. Si `CreateInstance` es incorrecta, *pp* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El objeto devuelto tiene un recuento de referencias de cero, puede llamarlo `AddRef` inmediatamente, use `Release` para liberar la referencia en el puntero de objeto cuando haya terminado.

Si no necesita acceso directo a los objetos, pero todavía desea crear un nuevo objeto sin la sobrecarga de `CoCreateInstance`, utilice [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) en su lugar.

##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct

Se llama durante la fase final de la construcción de objetos, este método realiza cualquier inicialización final en el [m_contained](#m_contained) miembro.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="finalrelease"></a>  CComAggObject::FinalRelease

Se llama durante la destrucción de objetos, este método libera el [m_contained](#m_contained) miembro.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComAggObject::m_contained

Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*contenidos*<br/>
[in] La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir en el objeto.

### <a name="remarks"></a>Comentarios

Todos los `IUnknown` llama a través de `m_contained` se delegan al desconocido externo.

##  <a name="queryinterface"></a>  CComAggObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parámetros

*IID*<br/>
[in] El identificador de la interfaz que se solicita.

*ppvObject*<br/>
[out] Un puntero al puntero de interfaz identificado por *iid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

*perfil de puerto*<br/>
[out] Un puntero al puntero de interfaz identificado por tipo `Q`. Si el objeto no admite esta interfaz, *pp* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si la interfaz solicitada es `IUnknown`, `QueryInterface` devuelve un puntero para el objeto agregado propio `IUnknown` e incrementa el recuento de referencias. En caso contrario, este método consulta para la interfaz a través de la `CComContainedObject` miembro, [m_contained](#m_contained).

##  <a name="release"></a>  CComAggObject::Release

Disminuye el recuento de referencias en el objeto agregado.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En las compilaciones de depuración, `Release` devuelve un valor que puede ser útil para el diagnóstico o de pruebas. En versiones no depuradas, `Release` siempre devuelve 0.

## <a name="see-also"></a>Vea también

[CComObject (clase)](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject (clase)](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
