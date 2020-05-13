---
title: Clase CComObjectGlobal
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: 9a784584179186cdf1e63c1ec43cad4d59391ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327633"
---
# <a name="ccomobjectglobal-class"></a>Clase CComObjectGlobal

Esta clase administra un recuento de `Base` referencias en el módulo que contiene el objeto.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|El constructor.|
|[CComObjectGlobal::-CComObjectGlobal](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|Implementa un `AddRef`archivo .|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementa un `QueryInterface`archivo .|
|[CComObjectGlobal::Release](#release)|Implementa un `Release`archivo .|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Contiene el HRESULT devuelto `CComObjectGlobal` durante la construcción del objeto.|

## <a name="remarks"></a>Observaciones

`CComObjectGlobal`administra un recuento de referencias `Base` en el módulo que contiene el objeto. `CComObjectGlobal`garantiza que el objeto no se eliminará mientras el módulo no se libere. El objeto solo se eliminará cuando el recuento de referencias de todo el módulo vaya a cero.

Por ejemplo, `CComObjectGlobal`el uso de , un generador de clases puede contener un objeto global común que es compartido por todos sus clientes.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a>CComObjectGlobal::AddRef

Incrementa el recuento de referencias del objeto en 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos y pruebas.

### <a name="remarks"></a>Observaciones

De forma `AddRef` `_Module::Lock`predeterminada, `_Module` llama a , donde está la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de ella.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal

El constructor. Llama `FinalConstruct` y, a `HRESULT` continuación, `FinalConstruct`establece [m_hResFinalConstruct](#m_hresfinalconstruct) en el devuelto por .

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Observaciones

Si no ha derivado la clase base de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), debe proporcionar su propio `FinalConstruct` método. El destructor llama a `FinalRelease`.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a>CComObjectGlobal::-CComObjectGlobal

Destructor.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados y llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct

Contiene el HRESULT `FinalConstruct` de llamar `CComObjectGlobal` durante la construcción del objeto.

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a>CComObjectGlobal::QueryInterface

Recupera un puntero al puntero de interfaz solicitado.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] GUID de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz identificado por iid, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

`QueryInterface` solo administra interfaces de la tabla de asignación COM.

## <a name="ccomobjectglobalrelease"></a><a name="release"></a>CComObjectGlobal::Release

Disminuye el recuento de referencias del objeto en 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos y pruebas. En compilaciones que `Release` no son de depuración, siempre devuelve 0.

### <a name="remarks"></a>Observaciones

De forma `Release` `_Module::Unlock`predeterminada, `_Module` llama a , donde está la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de ella.

## <a name="see-also"></a>Consulte también

[Clase CComObjectStack](../../atl/reference/ccomobjectstack-class.md)<br/>
[Clase CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Clase CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
