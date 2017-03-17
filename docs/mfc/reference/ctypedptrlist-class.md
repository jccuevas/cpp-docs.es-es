---
title: CTypedPtrList (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTypedPtrList
- AFXTEMPL/CTypedPtrList
- AFXTEMPL/CTypedPtrList::AddHead
- AFXTEMPL/CTypedPtrList::AddTail
- AFXTEMPL/CTypedPtrList::GetAt
- AFXTEMPL/CTypedPtrList::GetHead
- AFXTEMPL/CTypedPtrList::GetNext
- AFXTEMPL/CTypedPtrList::GetPrev
- AFXTEMPL/CTypedPtrList::GetTail
- AFXTEMPL/CTypedPtrList::RemoveHead
- AFXTEMPL/CTypedPtrList::RemoveTail
- AFXTEMPL/CTypedPtrList::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrList class
- type-safe collections
- lists [C++]
- template classes, CTypedPtrList class
- linked lists [C++]
- pointer lists
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ca8d868333aa977710e387fc1bb13271dc8f99fa
ms.lasthandoff: 02/24/2017

---
# <a name="ctypedptrlist-class"></a>Clase CTypedPtrList
Proporciona un "contenedor" de tipo seguro para objetos de clase `CPtrList`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrList : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parámetros  
 `BASE_CLASS`  
 Clase base de la clase de lista de puntero con tipo. debe ser una clase de lista de puntero ( `CObList` o `CPtrList`).  
  
 `TYPE`  
 Tipo de los elementos almacenados en la lista de clases base.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTypedPtrList::AddHead](#addhead)|Agrega un elemento (o todos los elementos de otra lista) en el encabezado de la lista (hace un nuevo encabezado).|  
|[CTypedPtrList::AddTail](#addtail)|Agrega un elemento (o todos los elementos de otra lista) hasta el final de la lista (hace una cola nueva).|  
|[CTypedPtrList::GetAt](#getat)|Obtiene el elemento en una posición determinada.|  
|[CTypedPtrList::GetHead](#gethead)|Devuelve el elemento principal de la lista (no puede estar vacía).|  
|[CTypedPtrList::GetNext](#getnext)|Obtiene el siguiente elemento para efectuar una iteración.|  
|[CTypedPtrList::GetPrev](#getprev)|Obtiene el elemento anterior para efectuar una iteración.|  
|[CTypedPtrList::GetTail](#gettail)|Devuelve el elemento final de la lista (no puede estar vacía).|  
|[CTypedPtrList::RemoveHead](#removehead)|Quita el elemento del encabezado de la lista.|  
|[CTypedPtrList::RemoveTail](#removetail)|Quita el elemento de la cola de la lista.|  
|[CTypedPtrList::SetAt](#setat)|Establece el elemento en una posición determinada.|  
  
## <a name="remarks"></a>Comentarios  
 Al usar `CTypedPtrList` en lugar de `CObList` o `CPtrList`, la utilidad de comprobación de tipos de C++ ayuda a eliminar los errores causados por los tipos de puntero no coinciden.  
  
 Además, el `CTypedPtrList` contenedor realiza gran parte de la conversión que sería necesaria si usó `CObList` o `CPtrList`.  
  
 Dado que todos los `CTypedPtrList` funciones están en línea, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.  
  
 Derivan de listas `CObList` se puede serializar, pero los derivados de `CPtrList` no puede.  
  
 Cuando se elimina un objeto `CTypedPtrList`, o cuando se quitan sus elementos, solo se quitan los punteros, no las entidades a las que hacen referencia.  
  
 Para obtener más información sobre el uso de `CTypedPtrList`, consulte los artículos [colecciones](../../mfc/collections.md) y [clases basadas en plantillas](../../mfc/template-based-classes.md).  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se crea una instancia de `CTypedPtrList`, agrega un objeto, se serializa la lista en el disco y, a continuación, elimina el objeto:  
  
 [!code-cpp[NVC_MFCCollections&#110;](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCCollections&#111;](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `BASE_CLASS`  
  
 `_CTypedPtrList`  
  
 `CTypedPtrList`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtempl.h  
  
##  <a name="addhead"></a>CTypedPtrList::AddHead  
 Llama a esta función miembro `BASE_CLASS` **:: AddHead**.  
  
```  
POSITION AddHead(TYPE newElement);  
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Tipo de los elementos almacenados en la lista de clases base.  
  
 `newElement`  
 El puntero de objeto para agregarse a esta lista. Un **NULL** se permite el valor.  
  
 `BASE_CLASS`  
 Clase base de la clase de lista de puntero con tipo. debe ser una clase de lista de puntero ( [CObList](../../mfc/reference/coblist-class.md) o [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Un puntero a otra [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objeto. Los elementos de `pNewList` se agregará a esta lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la primera versión del **posición** valor del elemento recién insertado.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión agrega un nuevo elemento antes del encabezado de la lista. La segunda versión agrega otra lista de elementos antes de la cabeza.  
  
##  <a name="addtail"></a>CTypedPtrList::AddTail  
 Llama a esta función miembro `BASE_CLASS` **:: AddTail**.  
  
```  
POSITION AddTail(TYPE newElement);  
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Tipo de los elementos almacenados en la lista de clases base.  
  
 `newElement`  
 El puntero de objeto para agregarse a esta lista. Un **NULL** se permite el valor.  
  
 `BASE_CLASS`  
 Clase base de la clase de lista de puntero con tipo. debe ser una clase de lista de puntero ( [CObList](../../mfc/reference/coblist-class.md) o [CPtrList](../../mfc/reference/cptrlist-class.md)).  
  
 `pNewList`  
 Un puntero a otra [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objeto. Los elementos de `pNewList` se agregará a esta lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la primera versión del **posición** valor del elemento recién insertado.  
  
### <a name="remarks"></a>Comentarios  
 La primera versión, agrega un nuevo elemento después del final de la lista. La segunda versión agrega otra lista de elementos después del final de la lista.  
  
##  <a name="getat"></a>CTypedPtrList::GetAt  
 Una variable de tipo **posición** es una clave para la lista.  
  
```  
TYPE& GetAt(POSITION position);  
TYPE GetAt(POSITION position) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.  
  
 *posición*  
 Un **posición** valor devuelto por un método `GetHeadPosition` o **buscar** llamada a función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se tiene acceso a la lista mediante un puntero a un **CTypedPtrList const**, a continuación, `GetAt` devuelve un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite que la función que se utilizará sólo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.  
  
 Si la lista se obtiene acceso directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetAt` devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
### <a name="remarks"></a>Comentarios  
 No es lo mismo que un índice y no puede funcionar en un **posición** valor usted mismo. `GetAt`Recupera el `CObject` puntero asociado a una posición determinada.  
  
 Debe asegurarse de que su **posición** valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 Llama a esta función inline `BASE_CLASS` **:: GetAt**.  
  
##  <a name="gethead"></a>CTypedPtrList::GetHead  
 Obtiene el puntero que representa el elemento principal de esta lista.  
  
```  
TYPE& GetHead();  
TYPE GetHead() const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se tiene acceso a la lista mediante un puntero a un **CTypedPtrList const**, a continuación, `GetHead` devuelve un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite que la función que se utilizará sólo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.  
  
 Si la lista se obtiene acceso directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetHead` devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que la lista no está vacía antes de llamar a `GetHead`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.  
  
##  <a name="getnext"></a>CTypedPtrList::GetNext  
 Obtiene el elemento de lista identificado por `rPosition`, a continuación, se establece `rPosition` a la **posición** valor de la entrada siguiente en la lista.  
  
```  
TYPE& GetNext(POSITION& rPosition);  
TYPE GetNext(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos incluidos en esta lista.  
  
 `rPosition`  
 Una referencia a un **posición** valor devuelto por un método `GetNext`, `GetHeadPosition`, u otra llamada de función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se tiene acceso a la lista mediante un puntero a un **CTypedPtrList const**, a continuación, `GetNext` devuelve un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite que la función que se utilizará sólo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.  
  
 Si la lista se obtiene acceso directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetNext` devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `GetNext` en un bucle de iteración de avance, si establece la posición inicial con una llamada a `GetHeadPosition` o [CPtrList::Find](../../mfc/reference/coblist-class.md#find).  
  
 Debe asegurarse de que su **posición** valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 Si el elemento recuperado es el último de la lista, a continuación, el nuevo valor de `rPosition` está establecido en **NULL**.  
  
 Es posible quitar un elemento durante una iteración. Vea el ejemplo de [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).  
  
##  <a name="getprev"></a>CTypedPtrList::GetPrev  
 Obtiene el elemento de lista identificado por `rPosition`, a continuación, se establece `rPosition` a la **posición** valor de la entrada anterior en la lista.  
  
```  
TYPE& GetPrev(POSITION& rPosition);  
TYPE GetPrev(POSITION& rPosition) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos incluidos en esta lista.  
  
 `rPosition`  
 Una referencia a un **posición** valor devuelto por un método `GetPrev` u otra llamada de función miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se tiene acceso a la lista mediante un puntero a un **CTypedPtrList const**, a continuación, `GetPrev` devuelve un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite que la función que se utilizará sólo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.  
  
 Si la lista se obtiene acceso directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetPrev` devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `GetPrev` en un bucle de iteración inversa si establece la posición inicial con una llamada a `GetTailPosition` o **buscar**.  
  
 Debe asegurarse de que su **posición** valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 Si el elemento recuperado es el primero en la lista, a continuación, el nuevo valor de `rPosition` está establecido en **NULL**.  
  
##  <a name="gettail"></a>CTypedPtrList::GetTail  
 Obtiene el puntero que representa el elemento principal de esta lista.  
  
```  
TYPE& GetTail();  
TYPE GetTail() const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se tiene acceso a la lista mediante un puntero a un **CTypedPtrList const**, a continuación, `GetTail` devuelve un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite que la función que se utilizará sólo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.  
  
 Si la lista se obtiene acceso directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetTail` devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que la lista no está vacía antes de llamar a `GetTail`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.  
  
##  <a name="removehead"></a>CTypedPtrList::RemoveHead  
 Quita el elemento de encabezado de la lista y lo devuelve.  
  
```  
TYPE RemoveHead();
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero previamente al principio de la lista. Este puntero es del tipo especificado por el parámetro de plantilla *tipo*.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que la lista no está vacía antes de llamar a `RemoveHead`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.  
  
##  <a name="removetail"></a>CTypedPtrList::RemoveTail  
 Quita el elemento de la cola de la lista y lo devuelve.  
  
```  
TYPE RemoveTail();
```  
  
### <a name="parameters"></a>Parámetros  
 *TIPO DE*  
 Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero previamente en la cola de la lista. Este puntero es del tipo especificado por el parámetro de plantilla *tipo*.  
  
### <a name="remarks"></a>Comentarios  
 Debe asegurarse de que la lista no está vacía antes de llamar a `RemoveTail`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.  
  
##  <a name="setat"></a>CTypedPtrList::SetAt  
 Llama a esta función miembro `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(POSITION pos, TYPE newElement);
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El **posición** del elemento que se va a establecer.  
  
 *TIPO DE*  
 Tipo de los elementos almacenados en la lista de clases base.  
  
 `newElement`  
 El puntero de objeto se escriban en la lista.  
  
### <a name="remarks"></a>Comentarios  
 Una variable de tipo **posición** es una clave para la lista. No es lo mismo que un índice y no puede funcionar en un **posición** valor usted mismo. `SetAt`Escribe el puntero de objeto a la posición especificada en la lista.  
  
 Debe asegurarse de que su **posición** valor representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 Para obtener comentarios más detallada, consulte [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CPtrList](../../mfc/reference/cptrlist-class.md)   
 [Clase cObList](../../mfc/reference/coblist-class.md)

