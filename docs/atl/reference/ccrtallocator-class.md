---
title: CCRTAllocator (clase)
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
ms.openlocfilehash: c08d594e1c0f4d532f46961e266bf6ced98c51b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259084"
---
# <a name="ccrtallocator-class"></a>CCRTAllocator (clase)

Esta clase proporciona métodos para administrar la memoria utilizando las rutinas de memoria de CRT.

## <a name="syntax"></a>Sintaxis

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CCRTAllocator::Allocate](#allocate)|(Estático) Llame a este método para asignar memoria.|
|[CCRTAllocator::Free](#free)|(Estático) Llame a este método para liberar memoria.|
|[CCRTAllocator::Reallocate](#reallocate)|(Estático) Llame a este método para reasignar memoria.|

## <a name="remarks"></a>Comentarios

Esta clase se utiliza por [CHeapPtr](../../atl/reference/cheapptr-class.md) para proporcionar rutinas de asignación de la memoria de CRT. La clase homólogo, [CComAllocator](../../atl/reference/ccomallocator-class.md), proporciona los mismos métodos que usa COM rutinas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

##  <a name="allocate"></a>  CCRTAllocator::Allocate

Llame a esta función estática para asignar memoria.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes que se van a asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero void al espacio asignado, o NULL si no hay suficiente memoria disponible.

### <a name="remarks"></a>Comentarios

Asigna memoria. Consulte [malloc](../../c-runtime-library/reference/malloc.md) para obtener más detalles.

##  <a name="free"></a>  CCRTAllocator::Free

Llame a esta función estática para liberar memoria.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria asignada.

### <a name="remarks"></a>Comentarios

Libera la memoria asignada. Consulte [libre](../../c-runtime-library/reference/free.md) para obtener más detalles.

##  <a name="reallocate"></a>  CCRTAllocator::Reallocate

Llame a esta función estática para reasignar memoria.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria asignada.

*nBytes*<br/>
El número de bytes para reasignar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero void al espacio asignado o NULL si no hay memoria suficiente.

### <a name="remarks"></a>Comentarios

Cambia el tamaño de la cantidad de memoria asignada. Consulte [realloc](../../c-runtime-library/reference/realloc.md) para obtener más detalles.

## <a name="see-also"></a>Vea también

[CHeapPtr (clase)](../../atl/reference/cheapptr-class.md)<br/>
[CComAllocator (clase)](../../atl/reference/ccomallocator-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
