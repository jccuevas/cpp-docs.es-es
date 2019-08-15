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
ms.openlocfilehash: ce3585310198ee3e2d7b2b8b829f4202b1021284
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496199"
---
# <a name="cwin32heap-class"></a>Clase CWin32Heap

Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) con las funciones de asignación del montón de Win32.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWin32Heap::CWin32Heap](#cwin32heap)|El constructor.|
|[CWin32Heap::~CWin32Heap](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWin32Heap::Allocate](#allocate)|Asigna un bloque de memoria del objeto de montón.|
|[CWin32Heap::Attach](#attach)|Adjunta el objeto heap a un montón existente.|
|[CWin32Heap::Detach](#detach)|Desasocia el objeto heap de un montón existente.|
|[CWin32Heap::Free](#free)|Libera memoria previamente asignada del montón.|
|[CWin32Heap::GetSize](#getsize)|Devuelve el tamaño de un bloque de memoria asignado desde el objeto heap.|
|[CWin32Heap::Reallocate](#reallocate)|Reasigna un bloque de memoria del objeto de montón.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Marca que se usa para determinar la propiedad actual del identificador del montón.|
|[CWin32Heap::m_hHeap](#m_hheap)|Identificador del objeto de montón.|

## <a name="remarks"></a>Comentarios

`CWin32Heap`implementa los métodos de asignación de memoria mediante las funciones de asignación del montón de Win32, incluidas [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) y [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). A diferencia de otras clases heap `CWin32Heap` , requiere que se proporcione un identificador de montón válido antes de que se asigne la memoria: las otras clases tienen como valor predeterminado el montón del proceso. El identificador se puede proporcionar al constructor o al método [CWin32Heap:: Attach](#attach) . Vea el método [CWin32Heap:: CWin32Heap](#cwin32heap) para obtener más detalles.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlmem. h

##  <a name="allocate"></a>  CWin32Heap::Allocate

Asigna un bloque de memoria del objeto de montón.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes solicitado en el nuevo bloque de memoria.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Llame a [CWin32Heap:: Free](#free) o [CWin32Heap::](#reallocate) allocate para liberar la memoria asignada por este método.

Implementado mediante [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

##  <a name="attach"></a>  CWin32Heap::Attach

Adjunta el objeto heap a un montón existente.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parámetros

*hHeap*<br/>
Un identificador de montón existente.

*bTakeOwnership*<br/>
Marca que indica si el `CWin32Heap` objeto va a tomar posesión de los recursos del montón.

### <a name="remarks"></a>Comentarios

Si *bTakeOwnership* es true, el `CWin32Heap` objeto es responsable de eliminar el identificador del montón.

##  <a name="cwin32heap"></a>  CWin32Heap::CWin32Heap

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

### <a name="remarks"></a>Comentarios

Antes de asignar memoria, es necesario proporcionar el objeto `CWin32Heap` con un identificador de montón válido. El modo más sencillo de hacerlo es usar el montón de procesos:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

También se puede proporcionar un identificador de montón existente al constructor, en cuyo caso el nuevo objeto no asumirá la propiedad del montón. El identificador del montón original seguirá siendo válido cuando se elimine el objeto `CWin32Heap`.

También se puede adjuntar un montón existente al nuevo objeto, mediante [CWin32Heap:: Attach](#attach).

Si se necesita un montón en las operaciones que se realizan en un único subproceso, la mejor manera de hacerlo es crear el objeto del modo siguiente:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

El parámetro HEAP_NO_SERIALIZE especifica que la exclusión mutua no se utilizará cuando las funciones del montón asignan y liberan memoria, con un aumento en el rendimiento.

El tercer parámetro se establece en 0 de forma predeterminada, lo que permite al montón crecer según sea necesario. Consulte [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) para obtener una explicación de los tamaños de memoria y las marcas.

##  <a name="dtor"></a>  CWin32Heap::~CWin32Heap

Destructor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Comentarios

Destruye el identificador del montón si el `CWin32Heap` objeto tiene la propiedad del montón.

##  <a name="detach"></a>  CWin32Heap::Detach

Desasocia el objeto heap de un montón existente.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el identificador del montón al que se adjuntó el objeto previamente.

##  <a name="free"></a>  CWin32Heap::Free

Libera memoria previamente asignada del montón por [CWin32Heap::](#allocate) allocate o [CWin32Heap::](#reallocate)allocate.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero al bloque de memoria que se va a liberar. NULL es un valor válido y no hace nada.

##  <a name="getsize"></a>  CWin32Heap::GetSize

Devuelve el tamaño de un bloque de memoria asignado desde el objeto heap.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero al bloque de memoria cuyo tamaño obtendrá el método. Se trata de un puntero devuelto por [CWin32Heap::](#allocate) allocate o [CWin32Heap::](#reallocate)allocate.

### <a name="return-value"></a>Valor devuelto

Devuelve el tamaño, en bytes, del bloque de memoria asignado.

##  <a name="m_bownheap"></a>  CWin32Heap::m_bOwnHeap

Marca que se usa para determinar la propiedad actual del identificador del montón almacenado en [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

##  <a name="m_hheap"></a>  CWin32Heap::m_hHeap

Identificador del objeto de montón.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Comentarios

Variable que se usa para almacenar un identificador en el objeto de montón.

##  <a name="reallocate"></a>  CWin32Heap::Reallocate

Reasigna un bloque de memoria del objeto de montón.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parámetros

*p*<br/>
Puntero al bloque de memoria que se va a reasignar.

*nBytes*<br/>
Nuevo tamaño en bytes del bloque asignado. El bloque se puede hacer mayor o menor.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Si *p* es null, se supone que el bloque de memoria aún no se ha asignado y se llama a [CWin32Heap::](#allocate) allocate, con un argumento de *nBytes*.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../../atl/atl-class-overview.md)<br/>
[IAtlMemMgr (clase)](../../atl/reference/iatlmemmgr-class.md)<br/>
[CLocalHeap (clase)](../../atl/reference/clocalheap-class.md)<br/>
[CGlobalHeap (clase)](../../atl/reference/cglobalheap-class.md)<br/>
[CCRTHeap (clase)](../../atl/reference/ccrtheap-class.md)<br/>
[CComHeap (clase)](../../atl/reference/ccomheap-class.md)
