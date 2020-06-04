---
title: Clase CComObjectStack
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: 8c3fd56635da8b80c84f6151009586b7bd2b4341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327573"
---
# <a name="ccomobjectstack-class"></a>Clase CComObjectStack

Esta clase crea un objeto COM temporal y `IUnknown`le proporciona una implementación esquelética de .

## <a name="syntax"></a>Sintaxis

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|El constructor.|
|[CComObjectStack::-CComObjectStack](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|Devuelve cero. En el modo `_ASSERTE`de depuración, llama a .|
|[CComObjectStack::QueryInterface](#queryinterface)|Devuelve E_NOINTERFACE. En el modo `_ASSERTE`de depuración, llama a .|
|[CComObjectStack::Release](#release)|Devuelve cero. En el modo `_ASSERTE`de depuración, llama a . ~|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Contiene el HRESULT devuelto `CComObjectStack` durante la construcción del objeto.|

## <a name="remarks"></a>Observaciones

`CComObjectStack`se utiliza para crear un objeto COM temporal y `IUnknown`proporcionar al objeto una implementación esquelética de . Normalmente, el objeto se utiliza como una variable local dentro de una función (es decir, insertado en la pila). Puesto que el objeto se destruye cuando finaliza la función, no se realiza el recuento de referencias para aumentar la eficiencia.

En el ejemplo siguiente se muestra cómo crear un objeto COM utilizado dentro de una función:

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

El objeto `Tempobj` temporal se inserta en la pila y desaparece automáticamente cuando finaliza la función.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComObjectStack`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomobjectstackaddref"></a><a name="addref"></a>CComObjectStack::AddRef

Devuelve cero.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Devuelve cero.

### <a name="remarks"></a>Observaciones

En el modo `_ASSERTE`de depuración, llama a .

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack

El constructor.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Observaciones

Llama `FinalConstruct` y, [m_hResFinalConstruct](#m_hresfinalconstruct) a continuación, establece `FinalConstruct`m_hResFinalConstruct en el HRESULT devuelto por . Si no ha derivado la clase base de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), debe proporcionar su propio `FinalConstruct` método. El destructor llama a `FinalRelease`.

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a>CComObjectStack::-CComObjectStack

Destructor.

```
CComObjectStack();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados y llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct

Contiene el HRESULT `FinalConstruct` devuelto al `CComObjectStack` llamar durante la construcción del objeto.

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a>CComObjectStack::QueryInterface

Devuelve E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOINTERFACE.

### <a name="remarks"></a>Observaciones

En el modo `_ASSERTE`de depuración, llama a .

## <a name="ccomobjectstackrelease"></a><a name="release"></a>CComObjectStack::Release

Devuelve cero.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

Devuelve cero.

### <a name="remarks"></a>Observaciones

En el modo `_ASSERTE`de depuración, llama a .

## <a name="see-also"></a>Consulte también

[Clase CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Clase CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Clase CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
