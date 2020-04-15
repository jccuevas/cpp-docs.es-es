---
title: Clase CWin32Heap
ms.date: 11/04/2016
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
ms.openlocfilehash: fbdb77e7f52e858401c87e1cd8782b59cc6ebcea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330460"
---
# <a name="cwin32heap-class"></a>Clase CWin32Heap

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de asignación de montón Win32.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWin32Heap::CWin32Heap](#cwin32heap)|El constructor.|
|[CWin32Heap::-CWin32Heap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWin32Heap::Asignar](#allocate)|Asigna un bloque de memoria del objeto de montón.|
|[CWin32Heap::Attach](#attach)|Asocia el objeto de montón a un montón existente.|
|[CWin32Heap::Detach](#detach)|Separa el objeto de montón de un montón existente.|
|[CWin32Heap::Gratis](#free)|Libera memoria previamente asignada del montón.|
|[CWin32Heap::GetSize](#getsize)|Devuelve el tamaño de un bloque de memoria asignado desde el objeto de montón.|
|[CWin32Heap::Reallocate](#reallocate)|Reasigna un bloque de memoria del objeto de montón.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Marca utilizada para determinar la propiedad actual del identificador de montón.|
|[CWin32Heap::m_hHeap](#m_hheap)|Controlar el objeto de montón.|

## <a name="remarks"></a>Observaciones

`CWin32Heap`implementa métodos de asignación de memoria mediante las funciones de asignación de montón de Win32, incluidos [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) y [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). A diferencia de `CWin32Heap` otras clases de montón, requiere que se proporcione un identificador de montón válido antes de asignar memoria: las otras clases utilizan el montón de procesos de forma predeterminada. El identificador se puede proporcionar al constructor o a la [CWin32Heap::Attach](#attach) método. Consulte el [método CWin32Heap::CWin32Heap](#cwin32heap) para obtener más detalles.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem.h

## <a name="cwin32heapallocate"></a><a name="allocate"></a>CWin32Heap::Asignar

Asigna un bloque de memoria del objeto de montón.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al bloque de memoria recién asignado.

### <a name="remarks"></a>Observaciones

Llame a [CWin32Heap::Free](#free) o [CWin32Heap::Reallocate](#reallocate) para liberar la memoria asignada por este método.

Se implementa mediante [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

## <a name="cwin32heapattach"></a><a name="attach"></a>CWin32Heap::Attach

Asocia el objeto de montón a un montón existente.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parámetros

*hHeap*<br/>
Un identificador de montón existente.

*bTakeOwnership*<br/>
Marca que indica `CWin32Heap` si el objeto debe tomar posesión sobre los recursos del montón.

### <a name="remarks"></a>Observaciones

Si *bTakeOwnership* es `CWin32Heap` TRUE, el objeto es responsable de eliminar el identificador de montón.

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a>CWin32Heap::CWin32Heap

El constructor.

```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```

### <a name="parameters"></a>Parámetros

*hHeap*<br/>
Objeto de montón existente.

*dwFlags*<br/>
Marcas utilizadas en la creación del montón.

*nInitialSize*<br/>
Tamaño inicial del montón.

*nMaxSize*<br/>
Tamaño máximo del montón.

### <a name="remarks"></a>Observaciones

Antes de asignar memoria, es necesario proporcionar el objeto `CWin32Heap` con un identificador de montón válido. El modo más sencillo de hacerlo es usar el montón de procesos:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

También se puede proporcionar un identificador de montón existente al constructor, en cuyo caso el nuevo objeto no asumirá la propiedad del montón. El identificador del montón original seguirá siendo válido cuando se elimine el objeto `CWin32Heap`.

Un montón existente también se puede asociar al nuevo objeto, mediante [CWin32Heap::Attach](#attach).

Si se necesita un montón en las operaciones que se realizan en un único subproceso, la mejor manera de hacerlo es crear el objeto del modo siguiente:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

El parámetro HEAP_NO_SERIALIZE especifica que la exclusión mutua no se utilizará cuando las funciones del montón asignen y liberen memoria, con el correspondiente aumento de rendimiento.

El tercer parámetro se establece en 0 de forma predeterminada, lo que permite al montón crecer según sea necesario. Consulte [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) para obtener una explicación de los tamaños de memoria y las marcas.

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a>CWin32Heap::-CWin32Heap

Destructor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Observaciones

Destruye el identificador de `CWin32Heap` montón si el objeto tiene la propiedad del montón.

## <a name="cwin32heapdetach"></a><a name="detach"></a>CWin32Heap::Detach

Separa el objeto de montón de un montón existente.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador al montón al que se adjuntó previamente el objeto.

## <a name="cwin32heapfree"></a><a name="free"></a>CWin32Heap::Gratis

Libera memoria previamente asignada del montón por [CWin32Heap::Allocate](#allocate) o [CWin32Heap::Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero al bloque de memoria para liberar. NULL es un valor válido y no hace nada.

## <a name="cwin32heapgetsize"></a><a name="getsize"></a>CWin32Heap::GetSize

Devuelve el tamaño de un bloque de memoria asignado desde el objeto de montón.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero al bloque de memoria cuyo tamaño obtendrá el método. Se trata de un puntero devuelto por [CWin32Heap::Allocate](#allocate) o [CWin32Heap::Reallocate](#reallocate).

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño, en bytes, del bloque de memoria asignado.

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap

Marca utilizada para determinar la propiedad actual del identificador de montón almacenado en [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a>CWin32Heap::m_hHeap

Controlar el objeto de montón.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Observaciones

Variable utilizada para almacenar un identificador en el objeto de montón.

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a>CWin32Heap::Reallocate

Reasigna un bloque de memoria del objeto de montón.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*P*<br/>
Puntero al bloque de memoria que se va a reasignar.

*nBytes*<br/>
Nuevo tamaño en bytes del bloque asignado. El bloque se puede hacer mayor o menor.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al bloque de memoria recién asignado.

### <a name="remarks"></a>Observaciones

Si *p* es NULL, se supone que el bloque de memoria aún no se ha asignado y se llama a [CWin32Heap::Allocate,](#allocate) con un argumento de *nBytes*.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)<br/>
[Clase CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Clase CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Clase CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Clase CComHeap](../../atl/reference/ccomheap-class.md)
