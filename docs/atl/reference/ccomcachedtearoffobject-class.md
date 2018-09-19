---
title: CComCachedTearOffObject (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40dddf2bb1619bd896ecf50008f80fca968ef8c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075714"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject (clase)

Esta clase implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) para una interfaz desplazable.

## <a name="syntax"></a>Sintaxis

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parámetros

*contenidos*<br/>
Deriva de la clase desplazable, `CComTearOffObjectBase` y las interfaces desea que el objeto desplazable para admitir.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|El constructor.|
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Incrementa el recuento de referencias para un `CComCachedTearOffObject` objeto.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Las llamadas del `m_contained::FinalConstruct` (método de clase que desplazable).|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Las llamadas del `m_contained::FinalRelease` (método de clase que desplazable).|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Devuelve un puntero a la `IUnknown` de la `CComCachedTearOffObject` objeto, o a la interfaz solicitada en la clase desplazable (la clase `contained`).|
|[CComCachedTearOffObject::Release](#release)|Disminuye el recuento de referencias para un `CComCachedTearOffObject` de objeto y lo destruye si el recuento de referencias es 0.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Un `CComContainedObject` objeto derivado de la clase desplazable (la clase `contained`).|

## <a name="remarks"></a>Comentarios

`CComCachedTearOffObject` implementa [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) para una interfaz desplazable. Esta clase difiere `CComTearOffObject` que `CComCachedTearOffObject` tiene su propio `IUnknown`, independiente del objeto propietario de `IUnknown` (el propietario es el objeto para el que se crea el desplazable). `CComCachedTearOffObject` mantiene su propio el recuento de referencias en sus `IUnknown` y elimina a sí mismo una vez que su recuento de referencias es cero. Sin embargo, si una consulta para cualquiera de su desplazable interfaces, el recuento de referencias del objeto propietario `IUnknown` se incrementará.

Si el `CComCachedTearOffObject` objeto ya se crean instancias de implementar las tiras y la interfaz desplazable se consulta de nuevo, en el mismo `CComCachedTearOffObject` se vuelve a usar el objeto. En cambio, si implementa una interfaz divisible por un `CComTearOffObject` nuevo se consulta a través del objeto propietario, otro `CComTearOffObject` se creará una instancia.

Debe implementar la clase propietaria `FinalRelease` y llamada `Release` en la caché `IUnknown` para el `CComCachedTearOffObject`, lo que reducirá su recuento de referencias. Esto hará que `CComCachedTearOffObject`del `FinalRelease` para llamarse y eliminar el desplazable.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="addref"></a>  CComCachedTearOffObject::AddRef

Incrementa el recuento de referencias de la `CComCachedTearOffObject` objeto por 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para el diagnóstico y prueba.

##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject

El constructor.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parámetros

*PV*<br/>
[in] Puntero a la `IUnknown` de la `CComCachedTearOffObject`.

### <a name="remarks"></a>Comentarios

Inicializa el `CComContainedObject` miembro, [m_contained](#m_contained).

##  <a name="dtor"></a>  CComCachedTearOffObject:: ~ CComCachedTearOffObject

Destructor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados y llama a [FinalRelease](#finalrelease).

##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct

Las llamadas `m_contained::FinalConstruct` crear `m_contained`, el `CComContainedObject` <  `contained`> objeto utilizado para tener acceso a la interfaz implementada por la clase desplazable.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease

Las llamadas `m_contained::FinalRelease` para liberar `m_contained`, `CComContainedObject` <  `contained`> objeto.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained

Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de la clase desplazable.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parámetros

*contenidos*<br/>
[in] Deriva de la clase desplazable, `CComTearOffObjectBase` y las interfaces desea que el objeto desplazable para admitir.

### <a name="remarks"></a>Comentarios

Los métodos `m_contained` hereda se usan para tener acceso a la interfaz desplazable, en la clase desplazable a través de la caché desplazable del objeto `QueryInterface`, `FinalConstruct`, y `FinalRelease`.

##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*IID*<br/>
[in] El GUID de la interfaz que se solicita.

*ppvObject*<br/>
[out] Un puntero al puntero de interfaz identificado por *iid*, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si la interfaz solicitada es `IUnknown`, devuelve un puntero a la `CComCachedTearOffObject`del propio `IUnknown` e incrementa el recuento de referencias. En caso contrario, las consultas para la interfaz de la clase desplazable mediante el [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) método hereda `CComObjectRootEx`.  

##  <a name="release"></a>  CComCachedTearOffObject::Release

Disminuye el recuento de referencias en 1 y, si el recuento de referencias es 0, se elimina el `CComCachedTearOffObject` objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En versiones no depuradas, siempre devuelve 0. En las compilaciones de depuración, devuelve un valor que puede ser útil para el diagnóstico o de pruebas.

## <a name="see-also"></a>Vea también

[CComTearOffObject (clase)](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
