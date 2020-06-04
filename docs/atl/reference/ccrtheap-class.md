---
title: Clase CCRTHeap
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: caf5508079332689c2fff42f130951375dc35512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327162"
---
# <a name="ccrtheap-class"></a>Clase CCRTHeap

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de montón de CRT.

## <a name="syntax"></a>Sintaxis

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCRTHeap::Asignar](#allocate)|Llame a este método para asignar un bloque de memoria.|
|[CCRTHeap::Gratis](#free)|Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.|
|[CCRTHeap::GetSize](#getsize)|Llame a este método para obtener el tamaño asignado de un bloque de memoria asignado por este administrador de memoria.|
|[CCRTHeap::Reallocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|

## <a name="remarks"></a>Observaciones

`CCRTHeap`implementa funciones de asignación de memoria mediante las funciones de montón de CRT, incluidas [malloc](../../c-runtime-library/reference/malloc.md), [free](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md)y [_msize](../../c-runtime-library/reference/msize.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem.h

## <a name="ccrtheapallocate"></a><a name="allocate"></a>CCRTHeap::Asignar

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

Llame a [CCRTHeap::Free](#free) o [CCRTHeap::Reallocate](#reallocate) para liberar la memoria asignada por este método.

Implementado usando [malloc](../../c-runtime-library/reference/malloc.md).

## <a name="ccrtheapfree"></a><a name="free"></a>CCRTHeap::Gratis

Llame a este método para liberar un bloque de memoria asignado por este administrador de memoria.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.

### <a name="remarks"></a>Observaciones

Implementado usando [libre](../../c-runtime-library/reference/free.md).

## <a name="ccrtheapgetsize"></a><a name="getsize"></a>CCRTHeap::GetSize

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

Implementado mediante [_msize](../../c-runtime-library/reference/msize.md).

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a>CCRTHeap::Reallocate

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

Llame a [CCRTHeap::Free](#free) para liberar la memoria asignada por este método. Implementado usando [realloc](../../c-runtime-library/reference/realloc.md).

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Clase CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Clase CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Clase CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Clase IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
