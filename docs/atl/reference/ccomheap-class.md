---
title: Clase CComHeap
ms.date: 11/04/2016
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
ms.openlocfilehash: a38d1147e718870c03af84ec1487e226805b956e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327818"
---
# <a name="ccomheap-class"></a>Clase CComHeap

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de asignación de memoria COM.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComHeap::Asignar](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[CComHeap::Gratis](#free)|Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.|
|[CComHeap::GetSize](#getsize)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignado por este administrador de memoria.|
|[CComHeap::Reallocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|

## <a name="remarks"></a>Observaciones

`CComHeap`implementa funciones de asignación de memoria mediante las funciones de asignación COM, incluidas [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)y [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). La cantidad máxima de memoria que se puede asignar es igual a INT_MAX (2147483647) bytes.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLComMem.h

## <a name="ccomheapallocate"></a><a name="allocate"></a>CComHeap::Asignar

Llame a este método para asignar un bloque de memoria.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Observaciones

Llame a [CComHeap::Free](#free) o [CComHeap::Reallocate](#reallocate) para liberar la memoria asignada por este método.

Implementado mediante [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

## <a name="ccomheapfree"></a><a name="free"></a>CComHeap::Gratis

Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.

### <a name="remarks"></a>Observaciones

Implementado mediante [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

## <a name="ccomheapgetsize"></a><a name="getsize"></a>CComHeap::GetSize

Llame a este método para obtener el tamaño asignado de un bloque de memoria asignado por este administrador de memoria.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño del bloque de memoria asignado en bytes.

### <a name="remarks"></a>Observaciones

Implementado mediante [IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize).

## <a name="ccomheapreallocate"></a><a name="reallocate"></a>CComHeap::Reallocate

Llame a este método para reasignar la memoria asignada por este administrador de memoria.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Observaciones

Llame a [CComHeap::Free](#free) para liberar la memoria asignada por este método.

Implementado mediante [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Consulte también

[Ejemplo de DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Clase CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Clase CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Clase CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Clase IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
