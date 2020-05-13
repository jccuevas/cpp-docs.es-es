---
title: Clase CCRTAllocator
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: 2f6bae3818fa0f1639e0e3cee4e09121580da768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327180"
---
# <a name="ccrtallocator-class"></a>Clase CCRTAllocator

Esta clase proporciona métodos para administrar la memoria mediante rutinas de memoria CRT.

## <a name="syntax"></a>Sintaxis

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CCRTAllocator::Asignar](#allocate)|(Estático) Llame a este método para asignar memoria.|
|[CCRTAllocator::Gratis](#free)|(Estático) Llame a este método para liberar memoria.|
|[CCRTAllocator::Reallocate](#reallocate)|(Estático) Llame a este método para reasignar memoria.|

## <a name="remarks"></a>Observaciones

[CHeapPtr](../../atl/reference/cheapptr-class.md) utiliza esta clase para proporcionar las rutinas de asignación de memoria de CRT. La clase [homóloga, CComAllocator](../../atl/reference/ccomallocator-class.md), proporciona los mismos métodos mediante rutinas COM.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a>CCRTAllocator::Asignar

Llame a esta función estática para asignar memoria.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes que se van a asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero void al espacio asignado, o NULL si no hay suficiente memoria disponible.

### <a name="remarks"></a>Observaciones

Asigna memoria. Consulte [malloc](../../c-runtime-library/reference/malloc.md) para obtener más detalles.

## <a name="ccrtallocatorfree"></a><a name="free"></a>CCRTAllocator::Gratis

Llame a esta función estática para liberar memoria.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria asignada.

### <a name="remarks"></a>Observaciones

Libera la memoria asignada. Consulte [gratis](../../c-runtime-library/reference/free.md) para obtener más detalles.

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a>CCRTAllocator::Reallocate

Llame a esta función estática para reasignar memoria.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria asignada.

*nBytes*<br/>
El número de bytes para reasignar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero void al espacio asignado o NULL si no hay memoria suficiente.

### <a name="remarks"></a>Observaciones

Cambia el tamaño de la cantidad de memoria asignada. Consulte [realloc](../../c-runtime-library/reference/realloc.md) para obtener más detalles.

## <a name="see-also"></a>Consulte también

[Clase CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Clase CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
