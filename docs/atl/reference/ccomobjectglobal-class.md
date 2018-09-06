---
title: CComObjectGlobal (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
dev_langs:
- C++
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4198e08a4c126a180006a088d4fc1509643824f6
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764935"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal (clase)

Esta clase administra un recuento de referencias en el módulo que contiene su `Base` objeto.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Parámetros

*base*  
La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir de cualquier otra interfaz que desea admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|El constructor.|
|[CComObjectGlobal:: ~ CComObjectGlobal](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|Implementa una global `AddRef`.|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementa una global `QueryInterface`.|
|[CComObjectGlobal::Release](#release)|Implementa una global `Release`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Contiene el HRESULT devuelto durante la construcción de la `CComObjectGlobal` objeto.|

## <a name="remarks"></a>Comentarios

`CComObjectGlobal` administra un recuento de referencias en el módulo que contiene su `Base` objeto. `CComObjectGlobal` garantiza que no se eliminará el objeto siempre que el módulo no se libera. Cuando el recuento de referencias en todo el módulo llega a cero, solo se quitará el objeto.

Por ejemplo, mediante `CComObjectGlobal`, un generador de clases puede contener un objeto global común compartida por todos sus clientes.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="addref"></a>  CComObjectGlobal::AddRef

Incrementa el recuento de referencias del objeto en 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para el diagnóstico y prueba.

### <a name="remarks"></a>Comentarios

De forma predeterminada, `AddRef` llamadas `_Module::Lock`, donde `_Module` es la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de él.

##  <a name="ccomobjectglobal"></a>  CComObjectGlobal::CComObjectGlobal

El constructor. Las llamadas `FinalConstruct` y, a continuación, establece [m_hResFinalConstruct](#m_hresfinalconstruct) a la `HRESULT` devuelto por `FinalConstruct`.

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Comentarios

Si no se ha derivado la clase base desde [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md), debe proporcionar su propia `FinalConstruct` método. El destructor llama a `FinalRelease`.

##  <a name="dtor"></a>  CComObjectGlobal:: ~ CComObjectGlobal

Destructor.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados y llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="m_hresfinalconstruct"></a>  CComObjectGlobal::m_hResFinalConstruct

Contiene el valor HRESULT de llamar a `FinalConstruct` durante la construcción de la `CComObjectGlobal` objeto.

```
HRESULT m_hResFinalConstruct;
```

##  <a name="queryinterface"></a>  CComObjectGlobal::QueryInterface

Recupera un puntero al puntero de interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*IID*  
[in] El GUID de la interfaz que se solicita.

*ppvObject*  
[out] Un puntero al puntero de interfaz identificado por el iid, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

`QueryInterface` solo administra interfaces de la tabla de asignación COM.

##  <a name="release"></a>  CComObjectGlobal::Release

Disminuye el recuento de referencias del objeto en 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En las compilaciones de depuración, `Release` devuelve un valor que puede ser útil para el diagnóstico y prueba. En versiones no depuradas, `Release` siempre devuelve 0.

### <a name="remarks"></a>Comentarios

De forma predeterminada, `Release` llamadas `_Module::Unlock`, donde `_Module` es la instancia global de [CComModule](../../atl/reference/ccommodule-class.md) o una clase derivada de él.

## <a name="see-also"></a>Vea también

[CComObjectStack (clase)](../../atl/reference/ccomobjectstack-class.md)   
[CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)   
[CComObject (clase)](../../atl/reference/ccomobject-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)
