---
title: CByteArray (clase)
ms.date: 11/04/2016
f1_keywords:
- CByteArray
- AFXCOLL/CByteArray
- AFXCOLL/CByteArray::CByteArray
- AFXCOLL/CByteArray::Add
- AFXCOLL/CByteArray::Append
- AFXCOLL/CByteArray::Copy
- AFXCOLL/CByteArray::ElementAt
- AFXCOLL/CByteArray::FreeExtra
- AFXCOLL/CByteArray::GetAt
- AFXCOLL/CByteArray::GetCount
- AFXCOLL/CByteArray::GetData
- AFXCOLL/CByteArray::GetSize
- AFXCOLL/CByteArray::GetUpperBound
- AFXCOLL/CByteArray::InsertAt
- AFXCOLL/CByteArray::IsEmpty
- AFXCOLL/CByteArray::RemoveAll
- AFXCOLL/CByteArray::RemoveAt
- AFXCOLL/CByteArray::SetAt
- AFXCOLL/CByteArray::SetAtGrow
- AFXCOLL/CByteArray::SetSize
helpviewer_keywords:
- CByteArray [MFC], CByteArray
- CByteArray [MFC], Add
- CByteArray [MFC], Append
- CByteArray [MFC], Copy
- CByteArray [MFC], ElementAt
- CByteArray [MFC], FreeExtra
- CByteArray [MFC], GetAt
- CByteArray [MFC], GetCount
- CByteArray [MFC], GetData
- CByteArray [MFC], GetSize
- CByteArray [MFC], GetUpperBound
- CByteArray [MFC], InsertAt
- CByteArray [MFC], IsEmpty
- CByteArray [MFC], RemoveAll
- CByteArray [MFC], RemoveAt
- CByteArray [MFC], SetAt
- CByteArray [MFC], SetAtGrow
- CByteArray [MFC], SetSize
ms.assetid: 53d4a512-657c-4187-9609-e3f5339a78e0
ms.openlocfilehash: 2453e7c040b9101f9c3a3b018e274b16e76ebea7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446350"
---
# <a name="cbytearray-class"></a>CByteArray (clase)

Admite matrices dinámicas de bytes.

## <a name="syntax"></a>Sintaxis

```
class CByteArray : public CObject
```

## <a name="members"></a>Members

Las funciones miembro de `CByteArray` son similares a las funciones miembro de la [cobarra](../../mfc/reference/cobarray-class.md)de clases. Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para obtener información específica de la función miembro. Siempre que vea un puntero `CObject` como un parámetro de función o un valor devuelto, sustituya un BYTE.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

por ejemplo, se traduce en

`BYTE CByteArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CByteArray:: CByteArray](../../mfc/reference/cobarray-class.md#cobarray)|Construye una matriz vacía.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CByteArray:: Add](../../mfc/reference/cobarray-class.md#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CByteArray:: Append](../../mfc/reference/cobarray-class.md#append)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CByteArray:: Copy](../../mfc/reference/cobarray-class.md#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CByteArray:: ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Devuelve una referencia temporal al byte de la matriz.|
|[CByteArray:: FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|
|[CByteArray:: GetAt](../../mfc/reference/cobarray-class.md#getat)|Devuelve el valor en un índice dado.|
|[CByteArray:: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtiene el número de elementos de esta matriz.|
|[CByteArray:: GetData](../../mfc/reference/cobarray-class.md#getdata)|Permite el acceso a los elementos de la matriz. Puede ser NULL.|
|[CByteArray:: se obtiene](../../mfc/reference/cobarray-class.md#getsize)|Obtiene el número de elementos de esta matriz.|
|[CByteArray:: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Devuelve el índice válido de mayor tamaño.|
|[CByteArray:: Insertat (](../../mfc/reference/cobarray-class.md#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|
|[CByteArray:: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Determina si la matriz está vacía.|
|[CByteArray:: RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Quita todos los elementos de esta matriz.|
|[CByteArray:: RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Quita un elemento en un índice específico.|
|[CByteArray:: SetAt](../../mfc/reference/cobarray-class.md#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|
|[CByteArray:: SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|
|[CByteArray:: setSize](../../mfc/reference/cobarray-class.md#setsize)|Establece el número de elementos que contendrá esta matriz.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CByteArray:: Operator \[ \]](../../mfc/reference/cobarray-class.md#operator_at)|Establece u obtiene el elemento en el índice especificado.|

## <a name="remarks"></a>Observaciones

`CByteArray` incorpora la macro IMPLEMENT_SERIAL para admitir la serialización y el volcado de sus elementos. Si una matriz de bytes se almacena en un archivo, ya sea con el operador de inserción sobrecargado ( **<<** ) o con la función miembro `Serialize`, cada elemento se serializa, a su vez,.

> [!NOTE]
>  Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

Si necesita una salida de depuración de elementos individuales de la matriz, debe establecer la profundidad del objeto `CDumpContext` en 1 o más.

Para obtener más información sobre el uso de `CByteArray`, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CByteArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObArray (clase)](../../mfc/reference/cobarray-class.md)
