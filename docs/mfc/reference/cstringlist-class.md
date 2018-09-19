---
title: Clase de objeto CStringList | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31e13222ccd5ac12768961ff5e93d11e68ecfded
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122720"
---
# <a name="cstringlist-class"></a>Clase de objeto CStringList
Admite listas de objetos `CString` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CStringList : public CObject  
```  
  
## <a name="members"></a>Miembros  
 Las funciones miembro de `CStringList` son similares a las funciones miembro de clase [CObList](../../mfc/reference/coblist-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CObList` para obtener información específica de la función miembro. Siempre que vea un `CObject` puntero como un valor devuelto, use un `CString` (no un `CString` puntero). Siempre que vea un `CObject` puntero como un parámetro de función, use un `LPCTSTR`.  
  
 `CObject*& CObList::GetHead() const;`  
  
 por ejemplo, se traduce en  
  
 `CString& CStringList::GetHead() const;`  
  
 y  
  
 `POSITION AddHead( CObject* <newElement> );`  
  
 se traduce en  
  
 `POSITION AddHead( LPCTSTR <newElement> );`  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|Construye una lista vacía.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Agrega un elemento (o todos los elementos de otra lista) en el encabezado de la lista (hace un nuevo encabezado).|  
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|Agrega un elemento (o todos los elementos de otra lista) a la cola de la lista (hace una cola nueva).|  
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|Obtiene la posición de un elemento especificado por el valor del puntero.|  
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|Obtiene la posición de un elemento especificado por un índice de base cero.|  
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|Obtiene el elemento en una posición determinada.|  
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|Devuelve el número de elementos en esta lista.|  
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Devuelve el elemento principal de la lista (no puede estar vacía).|  
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Devuelve la posición del elemento principal de la lista.|  
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|Obtiene el elemento siguiente para efectuar una iteración.|  
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Obtiene el elemento anterior para efectuar una iteración.|  
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|Devuelve el número de elementos en esta lista.|  
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Devuelve el elemento final de la lista (no puede estar vacía).|  
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Devuelve la posición del elemento final de la lista.|  
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Inserta un nuevo elemento después de una posición especificada.|  
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Inserta un nuevo elemento antes de una posición especificada.|  
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Comprueba si la condición de la lista vacía (no hay elementos).|  
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Quita todos los elementos de esta lista.|  
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Quita un elemento de esta lista, especificada por posición.|  
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Quita el elemento del encabezado de la lista.|  
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Quita el elemento de la cola de la lista.|  
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|Establece el elemento en una posición determinada.|  
  
## <a name="remarks"></a>Comentarios  
 Todas las comparaciones se realizan por valor, lo que significa que se comparan los caracteres de la cadena en lugar de las direcciones de las cadenas.  
  
 `CStringList` incorpora la macro IMPLEMENT_SERIAL para admitir la serialización y el volcado de sus elementos. Si es una lista de `CString` los objetos se almacenan en un archivo, con un operador de inserción sobrecargado o con el `Serialize` miembro funcione, cada uno de ellos `CString` elemento se serializa a su vez.  
  
 Si se necesita un volcado de persona `CString` elementos, debe establecer la profundidad del contexto de volcado en 1 o mayor.  
  
 Para obtener más información sobre el uso de `CStringList`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



