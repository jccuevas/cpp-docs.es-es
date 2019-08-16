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
ms.openlocfilehash: 1ded73047b895a44a22bdd5730886f7fc088c77a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497343"
---
# <a name="ccomheap-class"></a>Clase CComHeap

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) con las funciones de asignación de memoria de com.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComHeap::Allocate](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[CComHeap::Free](#free)|Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.|
|[CComHeap::GetSize](#getsize)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignado por este administrador de memoria.|
|[CComHeap::Reallocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|

## <a name="remarks"></a>Comentarios

`CComHeap`implementa funciones de asignación de memoria mediante las funciones de asignación COM, como [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [IMalloc::](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize) [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). La cantidad máxima de memoria que se puede asignar es igual a INT_MAX (2147483647) bytes.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Requisitos

**Encabezado**: ATLComMem.h

##  <a name="allocate"></a>  CComHeap::Allocate

Llame a este método para asignar un bloque de memoria.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Llame a [CComHeap:: Free](#free) o [CComHeap::](#reallocate) allocate para liberar la memoria asignada por este método.

Implementado mediante [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

##  <a name="free"></a>  CComHeap::Free

Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.

### <a name="remarks"></a>Comentarios

Se implementa mediante [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

##  <a name="getsize"></a>  CComHeap::GetSize

Llame a este método para obtener el tamaño asignado de un bloque de memoria asignado por este administrador de memoria.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño del bloque de memoria asignado en bytes.

### <a name="remarks"></a>Comentarios

Se implementa mediante [IMalloc:: se obtiene](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize).

##  <a name="reallocate"></a>  CComHeap::Reallocate

Llame a este método para reasignar la memoria asignada por este administrador de memoria.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Llame a [CComHeap:: Free](#free) para liberar la memoria asignada por este método.

Implementado mediante [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Vea también

[Ejemplo de DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[CWin32Heap (clase)](../../atl/reference/cwin32heap-class.md)<br/>
[CLocalHeap (clase)](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap (clase)](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap (clase)](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr (clase)](../../atl/reference/iatlmemmgr-class.md)
