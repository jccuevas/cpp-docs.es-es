---
title: Clase CStringArray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringArray
dev_langs:
- C++
helpviewer_keywords:
- string arrays
- arrays [C++], strings
- CStringArray class
- strings [C++], collections
ms.assetid: 6c637e06-bba8-4c08-b0fc-cf8cb067ce34
caps.latest.revision: 24
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
ms.openlocfilehash: 6f6ef1f6bdef74540948520cc27d6c10b143216c
ms.lasthandoff: 02/24/2017

---
# <a name="cstringarray-class"></a>Clase CStringArray
Admite matrices de [CString](../../atl-mfc-shared/using-cstring.md) objetos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CStringArray : public CObject  
```  
  
## <a name="members"></a>Miembros  
 Las funciones miembro de `CStringArray` son similares a las funciones miembro de clase [CObArray](../../mfc/reference/cobarray-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CObArray` para obtener información específica de la función miembro. Siempre que vea un `CObject` puntero como valor devuelto, use un [CString](../../atl-mfc-shared/using-cstring.md) objeto (no un [CString](../../atl-mfc-shared/using-cstring.md) puntero). Siempre que vea un puntero `CObject` como un parámetro de función, use un `LPCTSTR`.  
  
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
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Construye una matriz vacía.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|  
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|  
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Devuelve el valor en un índice dado.|  
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtiene el número de elementos de esta matriz.|  
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Permite el acceso a los elementos de la matriz. Puede ser **NULL**.|  
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Obtiene el número de elementos de esta matriz.|  
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Devuelve el índice válido de mayor tamaño.|  
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|  
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Determina si la matriz está vacía.|  
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Quita todos los elementos de esta matriz.|  
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Quita un elemento en un índice específico.|  
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|  
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|  
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Establece el número de elementos que contendrá esta matriz.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[[] CObArray::operator](../../mfc/reference/cobarray-class.md#operator_at)|Establece u obtiene el elemento en el índice especificado.|  
  
## <a name="remarks"></a>Comentarios  
 `CStringArray` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Si una matriz de objetos `CString` se almacena en un archivo, bien con un operador de inserción sobrecargado, o bien con la función miembro `Serialize`, cada elemento se serializa a su vez.  
  
> [!NOTE]
>  Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.  
  
 Si se necesita un volcado de elementos de cadena individuales en la matriz, se debe establecer la profundidad del contexto de volcado en 1 o un valor superior.  
  
 Cuando se elimina una matriz `CString` o cuando se quitan sus elementos, se libera memoria de cadenas según corresponda.  
  
 Para obtener más información sobre el uso de `CStringArray`, vea el artículo [colecciones](../../mfc/collections.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CStringArray`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcoll.h  
  
## <a name="see-also"></a>Vea también  
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




