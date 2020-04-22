---
title: Clase IAtlStringMgr
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
ms.openlocfilehash: c3fabb7a7a6da4129787d219bd83b2a35fa0c4dd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746611"
---
# <a name="iatlstringmgr-class"></a>Clase IAtlStringMgr

Esta clase representa la `CStringT` interfaz de un administrador de memoria.

## <a name="syntax"></a>Sintaxis

```
__interface IAtlStringMgr
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Asignar](#allocate)|Llame a este método para asignar una nueva estructura de datos de cadena.|
|[Clonar](#clone)|Llame a este método para devolver un puntero a `CSimpleStringT`un nuevo administrador de cadenas para su uso con otra instancia de .|
|[Gratis](#free)|Llame a este método para liberar una estructura de datos de cadena.|
|[GetNilString](#getnilstring)|Devuelve un puntero `CStringData` al objeto utilizado por los objetos de cadena vacíos.|
|[Reasignar](#reallocate)|Llame a este método para reasignar una estructura de datos de cadena.|

## <a name="remarks"></a>Observaciones

Esta interfaz administra la memoria utilizada por las clases de cadena independientes de MFC; como [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)y [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md).

También puede usar esta clase para implementar un administrador de memoria personalizado para la clase de cadena personalizada. Para obtener más información, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpstr.h

## <a name="iatlstringmgrallocate"></a><a name="allocate"></a>IAtlStringMgr::Asignar

Asigna una nueva estructura de datos de cadena.

```
CStringData* Allocate(int nAllocLength,int nCharSize) throw();
```

### <a name="parameters"></a>Parámetros

*nAllocLength*<br/>
El número de caracteres en el nuevo bloque de memoria.

*nCharSize*<br/>
El tamaño (en bytes) del tipo de carácter utilizado por el administrador de cadenas.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al bloque de memoria recién asignado.

> [!NOTE]
> No señale una asignación con errores iniciando una excepción. En su lugar, se debe señalar una asignación con errores devolviendo NULL.

### <a name="remarks"></a>Observaciones

Llame a [IAtlStringMgr::Free](#free) o [IAtlStringMgr::ReAllocate](#reallocate) para liberar la memoria asignada por este método.

> [!NOTE]
> Para obtener ejemplos de uso, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrclone"></a><a name="clone"></a>IAtlStringMgr::Clone

Devuelve un puntero a un nuevo administrador `CSimpleStringT`de cadenas para su uso con otra instancia de .

```
IAtlStringMgr* Clone() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una copia del objeto `IAtlStringMgr`.

### <a name="remarks"></a>Observaciones

Normalmente llamado por el marco de trabajo cuando se necesita un administrador de cadenas para una nueva cadena. En la mayoría de los casos, se devuelve el puntero **this.**

Sin embargo, si el administrador de memoria `CSimpleStringT`no admite el uso de varias instancias de , se debe devolver un puntero a un administrador de cadenas que se puede editar.

> [!NOTE]
> Para obtener ejemplos de uso, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrfree"></a><a name="free"></a>IAtlStringMgr::Gratis

Libera una estructura de datos de cadena.

```cpp
void Free(CStringData* pData) throw();
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
Un puntero al bloque de memoria que se va a liberar.

### <a name="remarks"></a>Observaciones

Libera el bloque de memoria especificado previamente asignado por [Asignar](#allocate) o [Reasignar](../../atl/reference/iatlmemmgr-class.md#reallocate).

> [!NOTE]
> Para obtener ejemplos de uso, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrgetnilstring"></a><a name="getnilstring"></a>IAtlStringMgr::GetNilString

Devuelve un puntero a una estructura de datos de cadena para una cadena vacía.

```
CStringData* GetNilString() throw();
```

### <a name="return-value"></a>Valor devuelto

Puntero al `CStringData` objeto utilizado para representar una cadena vacía.

### <a name="remarks"></a>Observaciones

Llame a esta función para devolver una representación de una cadena vacía.

> [!NOTE]
> Al implementar un administrador de cadenas personalizado, esta función nunca debe producir un error. Puede asegurarse de esto incrustando una instancia de en la clase de `CNilStringData` administrador de cadenas y devolver un puntero a esa instancia.

> [!NOTE]
> Para obtener ejemplos de uso, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="iatlstringmgrreallocate"></a><a name="reallocate"></a>IAtlStringMgr::Reallocate

Reasigna una estructura de datos de cadena.

```
CStringData* Reallocate(
    CStringData* pData,
    int nAllocLength,
    int nCharSize) throw();
```

### <a name="parameters"></a>Parámetros

*pData*<br/>
Puntero a la memoria asignada previamente por este administrador de memoria.

*nAllocLength*<br/>
El número de caracteres en el nuevo bloque de memoria.

*nCharSize*<br/>
El tamaño (en bytes) del tipo de carácter utilizado por el administrador de cadenas.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al principio del bloque de memoria recién asignado.

### <a name="remarks"></a>Observaciones

Llame a esta función para cambiar el tamaño del bloque de memoria existente especificado por *pData*.

Llame a [IAtlStringMgr::Free](#free) para liberar la memoria asignada por este método.

> [!NOTE]
> Para obtener ejemplos de uso, vea [Administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases compartidas ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
