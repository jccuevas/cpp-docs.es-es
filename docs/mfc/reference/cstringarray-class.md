---
title: Clase CStringArray
ms.date: 11/04/2016
f1_keywords:
- CStringArray
- AFXCOLL/CStringArray
- AFXCOLL/CStringArray::CStringArray
- AFXCOLL/CStringArray::Add
- AFXCOLL/CStringArray::Append
- AFXCOLL/CStringArray::Copy
- AFXCOLL/CStringArray::ElementAt
- AFXCOLL/CStringArray::FreeExtra
- AFXCOLL/CStringArray::GetAt
- AFXCOLL/CStringArray::GetCount
- AFXCOLL/CStringArray::GetData
- AFXCOLL/CStringArray::GetSize
- AFXCOLL/CStringArray::GetUpperBound
- AFXCOLL/CStringArray::InsertAt
- AFXCOLL/CStringArray::IsEmpty
- AFXCOLL/CStringArray::RemoveAll
- AFXCOLL/CStringArray::RemoveAt
- AFXCOLL/CStringArray::SetAt
- AFXCOLL/CStringArray::SetAtGrow
- AFXCOLL/CStringArray::SetSize
helpviewer_keywords:
- CStringArray [MFC], CStringArray
- CStringArray [MFC], Add
- CStringArray [MFC], Append
- CStringArray [MFC], Copy
- CStringArray [MFC], ElementAt
- CStringArray [MFC], FreeExtra
- CStringArray [MFC], GetAt
- CStringArray [MFC], GetCount
- CStringArray [MFC], GetData
- CStringArray [MFC], GetSize
- CStringArray [MFC], GetUpperBound
- CStringArray [MFC], InsertAt
- CStringArray [MFC], IsEmpty
- CStringArray [MFC], RemoveAll
- CStringArray [MFC], RemoveAt
- CStringArray [MFC], SetAt
- CStringArray [MFC], SetAtGrow
- CStringArray [MFC], SetSize
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
ms.openlocfilehash: f5be5f44e86e3e24bc51dc014ca3c837bf5cf07d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445126"
---
# <a name="cstringarray-class"></a>Clase CStringArray

Admite matrices de objetos [CString](../../atl-mfc-shared/using-cstring.md) .

## <a name="syntax"></a>Sintaxis

```
class CStringArray : public CObject
```

## <a name="members"></a>Members

Las funciones miembro de `CStringArray` son similares a las funciones miembro de la [cobarra](../../mfc/reference/cobarray-class.md)de clases. Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para obtener información específica de la función miembro. Siempre que vea un puntero `CObject` como un valor devuelto, sustituya un objeto [CString](../../atl-mfc-shared/using-cstring.md) (no un puntero [CString](../../atl-mfc-shared/using-cstring.md) ). Siempre que vea un puntero `CObject` como un parámetro de función, use un `LPCTSTR`.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

por ejemplo, se traduce en

`CString CStringArray::GetAt( int <nIndex> ) const;`

y

`void SetAt( int <nIndex>, CObject* <newElement> )`

se traduce en

`void SetAt( int <nIndex>, LPCTSTR <newElement> )`

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringArray::CStringArray](../../mfc/reference/cobarray-class.md#cobarray)|Construye una matriz vacía.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringArray:: Add](../../mfc/reference/cobarray-class.md#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CStringArray:: Append](../../mfc/reference/cobarray-class.md#append)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CStringArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CStringArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|
|[CStringArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|
|[CStringArray:: GetAt](../../mfc/reference/cobarray-class.md#getat)|Devuelve el valor en un índice dado.|
|[CStringArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtiene el número de elementos de esta matriz.|
|[CStringArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Permite el acceso a los elementos de la matriz. Puede ser **NULL**.|
|[CStringArray:: obtiene](../../mfc/reference/cobarray-class.md#getsize)|Obtiene el número de elementos de esta matriz.|
|[CStringArray:: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Devuelve el índice válido de mayor tamaño.|
|[CStringArray:: Insertat (](../../mfc/reference/cobarray-class.md#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|
|[CStringArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Determina si la matriz está vacía.|
|[CStringArray:: RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Quita todos los elementos de esta matriz.|
|[CStringArray:: RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Quita un elemento en un índice específico.|
|[CStringArray:: SetAt](../../mfc/reference/cobarray-class.md#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|
|[CStringArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|
|[CStringArray:: setSize](../../mfc/reference/cobarray-class.md#setsize)|Establece el número de elementos que contendrá esta matriz.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringArray:: Operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Establece u obtiene el elemento en el índice especificado.|

## <a name="remarks"></a>Observaciones

`CStringArray` incorpora la macro IMPLEMENT_SERIAL para admitir la serialización y el volcado de sus elementos. Si una matriz de objetos `CString` se almacena en un archivo, bien con un operador de inserción sobrecargado, o bien con la función miembro `Serialize`, cada elemento se serializa a su vez.

> [!NOTE]
>  Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

Si se necesita un volcado de elementos de cadena individuales en la matriz, se debe establecer la profundidad del contexto de volcado en 1 o un valor superior.

Cuando se elimina una matriz `CString` o cuando se quitan sus elementos, se libera memoria de cadenas según corresponda.

Para obtener más información sobre el uso de `CStringArray`, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CStringArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
