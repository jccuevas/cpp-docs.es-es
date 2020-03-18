---
title: Clase CStringList
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CStringList::CStringList
- AFXCOLL/CStringList::AddHead
- AFXCOLL/CStringList::AddTail
- AFXCOLL/CStringList::Find
- AFXCOLL/CStringList::FindIndex
- AFXCOLL/CStringList::GetAt
- AFXCOLL/CStringList::GetCount
- AFXCOLL/CStringList::GetHead
- AFXCOLL/CStringList::GetHeadPosition
- AFXCOLL/CStringList::GetNext
- AFXCOLL/CStringList::GetPrev
- AFXCOLL/CStringList::GetSize
- AFXCOLL/CStringList::GetTail
- AFXCOLL/CStringList::GetTailPosition
- AFXCOLL/CStringList::InsertAfter
- AFXCOLL/CStringList::InsertBefore
- AFXCOLL/CStringList::IsEmpty
- AFXCOLL/CStringList::RemoveAll
- AFXCOLL/CStringList::RemoveAt
- AFXCOLL/CStringList::RemoveHead
- AFXCOLL/CStringList::RemoveTail
- AFXCOLL/CStringList::SetAt
helpviewer_keywords:
- CStringList [MFC], CStringList
- CStringList [MFC], AddHead
- CStringList [MFC], AddTail
- CStringList [MFC], Find
- CStringList [MFC], FindIndex
- CStringList [MFC], GetAt
- CStringList [MFC], GetCount
- CStringList [MFC], GetHead
- CStringList [MFC], GetHeadPosition
- CStringList [MFC], GetNext
- CStringList [MFC], GetPrev
- CStringList [MFC], GetSize
- CStringList [MFC], GetTail
- CStringList [MFC], GetTailPosition
- CStringList [MFC], InsertAfter
- CStringList [MFC], InsertBefore
- CStringList [MFC], IsEmpty
- CStringList [MFC], RemoveAll
- CStringList [MFC], RemoveAt
- CStringList [MFC], RemoveHead
- CStringList [MFC], RemoveTail
- CStringList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: 9eb7a713fc02cd3e51135d1985a41688d4c885d9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447550"
---
# <a name="cstringlist-class"></a>Clase CStringList

Admite listas de objetos `CString` .

## <a name="syntax"></a>Sintaxis

```
class CStringList : public CObject
```

## <a name="members"></a>Members

Las funciones miembro de `CStringList` son similares a las funciones miembro de la clase [CObList](../../mfc/reference/coblist-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CObList` para obtener información específica de la función miembro. Siempre que vea un puntero `CObject` como un valor devuelto, sustituya un `CString` (no un puntero `CString`). Siempre que vea un puntero `CObject` como un parámetro de función, sustituya un `LPCTSTR`.

`CObject*& CObList::GetHead() const;`

por ejemplo, se traduce en

`CString& CStringList::GetHead() const;`

y

`POSITION AddHead( CObject* <newElement> );`

se traduce en

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringList::CStringList](../../mfc/reference/coblist-class.md#coblist)|Crea una lista vacía.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Agrega un elemento (o todos los elementos de otra lista) al encabezado de la lista (crea un nuevo encabezado).|
|[CStringList:: Addtail (](../../mfc/reference/coblist-class.md#addtail)|Agrega un elemento (o todos los elementos de otra lista) al final de la lista (crea una nueva cola).|
|[CStringList:: Find](../../mfc/reference/coblist-class.md#find)|Obtiene la posición de un elemento especificado por el valor de puntero.|
|[CStringList:: FindIndex](../../mfc/reference/coblist-class.md#findindex)|Obtiene la posición de un elemento especificado por un índice basado en cero.|
|[CStringList:: GetAt](../../mfc/reference/coblist-class.md#getat)|Obtiene el elemento en una posición determinada.|
|[CStringList:: GetCount](../../mfc/reference/coblist-class.md#getcount)|Devuelve el número de elementos de esta lista.|
|[CStringList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Devuelve el elemento de encabezado de la lista (no puede estar vacío).|
|[CStringList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Devuelve la posición del elemento de encabezado de la lista.|
|[CStringList:: GetNext](../../mfc/reference/coblist-class.md#getnext)|Obtiene el siguiente elemento para recorrer en iteración.|
|[CStringList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Obtiene el elemento anterior para la iteración.|
|[CStringList:: obtiene](../../mfc/reference/coblist-class.md#getsize)|Devuelve el número de elementos de esta lista.|
|[CStringList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Devuelve el elemento de cola de la lista (no puede estar vacío).|
|[CStringList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Devuelve la posición del elemento tail de la lista.|
|[CStringList:: InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Inserta un nuevo elemento después de una posición determinada.|
|[CStringList:: InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Inserta un nuevo elemento antes de una posición determinada.|
|[CStringList:: IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Comprueba la condición de lista vacía (no hay elementos).|
|[CStringList:: RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Quita todos los elementos de esta lista.|
|[CStringList:: RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Quita un elemento de esta lista, especificado por la posición.|
|[CStringList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Quita el elemento del encabezado de la lista.|
|[CStringList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Quita el elemento del final de la lista.|
|[CStringList:: SetAt](../../mfc/reference/coblist-class.md#setat)|Establece el elemento en una posición determinada.|

## <a name="remarks"></a>Observaciones

Todas las comparaciones se realizan por valor, lo que significa que los caracteres de la cadena se comparan en lugar de las direcciones de las cadenas.

`CStringList` incorpora la macro IMPLEMENT_SERIAL para admitir la serialización y el volcado de sus elementos. Si una lista de objetos de `CString` se almacena en un archivo, ya sea con un operador de inserción sobrecargado o con la función miembro `Serialize`, cada elemento `CString` se serializa a su vez.

Si necesita un volcado de elementos de `CString` individuales, debe establecer la profundidad del contexto de volcado en 1 o más.

Para obtener más información sobre el uso de `CStringList`, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

## <a name="see-also"></a>Consulte también

[Ejemplo de recopilación de MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
