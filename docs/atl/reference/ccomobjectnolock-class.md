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
ms.openlocfilehash: 9253c7495f4d13ed6ce609988251d8abd09592ad
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497033"
---
# <a name="ccomobjectnolock-class"></a>Clase CComObjectNoLock

Esta clase implementa `IUnknown` para un objeto no agregado, pero no incrementa el recuento de bloqueos del módulo en el constructor.

## <a name="syntax"></a>Sintaxis

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Parámetros

*Básica*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir en el objeto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Constructor.|
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|Incrementa el recuento de referencias en el objeto.|
|[CComObjectNoLock::QueryInterface](#queryinterface)|Devuelve un puntero a la interfaz solicitada.|
|[CComObjectNoLock::Release](#release)|Disminuye el recuento de referencias en el objeto.|

## <a name="remarks"></a>Comentarios

`CComObjectNoLock`es similar a [CComObject](../../atl/reference/ccomobject-class.md) en que implementa [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) para un objeto no agregado; sin embargo `CComObjectNoLock` , no incrementa el recuento de bloqueos del módulo en el constructor.

ATL usa `CComObjectNoLock` internamente para los generadores de clases. En general, no usará esta clase directamente.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="addref"></a>  CComObjectNoLock::AddRef

Incrementa el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Valor devuelto

Un valor que puede ser útil para diagnósticos o pruebas.

##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock

El constructor. A diferencia de [CComObject](../../atl/reference/ccomobject-class.md), no incrementa el recuento de bloqueos del módulo.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Parámetros

<em>void\*</em><br/>
de No se usa este parámetro sin nombre. Existe para la simetría con otros `CComXXXObjectXXX` constructores.

##  <a name="dtor"></a>  CComObjectNoLock::~CComObjectNoLock

Destructor.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados y llama a [FinalRelease](ccomobjectrootex-class.md#finalrelease).

##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface

Recupera un puntero a la interfaz solicitada.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*iid*<br/>
de Identificador de la interfaz que se solicita.

*ppvObject*<br/>
enuncia Puntero al puntero de interfaz identificado por *IID*. Si el objeto no admite esta interfaz, *ppvObject* se establece en NULL.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

##  <a name="release"></a>  CComObjectNoLock::Release

Disminuye el recuento de referencias en el objeto.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Valor devuelto

En compilaciones `Release` de depuración, devuelve un valor que puede ser útil para diagnósticos o pruebas. En las compilaciones que `Release` no son de depuración, siempre devuelve 0.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)
