---
title: Clase CComAllocator
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 165cdb8b0b16a4872214f4556c26ee141e6a4d89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321138"
---
# <a name="ccomallocator-class"></a>Clase CComAllocator

Esta clase proporciona métodos para administrar la memoria mediante rutinas de memoria COM.

## <a name="syntax"></a>Sintaxis

```
class CComAllocator
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComAllocator::Asignar](#allocate)|Llame a este método estático para asignar memoria.|
|[CComAllocator::Gratis](#free)|Llame a este método estático para liberar memoria asignada.|
|[CComAllocator::Reallocate](#reallocate)|Llame a este método estático para reasignar memoria.|

## <a name="remarks"></a>Observaciones

[CComHeapPtr](../../atl/reference/ccomheapptr-class.md) utiliza esta clase para proporcionar las rutinas de asignación de memoria COM. La clase homóloga, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), proporciona los mismos métodos mediante rutinas CRT.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a>CComAllocator::Asignar

Llame a esta función estática para asignar memoria.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes que se van a asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero void al espacio asignado, o NULL si no hay suficiente memoria disponible.

### <a name="remarks"></a>Observaciones

Asigna memoria. Consulte [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) para obtener más detalles.

## <a name="ccomallocatorfree"></a><a name="free"></a>CComAllocator::Gratis

Llame a esta función estática para liberar memoria asignada.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria asignada.

### <a name="remarks"></a>Observaciones

Libera la memoria asignada. Consulte [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) para obtener más detalles.

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a>CComAllocator::Reallocate

Llame a esta función estática para reasignar memoria.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero a la memoria asignada.

*nBytes*<br/>
El número de bytes para reasignar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero void al espacio asignado, o NULL si no hay memoria suficiente

### <a name="remarks"></a>Observaciones

Cambia el tamaño de la cantidad de memoria asignada. Consulte [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) para obtener más detalles.

## <a name="see-also"></a>Consulte también

[Clase CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Clase CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
