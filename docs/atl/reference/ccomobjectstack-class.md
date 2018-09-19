---
title: CComObjectStack (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 277951a5425a75c9769c5a2c4104421303f677c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46065346"
---
# <a name="ccomobjectstack-class"></a>CComObjectStack (clase)

Esta clase crea un objeto COM temporal y le proporciona una implementación básica de `IUnknown`.

## <a name="syntax"></a>Sintaxis

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Parámetros

*base*<br/>
La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir de cualquier otra interfaz que desea admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|El constructor.|
|[CComObjectStack:: ~ CComObjectStack](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|Devuelve cero. En modo de depuración, las llamadas `_ASSERTE`.|
|[CComObjectStack::QueryInterface](#queryinterface)|Devuelve E_NOINTERFACE. En modo de depuración, las llamadas `_ASSERTE`.|
|[CComObjectStack::Release](#release)|Devuelve cero. En modo de depuración, las llamadas `_ASSERTE`. ~|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Contiene el HRESULT devuelto durante la construcción de la `CComObjectStack` objeto.|

## <a name="remarks"></a>Comentarios

`CComObjectStack` se usa para crear un objeto COM temporal y proporcionar el objeto de una implementación básica de `IUnknown`. Normalmente, el objeto se usa como una variable local dentro de una función (que es, se inserta en la pila). Puesto que el objeto se destruye cuando finaliza la función, el recuento de referencias no se realiza para aumentar la eficacia.

El ejemplo siguiente muestra cómo crear un objeto COM utilizado dentro de una función:

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

El objeto temporal `Tempobj` se inserta en la pila y desaparece automáticamente cuando finaliza la función.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComObjectStack`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="addref"></a>  CComObjectStack::AddRef

Devuelve cero.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Devuelve cero.

### <a name="remarks"></a>Comentarios

En modo de depuración, las llamadas `_ASSERTE`.

##  <a name="ccomobjectstack"></a>  CComObjectStack::CComObjectStack

El constructor.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Comentarios

Las llamadas `FinalConstruct` y, a continuación, establece [m_hResFinalConstruct](#m_hresfinalconstruct) el HRESULT devuelto por `FinalConstruct`. Si no se ha derivado la clase base desde [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), debe proporcionar su propia `FinalConstruct` método. El destructor llama a `FinalRelease`.

##  <a name="dtor"></a>  CComObjectStack:: ~ CComObjectStack

Destructor.

```
CComObjectStack();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados y llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="m_hresfinalconstruct"></a>  CComObjectStack::m_hResFinalConstruct

Contiene el HRESULT devuelto desde la llamada `FinalConstruct` durante la construcción de la `CComObjectStack` objeto.

```
HRESULT    m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectStack::QueryInterface

Devuelve E_NOINTERFACE.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Valor devuelto

Devuelve E_NOINTERFACE.

### <a name="remarks"></a>Comentarios

En modo de depuración, las llamadas `_ASSERTE`.

##  <a name="release"></a>  CComObjectStack::Release

Devuelve cero.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

Devuelve cero.

### <a name="remarks"></a>Comentarios

En modo de depuración, las llamadas `_ASSERTE`.

## <a name="see-also"></a>Vea también

[CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject (clase)](../../atl/reference/ccomobject-class.md)<br/>
[CComObjectGlobal (clase)](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
