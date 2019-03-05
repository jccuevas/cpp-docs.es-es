---
title: CLocalHeap (clase)
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
ms.openlocfilehash: 53288bea8a50f62437eab4dd81d5d816abf78f44
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283090"
---
# <a name="clocalheap-class"></a>CLocalHeap (clase)

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones del montón local de Win32.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CLocalHeap::Allocate](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[CLocalHeap::Free](#free)|Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.|
|[CLocalHeap::GetSize](#getsize)|Llame a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.|
|[CLocalHeap::Reallocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|

## <a name="remarks"></a>Comentarios

`CLocalHeap` implementa funciones de asignación de memoria mediante las funciones del montón local de Win32.

> [!NOTE]
>  Las funciones del montón local son más lentas que otras funciones de administración de memoria y no proporcionan tantas características. Por lo tanto, las aplicaciones nuevas deben usar el [funciones de montón](/windows/desktop/Memory/heap-functions). Están disponibles en el [CWin32Heap](../../atl/reference/cwin32heap-class.md) clase.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem.h

##  <a name="allocate"></a>  CLocalHeap::Allocate

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

Llame a [clocalheap:: Free](#free) o [clocalheap:: ReAllocate](#reallocate) para liberar la memoria asignada por este método.

Implementa mediante [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) con un parámetro de marca de LMEM_FIXED.

##  <a name="free"></a>  CLocalHeap::Free

Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.

### <a name="remarks"></a>Comentarios

Implementa mediante [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree).

##  <a name="getsize"></a>  CLocalHeap::GetSize

Llame a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño del bloque de memoria asignada en bytes.

### <a name="remarks"></a>Comentarios

Implementa mediante [LocalSize](/windows/desktop/api/winbase/nf-winbase-localsize).

##  <a name="reallocate"></a>  CLocalHeap::Reallocate

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

Llame a [clocalheap:: Free](#free) para liberar la memoria asignada por este método.

Implementa mediante [LocalReAlloc](/windows/desktop/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[CComHeap (clase)](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Heap (clase)](../../atl/reference/cwin32heap-class.md)<br/>
[CGlobalHeap (clase)](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap (clase)](../../atl/reference/ccrtheap-class.md)<br/>
[IAtlMemMgr (clase)](../../atl/reference/iatlmemmgr-class.md)
