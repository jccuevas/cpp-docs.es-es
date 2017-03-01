---
title: Clase CAtlList | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CAtlList
- CAtlList
- ATL::CAtlList
dev_langs:
- C++
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
caps.latest.revision: 19
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
ms.openlocfilehash: b1ed350da625695f610980f9f48a6ae11394d3c8
ms.lasthandoff: 02/24/2017

---
# <a name="catllist-class"></a>Clase CAtlList
Esta clase proporciona métodos para crear y administrar un objeto de lista.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename E, class ETraits = CElementTraits<E>>  
class CAtlList
```  
  
#### <a name="parameters"></a>Parámetros  
 `E`  
 El tipo de elemento.  
  
 `ETraits`  
 El código utilizado para copiar o mover elementos. Consulte [CElementTraits clase](../../atl/reference/celementtraits-class.md) para obtener más detalles.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlList::INARGTYPE](#inargtype)||  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlList::CAtlList](#catllist)|El constructor.|  
|[CAtlList:: ~ CAtlList](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlList::AddHead](#addhead)|Llame a este método para agregar un elemento al principio de la lista.|  
|[CAtlList::AddHeadList](#addheadlist)|Llame a este método para agregar una lista existente en el encabezado de la lista.|  
|[CAtlList::AddTail](#addtail)|Llamar a este método para agregar un elemento a la cola de esta lista.|  
|[CAtlList::AddTailList](#addtaillist)|Llamar a este método para agregar una lista existente a la cola de esta lista.|  
|[CAtlList::AssertValid](#assertvalid)|Llamar a este método para confirmar que la lista es válida.|  
|[CAtlList::Find](#find)|Llame a este método para buscar en la lista para el elemento especificado.|  
|[CAtlList::FindIndex](#findindex)|Llame a este método para obtener la posición de un elemento, dado un valor de índice.|  
|[CAtlList::GetAt](#getat)|Llame a este método para devolver el elemento en una posición especificada en la lista.|  
|[CAtlList::GetCount](#getcount)|Llame a este método para devolver el número de objetos en la lista.|  
|[CAtlList::GetHead](#gethead)|Llame a este método para devolver el elemento situado al principio de la lista.|  
|[CAtlList::GetHeadPosition](#getheadposition)|Llame a este método para obtener la posición de la cabeza de la lista.|  
|[CAtlList::GetNext](#getnext)|Llame a este método para devolver el siguiente elemento de la lista.|  
|[CAtlList::GetPrev](#getprev)|Llame a este método para devolver el elemento anterior de la lista.|  
|[CAtlList::GetTail](#gettail)|Llame a este método para devolver el elemento en la cola de la lista.|  
|[CAtlList::GetTailPosition](#gettailposition)|Llame a este método para obtener la posición de la cola de la lista.|  
|[CAtlList::InsertAfter](#insertafter)|Llame a este método para insertar un nuevo elemento en la lista después de la posición especificada.|  
|[CAtlList::InsertBefore](#insertbefore)|Llamar a este método para insertar un nuevo elemento en la lista antes de la posición especificada.|  
|[CAtlList::IsEmpty](#isempty)|Llame a este método para determinar si la lista está vacía.|  
|[CAtlList::MoveToHead](#movetohead)|Llamar a este método para mover el elemento especificado en el encabezado de la lista.|  
|[CAtlList::MoveToTail](#movetotail)|Llamar a este método para mover el elemento especificado a la cola de la lista.|  
|[CAtlList::RemoveAll](#removeall)|Llame a este método para quitar todos los elementos de la lista.|  
|[CAtlList::RemoveAt](#removeat)|Llame a este método para quitar un único elemento de la lista.|  
|[CAtlList::RemoveHead](#removehead)|Llame a este método para quitar el elemento situado al principio de la lista.|  
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Llame a este método para quitar el elemento situado al principio de la lista sin devolver un valor.|  
|[CAtlList::RemoveTail](#removetail)|Llame a este método para quitar el elemento del final de la lista.|  
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Llame a este método para quitar el elemento del final de la lista sin devolver un valor.|  
|[CAtlList::SetAt](#setat)|Llamar a este método para establecer el valor del elemento en una posición determinada en la lista.|  
|[CAtlList::SwapElements](#swapelements)|Llamar a este método para intercambiar los elementos de la lista.|  
  
## <a name="remarks"></a>Comentarios  
 La `CAtlList` clase admite listas ordenadas de objetos no únicos accesibles secuencialmente o por valor. `CAtlList`listas se comportan como listas doblemente vinculadas. Cada lista tiene un encabezamiento y un final, y nuevos elementos (o en algunos casos listas) pueden agregar hasta final de la lista, o insertar antes o después de elementos específicos.  
  
 La mayoría de los `CAtlList` métodos hacen que el uso de un valor de posición. Este valor se utiliza con los métodos para hacer referencia a la ubicación de memoria real donde los elementos se almacenan y no se deben calcular o predecir directamente. Si es necesario para tener acceso a la *n*elemento en la lista, el método [CAtlList::FindIndex](#findindex) devolverá el valor de la posición correspondiente de un índice determinado. Los métodos [CAtlList::GetNext](#getnext) y [CAtlList::GetPrev](#getprev) puede utilizarse para recorrer en iteración los objetos de la lista.  
  
 Para obtener más información sobre las clases de colección disponible con ATL, vea [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="a-nameaddheada--catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead  
 Llame a este método para agregar un elemento al principio de la lista.  
  
```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```  
  
### <a name="parameters"></a>Parámetros  
 `element`  
 El nuevo elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición del elemento recién agregado.  
  
### <a name="remarks"></a>Comentarios  
 Si se utiliza la primera versión, se crea un elemento vacío con su constructor predeterminado, en lugar de su constructor de copia.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#13;](../../atl/codesnippet/cpp/catllist-class_1.cpp)]  
  
##  <a name="a-nameaddheadlista--catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList  
 Llame a este método para agregar una lista existente en el encabezado de la lista.  
  
```
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>Parámetros  
 `plNew`  
 La lista que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 La lista que apunta `plNew` se inserta al principio de la lista existente. En compilaciones de depuración, se producirá un error de aserción si `plNew` es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#14;](../../atl/codesnippet/cpp/catllist-class_2.cpp)]  
  
##  <a name="a-nameaddtaila--catllistaddtail"></a><a name="addtail"></a>CAtlList::AddTail  
 Llamar a este método para agregar un elemento a la cola de esta lista.  
  
```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```  
  
### <a name="parameters"></a>Parámetros  
 `element`  
 Elemento que se va a agregar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición del elemento recién agregado.  
  
### <a name="remarks"></a>Comentarios  
 Si se utiliza la primera versión, se crea un elemento vacío con su constructor predeterminado, en lugar de su constructor de copia. El elemento se agrega al final de la lista y, lo ahora se convierte en la cola. Este método puede utilizarse con una lista vacía.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#15;](../../atl/codesnippet/cpp/catllist-class_3.cpp)]  
  
##  <a name="a-nameaddtaillista--catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList  
 Llamar a este método para agregar una lista existente a la cola de esta lista.  
  
```
void AddTailList(const CAtlList<E, ETraits>* plNew);
```  
  
### <a name="parameters"></a>Parámetros  
 `plNew`  
 La lista que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 La lista que apunta `plNew` se inserta después del último elemento (si existe) del objeto de lista. El último elemento en el `plNew` lista, por tanto, se convierte en la cola. En compilaciones de depuración, se producirá un error de aserción si *plNew* es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&16;](../../atl/codesnippet/cpp/catllist-class_4.cpp)]  
  
##  <a name="a-nameassertvalida--catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid  
 Llamar a este método para confirmar que la lista es válida.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido. Para que sea válida, debe tener una lista vacía la cabeza y el final que apunta a NULL y debe tener una lista que no está vacía la cabeza y el final que apunta a direcciones válidas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#17;](../../atl/codesnippet/cpp/catllist-class_5.cpp)]  
  
##  <a name="a-namecatllista--catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList  
 El constructor.  
  
```
CAtlList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBlockSize`  
 El tamaño del bloque.  
  
### <a name="remarks"></a>Comentarios  
 El constructor para la `CAtlList` objeto. El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Mayores tamaños de bloque reducen las llamadas a rutinas de asignación de memoria, pero utilizan más recursos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#18;](../../atl/codesnippet/cpp/catllist-class_6.cpp)]  
  
##  <a name="a-namedtora--catllistcatllist"></a><a name="dtor"></a>CAtlList:: ~ CAtlList  
 Destructor.  
  
```
~CAtlList() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados, incluida una llamada a [CAtlList::RemoveAll](#removeall) para quitar todos los elementos de la lista.  
  
 En compilaciones de depuración, se producirá un error de aserción si la lista aún contiene algunos elementos después de la llamada a `RemoveAll`.  
  
##  <a name="a-namefinda--catllistfind"></a><a name="find"></a>CAtlList::Find  
 Llame a este método para buscar en la lista para el elemento especificado.  
  
```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `element`  
 El elemento que se encuentra en la lista.  
  
 `posStartAfter`  
 La posición inicial de la búsqueda. Si no se especifica ningún valor, la búsqueda comienza con el elemento de encabezado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la posición del elemento si se encuentra, en caso contrario, devuelve NULL.  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido, o si la `posStartAfter` valor está fuera del intervalo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&19;](../../atl/codesnippet/cpp/catllist-class_7.cpp)]  
  
##  <a name="a-namefindindexa--catllistfindindex"></a><a name="findindex"></a>CAtlList::FindIndex  
 Llame a este método para obtener la posición de un elemento, dado un valor de índice.  
  
```
POSITION FindIndex(size_t iElement) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 Índice de base cero del elemento de lista requerida.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de posición correspondiente, o NULL si `iElement` está fuera del intervalo.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve la posición correspondiente a un valor de índice especificado, permitiendo el acceso a la *n*elemento en la lista.  
  
 En compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#20;](../../atl/codesnippet/cpp/catllist-class_8.cpp)]  
  
##  <a name="a-namegetata--catllistgetat"></a><a name="getat"></a>CAtlList::GetAt  
 Llame a este método para devolver el elemento en una posición especificada en la lista.  
  
```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El valor de posición especifica un elemento determinado.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a, o una copia del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Si la lista es **const**, `GetAt` devuelve una copia del elemento. Esto permite que el método que se utilizará sólo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.  
  
 Si la lista no es **const**, `GetAt` devuelve una referencia al elemento. Esto permite que el método que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
 En compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::FindIndex](#findindex).  
  
##  <a name="a-namegetcounta--catllistgetcount"></a><a name="getcount"></a>CAtlList::GetCount  
 Llame a este método para devolver el número de objetos en la lista.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos de la lista.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::Find](#find).  
  
##  <a name="a-namegetheada--catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead  
 Llame a este método para devolver el elemento situado al principio de la lista.  
  
```
E& GetHead() throw();
const E& GetHead() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a, o una copia del elemento en el encabezado de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Si la lista es **const**, `GetHead` devuelve una copia del elemento en el encabezado de la lista. Esto permite que el método que se utilizará sólo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.  
  
 Si la lista no es **const**, `GetHead` devuelve una referencia al elemento en el encabezado de la lista. Esto permite que el método que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
 En compilaciones de depuración, se producirá un error de aserción si el encabezado de la lista apunta a NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::AddHead](#addhead).  
  
##  <a name="a-namegetheadpositiona--catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition  
 Llame a este método para obtener la posición de la cabeza de la lista.  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la posición correspondiente al elemento situado al principio de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Si la lista está vacía, el valor devuelto es NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_ATL_Utilities](../../atl/codesnippet/cpp/catllist-class_9.cpp)]  
  
##  <a name="a-namegetnexta--catllistgetnext"></a><a name="getnext"></a>CAtlList::GetNext  
 Llame a este método para devolver el siguiente elemento de la lista.  
  
```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Un valor de posición, devuelto por una llamada anterior a `GetNext`, [CAtlList::GetHeadPosition](#getheadposition), u otros `CAtlList` método.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la lista es **const**, `GetNext` devuelve una copia del siguiente elemento de la lista. Esto permite que el método que se utilizará sólo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.  
  
 Si la lista no es **const**, `GetNext` devuelve una referencia al siguiente elemento de la lista. Esto permite que el método que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
### <a name="remarks"></a>Comentarios  
 El contador de posición, `pos`, se actualiza para señalar al elemento siguiente en la lista, o NULL si no hay ningún elemento más. En compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::GetHeadPosition](#getheadposition).  
  
##  <a name="a-namegetpreva--catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev  
 Llame a este método para devolver el elemento anterior de la lista.  
  
```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Un valor de posición, devuelto por una llamada anterior a `GetPrev`, [CAtlList::GetTailPosition](#gettailposition), u otros `CAtlList` método.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la lista es **const**, `GetPrev` devuelve una copia de un elemento de la lista. Esto permite que el método que se utilizará sólo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.  
  
 Si la lista no es **const**, `GetPrev` devuelve una referencia a un elemento de la lista. Esto permite que el método que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
### <a name="remarks"></a>Comentarios  
 El contador de posición, `pos`, se actualiza para señalar al elemento anterior en la lista, o NULL si no hay ningún elemento más. En compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::GetTailPosition](#gettailposition).  
  
##  <a name="a-namegettaila--catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail  
 Llame a este método para devolver el elemento en la cola de la lista.  
  
```
E& GetTail() throw();
const E& GetTail() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a, o una copia del elemento en la cola de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Si la lista es **const**, `GetTail` devuelve una copia del elemento en el encabezado de la lista. Esto permite que el método que se utilizará sólo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.  
  
 Si la lista no es **const**, `GetTail` devuelve una referencia al elemento en el encabezado de la lista. Esto permite que el método que se utilizará en cada lado de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.  
  
 En compilaciones de depuración, se producirá un error de aserción si señala el final de la lista en NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::AddTail](#addtail).  
  
##  <a name="a-namegettailpositiona--catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition  
 Llame a este método para obtener la posición de la cola de la lista.  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la posición correspondiente al elemento del final de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Si la lista está vacía, el valor devuelto es NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#22;](../../atl/codesnippet/cpp/catllist-class_10.cpp)]  
  
##  <a name="a-nameinargtypea--catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE  
 Tipo que se utiliza cuando un elemento se pasa como un argumento de entrada.  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="a-nameinsertaftera--catllistinsertafter"></a><a name="insertafter"></a>CAtlList::InsertAfter  
 Llame a este método para insertar un nuevo elemento en la lista después de la posición especificada.  
  
```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El valor de posición después del cual se insertará el nuevo elemento.  
  
 `element`  
 El elemento que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la posición del nuevo elemento.  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, se producirá un error de aserción si la lista no es válida, si se produce un error en la inserción, o si intenta insertar el elemento detrás del final.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_ATL_Utilities #](../../atl/codesnippet/cpp/catllist-class_11.cpp)]  
  
##  <a name="a-nameinsertbeforea--catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList::InsertBefore  
 Llamar a este método para insertar un nuevo elemento en la lista antes de la posición especificada.  
  
```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Se insertará el nuevo elemento en la lista antes de este valor de posición.  
  
 `element`  
 El elemento que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de la posición del nuevo elemento.  
  
### <a name="remarks"></a>Comentarios  
 En compilaciones de depuración, se producirá un error de aserción si la lista no es válida, si se produce un error en la inserción, o si se realiza un intento para insertar el elemento antes de la cabeza.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#24;](../../atl/codesnippet/cpp/catllist-class_12.cpp)]  
  
##  <a name="a-nameisemptya--catllistisempty"></a><a name="isempty"></a>CAtlList::IsEmpty  
 Llame a este método para determinar si la lista está vacía.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la lista no contiene objetos, de lo contrario, false.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#25;](../../atl/codesnippet/cpp/catllist-class_13.cpp)]  
  
##  <a name="a-namemovetoheada--catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead  
 Llamar a este método para mover el elemento especificado en el encabezado de la lista.  
  
```
void MoveToHead(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El valor de la posición del elemento que se va a mover.  
  
### <a name="remarks"></a>Comentarios  
 El elemento especificado se mueve desde su posición actual en el encabezado de la lista. En compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_ATL_Utilities #](../../atl/codesnippet/cpp/catllist-class_14.cpp)]  
  
##  <a name="a-namemovetotaila--catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail  
 Llamar a este método para mover el elemento especificado a la cola de la lista.  
  
```
void MoveToTail(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El valor de la posición del elemento que se va a mover.  
  
### <a name="remarks"></a>Comentarios  
 El elemento especificado se mueve desde su posición actual hasta el final de la lista. En compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::MoveToHead](#movetohead).  
  
##  <a name="a-nameremovealla--catllistremoveall"></a><a name="removeall"></a>CAtlList::RemoveAll  
 Llame a este método para quitar todos los elementos de la lista.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método quita todos los elementos de la lista y libera la memoria asignada. En las compilaciones depura, se generará una ATLASSERT si no se eliminan todos los elementos o si se ha dañado la estructura de la lista.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::IsEmpty](#isempty).  
  
##  <a name="a-nameremoveata--catllistremoveat"></a><a name="removeat"></a>CAtlList::RemoveAt  
 Llame a este método para quitar un único elemento de la lista.  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El valor de la posición del elemento que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 El elemento al que hace referencia `pos` se quita, y se libera memoria. Es aceptable utilizar `RemoveAt` para quitar el encabezado o el final de la lista.  
  
 En compilaciones de depuración, se producirá un error de aserción si la lista no es válida o quitar el elemento, la lista en memoria de acceso que no forma parte de la estructura de la lista.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&27;](../../atl/codesnippet/cpp/catllist-class_15.cpp)]  
  
##  <a name="a-nameremoveheada--catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead  
 Llame a este método para quitar el elemento situado al principio de la lista.  
  
```
E RemoveHead();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el elemento situado al principio de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Se elimina el elemento de encabezado de la lista y se libera memoria. Se devuelve una copia del elemento. En compilaciones de depuración, se producirá un error de aserción si la lista está vacía.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#28;](../../atl/codesnippet/cpp/catllist-class_16.cpp)]  
  
##  <a name="a-nameremoveheadnoreturna--catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn  
 Llame a este método para quitar el elemento situado al principio de la lista sin devolver un valor.  
  
```
void RemoveHeadNoReturn() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Se elimina el elemento de encabezado de la lista y se libera memoria. En compilaciones de depuración, se producirá un error de aserción si la lista está vacía.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::IsEmpty](#isempty).  
  
##  <a name="a-nameremovetaila--catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail  
 Llame a este método para quitar el elemento del final de la lista.  
  
```
E RemoveTail();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el elemento en la cola de la lista.  
  
### <a name="remarks"></a>Comentarios  
 Se elimina el elemento final de la lista y se libera memoria. Se devuelve una copia del elemento. En compilaciones de depuración, se producirá un error de aserción si la lista está vacía.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#29;](../../atl/codesnippet/cpp/catllist-class_17.cpp)]  
  
##  <a name="a-nameremovetailnoreturna--catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn  
 Llame a este método para quitar el elemento del final de la lista sin devolver un valor.  
  
```
void RemoveTailNoReturn() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Se elimina el elemento final de la lista y se libera memoria. En compilaciones de depuración, se producirá un error de aserción si la lista está vacía.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlList::IsEmpty](#isempty).  
  
##  <a name="a-namesetata--catllistsetat"></a><a name="setat"></a>CAtlList::SetAt  
 Llamar a este método para establecer el valor del elemento en una posición determinada en la lista.  
  
```
void SetAt(POSITION pos, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El valor de la posición correspondiente para el elemento que se va a cambiar.  
  
 `element`  
 El nuevo valor del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Reemplaza el valor existente con `element`. En compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&30;](../../atl/codesnippet/cpp/catllist-class_18.cpp)]  
  
##  <a name="a-nameswapelementsa--catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements  
 Llamar a este método para intercambiar los elementos de la lista.  
  
```
void SwapElements(POSITION pos1, POSITION pos2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *POS1*  
 El primer valor de posición.  
  
 *POS2*  
 El segundo valor de posición.  
  
### <a name="remarks"></a>Comentarios  
 Intercambia los elementos en las dos posiciones especificadas. En compilaciones de depuración, se producirá un error de aserción si cualquier valor de posición es igual a NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#31;](../../atl/codesnippet/cpp/catllist-class_19.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CList (clase)](../../mfc/reference/clist-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

