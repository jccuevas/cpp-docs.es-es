---
title: Clase CUIntArray
ms.date: 11/04/2016
f1_keywords:
- CUIntArray
- AFXCOLL/CUIntArray
- AFXCOLL/CUIntArray::CUIntArray
- AFXCOLL/CUIntArray::Add
- AFXCOLL/CUIntArray::Append
- AFXCOLL/CUIntArray::Copy
- AFXCOLL/CUIntArray::ElementAt
- AFXCOLL/CUIntArray::FreeExtra
- AFXCOLL/CUIntArray::GetAt
- AFXCOLL/CUIntArray::GetCount
- AFXCOLL/CUIntArray::GetData
- AFXCOLL/CUIntArray::GetSize
- AFXCOLL/CUIntArray::GetUpperBound
- AFXCOLL/CUIntArray::InsertAt
- AFXCOLL/CUIntArray::IsEmpty
- AFXCOLL/CUIntArray::RemoveAll
- AFXCOLL/CUIntArray::RemoveAt
- AFXCOLL/CUIntArray::SetAt
- AFXCOLL/CUIntArray::SetAtGrow
- AFXCOLL/CUIntArray::SetSize
helpviewer_keywords:
- CUIntArray [MFC], CUIntArray
- CUIntArray [MFC], Add
- CUIntArray [MFC], Append
- CUIntArray [MFC], Copy
- CUIntArray [MFC], ElementAt
- CUIntArray [MFC], FreeExtra
- CUIntArray [MFC], GetAt
- CUIntArray [MFC], GetCount
- CUIntArray [MFC], GetData
- CUIntArray [MFC], GetSize
- CUIntArray [MFC], GetUpperBound
- CUIntArray [MFC], InsertAt
- CUIntArray [MFC], IsEmpty
- CUIntArray [MFC], RemoveAll
- CUIntArray [MFC], RemoveAt
- CUIntArray [MFC], SetAt
- CUIntArray [MFC], SetAtGrow
- CUIntArray [MFC], SetSize
ms.assetid: d71f3d8f-ef9f-4e48-9b69-7782c0e2ddf7
ms.openlocfilehash: 9d620269bbf6695af992feaf0df2ef1161c9ae8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373240"
---
# <a name="cuintarray-class"></a>Clase CUIntArray

Admite matrices de enteros sin signo.

## <a name="syntax"></a>Sintaxis

```
class CUIntArray : public CObject
```

## <a name="members"></a>Miembros

Las funciones `CUIntArray` miembro de son similares a las funciones miembro de la clase [CObArray](../../mfc/reference/cobarray-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para obtener información específica de la función miembro. Dondequiera que `CObject` vea un puntero como un parámetro de función o un valor devuelto, sustituya un UINT.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

por ejemplo, se traduce en

`UINT CUIntArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CUIntArray::CUIntArray](../../mfc/reference/cobarray-class.md#cobarray)|Construye una matriz vacía.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CUIntArray::Add](../../mfc/reference/cobarray-class.md#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CUIntArray::Append](../../mfc/reference/cobarray-class.md#append)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CUIntArray::Copiar](../../mfc/reference/cobarray-class.md#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CUIntArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|
|[CUIntArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|
|[CUIntArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Devuelve el valor en un índice dado.|
|[CUIntArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtiene el número de elementos de esta matriz.|
|[CUIntArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Permite el acceso a los elementos de la matriz. Puede ser NULL.|
|[CUIntArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Obtiene el número de elementos de esta matriz.|
|[CUIntArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Devuelve el índice válido de mayor tamaño.|
|[CUIntArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|
|[CUIntArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Determina si la matriz está vacía.|
|[CUIntArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Quita todos los elementos de esta matriz.|
|[CUIntArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Quita un elemento en un índice específico.|
|[CUIntArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|
|[CUIntArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|
|[CUIntArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Establece el número de elementos que contendrá esta matriz.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CUIntArray::operator \[\]](../../mfc/reference/cobarray-class.md#operator_at)|Establece u obtiene el elemento en el índice especificado.|

## <a name="remarks"></a>Observaciones

Un entero sin signo, o UINT, difiere de las palabras y las palabras dobles en que el tamaño físico de un UINT puede cambiar dependiendo del entorno operativo de destino. Un UINT tiene el mismo tamaño que una palabra doble.

`CUIntArray`incorpora la [macro de IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic) para admitir el acceso de tipo en tiempo de ejecución y el volcado a un [CDumpContext](../../mfc/reference/cdumpcontext-class.md) objeto. Si necesita un volcado de elementos enteros sin signo individuales, debe establecer la profundidad del contexto de volcado en 1 o superior. Las matrices de enteros sin signo no se pueden serializar.

> [!NOTE]
> Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

Para obtener más `CUIntArray`información sobre el uso , vea el artículo [Colecciones](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CUIntArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll.h

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
