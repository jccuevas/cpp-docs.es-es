---
title: IAtlStringMgr (clase)
ms.date: 10/18/2018
f1_keywords:
- IAtlStringMgr
- ATLSIMPSTR/ATL::IAtlStringMgr
- ATLSIMPSTR/ATL::Allocate
- ATLSIMPSTR/ATL::Clone
- ATLSIMPSTR/ATL::Free
- ATLSIMPSTR/ATL::GetNilString
- ATLSIMPSTR/ATL::Reallocate
helpviewer_keywords:
- shared classes, IAtlStringMgr
- memory, managing
- IAtlStringMgr class
ms.assetid: 722f0346-a770-4aa7-8f94-177be8dba823
ms.openlocfilehash: 978d33c719b9cb8c2708dc97fa78874534dfd748
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749963"
---
# <a name="iatlstringmgr-class"></a>IAtlStringMgr (clase)

Esta clase representa la interfaz para un `CStringT` Administrador de memoria.

## <a name="syntax"></a>Sintaxis

```
__interface IAtlStringMgr
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Allocate](#allocate)|Llame a este método para asignar una nueva estructura de datos de cadena.|
|[Clone](#clone)|Llamar a este método para devolver un puntero a un nuevo administrador de cadena para su uso con otra instancia de `CSimpleStringT`.|
|[Free](#free)|Llame a este método para liberar una estructura de datos de cadena.|
|[GetNilString](#getnilstring)|Devuelve un puntero a la `CStringData` objeto utilizado por los objetos de cadena vacía.|
|[Reallocate](#reallocate)|Llame a este método para reasignar una estructura de datos de cadena.|

## <a name="remarks"></a>Comentarios

Esta interfaz administra la memoria utilizada por las clases de cadenas independientes de MFC; como [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), y [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

También puede usar esta clase para implementar un administrador de memoria personalizado para la clase de cadena personalizada. Para obtener más información, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpstr.h

##  <a name="allocate"></a>  IAtlStringMgr::Allocate

Asigna una nueva estructura de datos de cadena.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parámetros

*nAllocLength*<br/>
El número de caracteres en el nuevo bloque de memoria.

*nCharSize*<br/>
El tamaño (en bytes) del tipo de caracteres utilizado por el Administrador de cadenas.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al bloque de memoria recién asignado.

> [!NOTE]
>  No se indican una asignación con error iniciando una excepción. En su lugar, debe señalar una asignación errónea al devolver NULL.

### <a name="remarks"></a>Comentarios

Llame a [IAtlStringMgr::Free](#free) o [IAtlStringMgr:: ReAllocate](#reallocate) para liberar la memoria asignada por este método.

> [!NOTE]
>  Para obtener ejemplos de uso, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="clone"></a>  IAtlStringMgr::Clone

Devuelve un puntero a un nuevo administrador de cadena para su uso con otra instancia de `CSimpleStringT`.

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia de la `IAtlStringMgr` objeto.

### <a name="remarks"></a>Comentarios

Normalmente lo llama el marco de trabajo cuando se necesita un administrador de cadenas para una nueva cadena. En la mayoría de los casos, el **esto** devuelve el puntero.

Sin embargo, si el Administrador de memoria no es compatible con la que se va a usar con varias instancias de `CSimpleStringT`, se debe devolver un puntero a un administrador de cadenas que se pueden compartir.

> [!NOTE]
>  Para obtener ejemplos de uso, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="free"></a>  IAtlStringMgr::Free

Libera una estructura de datos de cadena.

```
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
Un puntero al bloque de memoria que se va a liberar.

### <a name="remarks"></a>Comentarios

Libera el bloque de memoria especificado previamente asignado por [Allocate](#allocate) o [reasignar](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
>  Para obtener ejemplos de uso, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

##  <a name="getnilstring"></a>  IAtlStringMgr::GetNilString

Devuelve un puntero a una estructura de datos de cadena para una cadena vacía.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la `CStringData` objeto utilizado para representar una cadena vacía.

### <a name="remarks"></a>Comentarios

Llame a esta función para devolver la representación de una cadena vacía.

> [!NOTE]
> Al implementar un administrador de cadenas personalizado, esta función nunca debe producir un error. Puede asegurarse de esto mediante la incorporación de una instancia de `CNilStringData` en la clase de administrador de la cadena y devuelven un puntero a esa instancia.

> [!NOTE]
> Para obtener ejemplos de uso, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="reallocate"></a>  IAtlStringMgr::Reallocate

Reasigna una estructura de datos de cadena.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
Puntero a la memoria previamente asignada por este administrador de memoria.

*nAllocLength*<br/>
El número de caracteres en el nuevo bloque de memoria.

*nCharSize*<br/>
El tamaño (en bytes) del tipo de caracteres utilizado por el Administrador de cadenas.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Comentarios

Llame a esta función para cambiar el tamaño especificado por el bloque de memoria existente *pData*.

Llame a [IAtlStringMgr::Free](#free) para liberar la memoria asignada por este método.

> [!NOTE]
> Para obtener ejemplos de uso, consulte [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL y MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
