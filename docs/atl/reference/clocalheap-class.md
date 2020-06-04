---
title: Clase CLocalHeap
ms.date: 11/04/2016
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
ms.openlocfilehash: 303e3b85ad11c309f862f59d6ec610701c4ef6db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326756"
---
# <a name="clocalheap-class"></a>Clase CLocalHeap

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de montón local de Win32.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CLocalHeap::Asignar](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[CLocalHeap::Gratis](#free)|Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.|
|[CLocalHeap::GetSize](#getsize)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignado por este administrador de memoria.|
|[CLocalHeap::Reallocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|

## <a name="remarks"></a>Observaciones

`CLocalHeap`implementa funciones de asignación de memoria mediante las funciones de montón local de Win32.

> [!NOTE]
> Las funciones de montón local son más lentas que otras funciones de administración de memoria y no proporcionan tantas características. Por lo tanto, las nuevas aplicaciones deben utilizar las [funciones de montón.](/windows/win32/Memory/heap-functions) Están disponibles en la clase [CWin32Heap.](../../atl/reference/cwin32heap-class.md)

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem.h

## <a name="clocalheapallocate"></a><a name="allocate"></a>CLocalHeap::Asignar

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

Llame a [CLocalHeap::Free](#free) o [CLocalHeap::Reallocate](#reallocate) para liberar la memoria asignada por este método.

Implementado mediante [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) con un parámetro flag de LMEM_FIXED.

## <a name="clocalheapfree"></a><a name="free"></a>CLocalHeap::Gratis

Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.

### <a name="remarks"></a>Observaciones

Implementado mediante [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree).

## <a name="clocalheapgetsize"></a><a name="getsize"></a>CLocalHeap::GetSize

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

Implementado mediante [LocalSize](/windows/win32/api/winbase/nf-winbase-localsize).

## <a name="clocalheapreallocate"></a><a name="reallocate"></a>CLocalHeap::Reallocate

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

Llame a [CLocalHeap::Free](#free) para liberar la memoria asignada por este método.

Implementado mediante [LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Clase CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Clase CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Clase CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Clase IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
