---
title: CComAllocator (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f867d3a7ca81d190ee363c7539e56a62004eb377
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088948"
---
# <a name="ccomallocator-class"></a>CComAllocator (clase)

Esta clase proporciona métodos para administrar la memoria que usa COM rutinas de memoria.

## <a name="syntax"></a>Sintaxis

```
class CComAllocator
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComAllocator::Allocate](#allocate)|Llame a este método estático para asignar memoria.|
|[CComAllocator::Free](#free)|Llame a este método estático para liberar memoria asignada.|
|[CComAllocator::Reallocate](#reallocate)|Llame a este método estático para reasignar memoria.|

## <a name="remarks"></a>Comentarios

Esta clase se utiliza por [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) para proporcionar rutinas de asignación de memoria COM. La clase homólogo, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), proporciona los mismos métodos que usa las rutinas de CRT.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="allocate"></a>  CComAllocator::Allocate

Llame a esta función estática para asignar memoria.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes que se van a asignar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero void al espacio asignado, o NULL si no hay suficiente memoria disponible.

### <a name="remarks"></a>Comentarios

Asigna memoria. Consulte [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) para obtener más detalles.

##  <a name="free"></a>  CComAllocator::Free

Llame a esta función estática para liberar memoria asignada.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria asignada.

### <a name="remarks"></a>Comentarios

Libera la memoria asignada. Consulte [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree) para obtener más detalles.

##  <a name="reallocate"></a>  CComAllocator::Reallocate

Llame a esta función estática para reasignar memoria.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria asignada.

*nBytes*<br/>
El número de bytes para reasignar.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero void al espacio asignado, o NULL si no hay memoria suficiente

### <a name="remarks"></a>Comentarios

Cambia el tamaño de la cantidad de memoria asignada. Consulte [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc) para obtener más detalles.

## <a name="see-also"></a>Vea también

[CComHeapPtr (clase)](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator (clase)](../../atl/reference/ccrtallocator-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
