---
title: Clase CGlobalHeap
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: d596fd51c1bf33f606c1f14c9e8dbd2f1926c7f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326941"
---
# <a name="cglobalheap-class"></a>Clase CGlobalHeap

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de montón global de Win32.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CGlobalHeap::Asignar](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[CGlobalHeap::Gratis](#free)|Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.|
|[CGlobalHeap::GetSize](#getsize)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignado por este administrador de memoria.|
|[CGlobalHeap::Reallocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|

## <a name="remarks"></a>Observaciones

`CGlobalHeap`implementa funciones de asignación de memoria mediante las funciones de montón global de Win32.

> [!NOTE]
> Las funciones de montón global son más lentas que otras funciones de administración de memoria y no proporcionan tantas características. Por lo tanto, las nuevas aplicaciones deben utilizar las [funciones de montón.](/windows/win32/Memory/heap-functions) Están disponibles en la clase [CWin32Heap.](../../atl/reference/cwin32heap-class.md) DDE y las funciones del portapapeles siguen utilizando las funciones globales.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem.h

## <a name="cglobalheapallocate"></a><a name="allocate"></a>CGlobalHeap::Asignar

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

Llame a [CGlobalHeap::Free](#free) o [CGlobalHeap::Reallocate](#reallocate) para liberar la memoria asignada por este método.

Se implementa mediante [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) con un parámetro flag de GMEM_FIXED.

## <a name="cglobalheapfree"></a><a name="free"></a>CGlobalHeap::Gratis

Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.

### <a name="remarks"></a>Observaciones

Implementado mediante [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree).

## <a name="cglobalheapgetsize"></a><a name="getsize"></a>CGlobalHeap::GetSize

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

Implementado mediante [GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize).

## <a name="cglobalheapreallocate"></a><a name="reallocate"></a>CGlobalHeap::Reallocate

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

Llame a [CGlobalHeap::Free](#free) para liberar la memoria asignada por este método.

Implementado mediante [GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Clase CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Clase CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Clase CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Clase IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
