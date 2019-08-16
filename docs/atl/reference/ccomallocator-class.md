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
ms.openlocfilehash: de302c7a58bf1b15e63e7cd391621ed9558e5a70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497594"
---
# <a name="ccomallocator-class"></a>Clase CComAllocator

Esta clase proporciona métodos para administrar la memoria mediante rutinas de memoria COM.

## <a name="syntax"></a>Sintaxis

```
class CComAllocator
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComAllocator::Allocate](#allocate)|Llame a este método estático para asignar memoria.|
|[CComAllocator::Free](#free)|Llame a este método estático para liberar memoria asignada.|
|[CComAllocator::Reallocate](#reallocate)|Llame a este método estático para reasignar la memoria.|

## <a name="remarks"></a>Comentarios

[CComHeapPtr](../../atl/reference/ccomheapptr-class.md) usa esta clase para proporcionar las rutinas de asignación de memoria de com. La clase homólogo, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), proporciona los mismos métodos con las rutinas de CRT.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

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

Asigna memoria. Consulte [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) para obtener más detalles.

##  <a name="free"></a>  CComAllocator::Free

Llame a esta función estática para liberar memoria asignada.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero a la memoria asignada.

### <a name="remarks"></a>Comentarios

Libera la memoria asignada. Vea [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) para obtener más detalles.

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

Devuelve un puntero void al espacio asignado o NULL si no hay suficiente memoria

### <a name="remarks"></a>Comentarios

Cambia el tamaño de la cantidad de memoria asignada. Consulte [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) para obtener más información.

## <a name="see-also"></a>Vea también

[CComHeapPtr (clase)](../../atl/reference/ccomheapptr-class.md)<br/>
[CCRTAllocator (clase)](../../atl/reference/ccrtallocator-class.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
