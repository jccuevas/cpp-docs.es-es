---
title: Clase CComObjectNoLock
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: c190f495e284e98b27a6c6dc2099a8dfc4b1693d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327614"
---
# <a name="ccomobjectnolock-class"></a>Clase CComObjectNoLock

Esta clase `IUnknown` se implementa para un objeto no agregado, pero no incrementa el recuento de bloqueo de módulo en el constructor.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Parámetros

*Base*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Constructor.|
|[CComObjectNoLock::-CComObjectNoLock](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|Incrementa el recuento de referencias en el objeto.|
|[CComObjectNoLock::QueryInterface](#queryinterface)|Devuelve un puntero a la interfaz solicitada.|
|[CComObjectNoLock::Release](#release)|Disminuye el recuento de referencias en el objeto.|

## <a name="remarks"></a>Observaciones

`CComObjectNoLock`es similar a [CComObject](../../atl/reference/ccomobject-class.md) en que implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto no agregado; sin `CComObjectNoLock` embargo, no incrementa el recuento de bloqueo de módulo en el constructor.

ATL `CComObjectNoLock` utiliza internamente para fábricas de clases. En general, no usará esta clase directamente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a>CComObjectNoLock::AddRef

Incrementa el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>CComObjectNoLock::CComObjectNoLock

El constructor. A diferencia de [CComObject](../../atl/reference/ccomobject-class.md), no incrementa el recuento de bloqueos de módulo.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Parámetros

<em>void\*</em><br/>
[en] Este parámetro sin nombre no se utiliza. Existe para la simetría `CComXXXObjectXXX` con otros constructores.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CComObjectNoLock::-CComObjectNoLock

Destructor.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados y llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease).

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CComObjectNoLock::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] Identificador de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz identificado por *iid*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

## <a name="ccomobjectnolockrelease"></a><a name="release"></a>CComObjectNoLock::Release

Disminuye el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas. En compilaciones que `Release` no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
