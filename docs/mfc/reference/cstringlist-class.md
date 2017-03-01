---
title: Clase de objeto CStringList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringList
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], lists
- lists, string
- CStringList class
- strings [C++], collections
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0b67104e330890ffe8f67bac0dd3b129c7742a29
ms.lasthandoff: 02/24/2017

---
# <a name="cstringlist-class"></a>Clase de objeto CStringList
Admite listas de objetos `CString` .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CStringList : public CObject  
```  
  
## <a name="members"></a>Miembros  
 Las funciones miembro de `CStringList` son similares a las funciones miembro de clase [CObList](../../mfc/reference/coblist-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CObList` para obtener información específica de la función miembro. Siempre que vea un `CObject` puntero como valor devuelto, use un `CString` (no un `CString` puntero). Siempre que vea un `CObject` puntero como un parámetro de función, use un `LPCTSTR`.  
  
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
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|Construye una lista vacía.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Agrega un elemento (o todos los elementos de otra lista) en el encabezado de la lista (hace un nuevo encabezado).|  
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|Agrega un elemento (o todos los elementos de otra lista) hasta el final de la lista (hace una cola nueva).|  
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|Obtiene la posición de un elemento especificado por el valor de puntero.|  
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|Obtiene la posición de un elemento especificado por un índice de base cero.|  
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|Obtiene el elemento en una posición determinada.|  
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|Devuelve el número de elementos de esta lista.|  
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Devuelve el elemento principal de la lista (no puede estar vacía).|  
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Devuelve la posición del elemento principal de la lista.|  
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|Obtiene el siguiente elemento para efectuar una iteración.|  
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Obtiene el elemento anterior para efectuar una iteración.|  
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|Devuelve el número de elementos de esta lista.|  
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Devuelve el elemento final de la lista (no puede estar vacía).|  
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Devuelve la posición del elemento final de la lista.|  
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Inserta un nuevo elemento después de una posición especificada.|  
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Inserta un nuevo elemento antes de una posición especificada.|  
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Pruebas para la condición de la lista vacía (no hay elementos).|  
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Quita todos los elementos de esta lista.|  
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Quita un elemento de esta lista, especificada por posición.|  
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Quita el elemento del encabezado de la lista.|  
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Quita el elemento de la cola de la lista.|  
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|Establece el elemento en una posición determinada.|  
  
## <a name="remarks"></a>Comentarios  
 Todas las comparaciones se realizan por valor, lo que significa que se comparan los caracteres de la cadena en lugar de las direcciones de las cadenas.  
  
 `CStringList` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Si una lista de `CString` objetos se almacenan en un archivo, con un operador de inserción sobrecargado o con el `Serialize` cada miembro de función `CString` elemento se serializa a su vez.  
  
 Si se necesita un volcado de individuales `CString` elementos, debe establecer la profundidad del contexto de volcado en 1 o superior.  
  
 Para obtener más información sobre el uso de `CStringList`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




