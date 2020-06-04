---
title: Clase CAtlList
ms.date: 11/04/2016
f1_keywords:
- CAtlList
- ATLCOLL/ATL::CAtlList
- ATLCOLL/ATL::CAtlList::INARGTYPE
- ATLCOLL/ATL::CAtlList::CAtlList
- ATLCOLL/ATL::CAtlList::AddHead
- ATLCOLL/ATL::CAtlList::AddHeadList
- ATLCOLL/ATL::CAtlList::AddTail
- ATLCOLL/ATL::CAtlList::AddTailList
- ATLCOLL/ATL::CAtlList::AssertValid
- ATLCOLL/ATL::CAtlList::Find
- ATLCOLL/ATL::CAtlList::FindIndex
- ATLCOLL/ATL::CAtlList::GetAt
- ATLCOLL/ATL::CAtlList::GetCount
- ATLCOLL/ATL::CAtlList::GetHead
- ATLCOLL/ATL::CAtlList::GetHeadPosition
- ATLCOLL/ATL::CAtlList::GetNext
- ATLCOLL/ATL::CAtlList::GetPrev
- ATLCOLL/ATL::CAtlList::GetTail
- ATLCOLL/ATL::CAtlList::GetTailPosition
- ATLCOLL/ATL::CAtlList::InsertAfter
- ATLCOLL/ATL::CAtlList::InsertBefore
- ATLCOLL/ATL::CAtlList::IsEmpty
- ATLCOLL/ATL::CAtlList::MoveToHead
- ATLCOLL/ATL::CAtlList::MoveToTail
- ATLCOLL/ATL::CAtlList::RemoveAll
- ATLCOLL/ATL::CAtlList::RemoveAt
- ATLCOLL/ATL::CAtlList::RemoveHead
- ATLCOLL/ATL::CAtlList::RemoveHeadNoReturn
- ATLCOLL/ATL::CAtlList::RemoveTail
- ATLCOLL/ATL::CAtlList::RemoveTailNoReturn
- ATLCOLL/ATL::CAtlList::SetAt
- ATLCOLL/ATL::CAtlList::SwapElements
helpviewer_keywords:
- CAtlList class
ms.assetid: 09e98053-64b2-4efa-99ab-d0542caaf981
ms.openlocfilehash: 2c16713af11a915772085165ed294cba4ae337f2
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168051"
---
# <a name="catllist-class"></a>Clase CAtlList

Esta clase proporciona métodos para crear y administrar un objeto de lista.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

### <a name="parameters"></a>Parámetros

*E:.*<br/>
El tipo de elemento.

*ETraits*<br/>
Código que se usa para copiar o quitar elementos. Consulte [clase CElementTraits](../../atl/reference/celementtraits-class.md) para obtener más detalles.

## <a name="members"></a>Members

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
|[CAtlList::AddHead](#addhead)|Llame a este método para agregar un elemento al encabezado de la lista.|
|[CAtlList::AddHeadList](#addheadlist)|Llame a este método para agregar una lista existente al encabezado de la lista.|
|[CAtlList:: Addtail (](#addtail)|Llame a este método para agregar un elemento al final de esta lista.|
|[CAtlList::AddTailList](#addtaillist)|Llame a este método para agregar una lista existente al final de esta lista.|
|[CAtlList:: AssertValid](#assertvalid)|Llame a este método para confirmar que la lista es válida.|
|[CAtlList:: Find](#find)|Llame a este método para buscar el elemento especificado en la lista.|
|[CAtlList:: FindIndex](#findindex)|Llame a este método para obtener la posición de un elemento, dado un valor de índice.|
|[CAtlList:: GetAt](#getat)|Llame a este método para devolver el elemento en una posición especificada de la lista.|
|[CAtlList:: GetCount](#getcount)|Llame a este método para devolver el número de objetos de la lista.|
|[CAtlList::GetHead](#gethead)|Llame a este método para devolver el elemento en el encabezado de la lista.|
|[CAtlList::GetHeadPosition](#getheadposition)|Llame a este método para obtener la posición del encabezado de la lista.|
|[CAtlList:: GetNext](#getnext)|Llame a este método para devolver el siguiente elemento de la lista.|
|[CAtlList::GetPrev](#getprev)|Llame a este método para devolver el elemento anterior de la lista.|
|[CAtlList::GetTail](#gettail)|Llame a este método para devolver el elemento en la cola de la lista.|
|[CAtlList::GetTailPosition](#gettailposition)|Llame a este método para obtener la posición del final de la lista.|
|[CAtlList:: InsertAfter](#insertafter)|Llame a este método para insertar un nuevo elemento en la lista después de la posición especificada.|
|[CAtlList:: InsertBefore](#insertbefore)|Llame a este método para insertar un nuevo elemento en la lista antes de la posición especificada.|
|[CAtlList:: IsEmpty](#isempty)|Llame a este método para determinar si la lista está vacía.|
|[CAtlList::MoveToHead](#movetohead)|Llame a este método para trasladar el elemento especificado al encabezado de la lista.|
|[CAtlList::MoveToTail](#movetotail)|Llame a este método para trasladar el elemento especificado al final de la lista.|
|[CAtlList:: RemoveAll](#removeall)|Llame a este método para quitar todos los elementos de la lista.|
|[CAtlList:: RemoveAt](#removeat)|Llame a este método para quitar un solo elemento de la lista.|
|[CAtlList::RemoveHead](#removehead)|Llame a este método para quitar el elemento situado en el encabezado de la lista.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Llame a este método para quitar el elemento del encabezado de la lista sin devolver un valor.|
|[CAtlList::RemoveTail](#removetail)|Llame a este método para quitar el elemento en la cola de la lista.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Llame a este método para quitar el elemento en la cola de la lista sin devolver un valor.|
|[CAtlList:: SetAt](#setat)|Llame a este método para establecer el valor del elemento en una posición determinada de la lista.|
|[CAtlList::SwapElements](#swapelements)|Llame a este método para intercambiar los elementos de la lista.|

## <a name="remarks"></a>Observaciones

La `CAtlList` clase admite listas ordenadas de objetos no únicos accesibles secuencialmente o por valor. `CAtlList`las listas se comportan como listas de doble vínculo. Cada lista tiene un encabezado y una cola, y se pueden agregar nuevos elementos (o listas en algunos casos) al final de la lista, o bien insertarse antes o después de elementos específicos.

La mayoría de `CAtlList` los métodos hacen uso de un valor de posición. Los métodos utilizan este valor para hacer referencia a la ubicación de memoria real en la que se almacenan los elementos y no deben calcularse ni predecirse directamente. Si es necesario tener acceso al elemento *n*de la lista, el método [CAtlList:: FindIndex](#findindex) devolverá el valor de posición correspondiente para un índice determinado. Los métodos [CAtlList:: Getnext](#getnext) y [CAtlList:: GetPrev](#getprev) se pueden usar para recorrer en iteración los objetos de la lista.

Para obtener más información sobre las clases de colección disponibles con ATL, vea [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll. h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead

Llame a este método para agregar un elemento al encabezado de la lista.

```cpp
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*Element*<br/>
Nuevo elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del elemento recién agregado.

### <a name="remarks"></a>Observaciones

Si se usa la primera versión, se crea un elemento vacío usando su constructor predeterminado, en lugar de su constructor de copias.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

Llame a este método para agregar una lista existente al encabezado de la lista.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parámetros

*plNew*<br/>
Lista que se va a agregar.

### <a name="remarks"></a>Observaciones

La lista a la que señala *plNew* se inserta al principio de la lista existente. En las compilaciones de depuración, se producirá un error de aserción si *plNew* es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList:: Addtail (

Llame a este método para agregar un elemento al final de esta lista.

```cpp
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*Element*<br/>
Elemento que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del elemento recién agregado.

### <a name="remarks"></a>Observaciones

Si se usa la primera versión, se crea un elemento vacío usando su constructor predeterminado, en lugar de su constructor de copias. El elemento se agrega al final de la lista, por lo que ahora se convierte en la cola. Este método se puede usar con una lista vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

Llame a este método para agregar una lista existente al final de esta lista.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parámetros

*plNew*<br/>
Lista que se va a agregar.

### <a name="remarks"></a>Observaciones

La lista a la que señala *plNew* se inserta después del último elemento (si existe) en el objeto de lista. Por lo tanto, el último elemento de la lista *plNew* se convierte en el final. En las compilaciones de depuración, se producirá un error de aserción si *plNew* es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList:: AssertValid

Llame a este método para confirmar que la lista es válida.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido. Para ser válido, una lista vacía debe tener el encabezado y la cola que apuntan a NULL, y una lista que no esté vacía debe tener el encabezado y la cola que apuntan a direcciones válidas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

El constructor.

```cpp
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Tamaño de bloque.

### <a name="remarks"></a>Observaciones

Constructor para el `CAtlList` objeto. El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList:: ~ CAtlList

Destructor.

```cpp
~CAtlList() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados, incluida una llamada a [CAtlList:: RemoveAll](#removeall) para quitar todos los elementos de la lista.

En las compilaciones de depuración, se producirá un error de aserción si la lista todavía `RemoveAll`contiene algunos elementos después de la llamada a.

## <a name="catllistfind"></a><a name="find"></a>CAtlList:: Find

Llame a este método para buscar el elemento especificado en la lista.

```cpp
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*Element*<br/>
Elemento que se va a buscar en la lista.

*posStartAfter*<br/>
Posición inicial de la búsqueda. Si no se especifica ningún valor, la búsqueda comienza con el elemento de encabezado.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición del elemento si se encuentra; de lo contrario, devuelve NULL.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido o si el valor de *posStartAfter* está fuera del intervalo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList:: FindIndex

Llame a este método para obtener la posición de un elemento, dado un valor de índice.

```cpp
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
Índice de base cero del elemento de lista necesario.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de la posición correspondiente, o NULL si *IElement* está fuera del intervalo.

### <a name="remarks"></a>Observaciones

Este método devuelve la posición correspondiente a un valor de índice dado, lo que permite el acceso al elemento *n*de la lista.

En las compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList:: GetAt

Llame a este método para devolver el elemento en una posición especificada de la lista.

```cpp
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
Valor de posición que especifica un elemento determinado.

### <a name="return-value"></a>Valor devuelto

Referencia al elemento, o copia de él.

### <a name="remarks"></a>Observaciones

Si la lista es **const**, `GetAt` devuelve una copia del elemento. Esto permite que el método se use solo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.

Si la lista no es **const**, `GetAt` devuelve una referencia al elemento. Esto permite que el método se use en cualquier lado de una instrucción de asignación y, por tanto, permite que se modifiquen las entradas de la lista.

En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: FindIndex](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList:: GetCount

Llame a este método para devolver el número de objetos de la lista.

```cpp
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos de la lista.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: Find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead

Llame a este método para devolver el elemento en el encabezado de la lista.

```cpp
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a, o una copia de, del elemento en el encabezado de la lista.

### <a name="remarks"></a>Observaciones

Si la lista es **const**, `GetHead` devuelve una copia del elemento en el encabezado de la lista. Esto permite que el método se use solo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.

Si la lista no es **const**, `GetHead` devuelve una referencia al elemento en el encabezado de la lista. Esto permite que el método se use en cualquier lado de una instrucción de asignación y, por tanto, permite que se modifiquen las entradas de la lista.

En las compilaciones de depuración, se producirá un error de aserción si el encabezado de la lista apunta a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: AddHead](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

Llame a este método para obtener la posición del encabezado de la lista.

```cpp
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición correspondiente al elemento en el encabezado de la lista.

### <a name="remarks"></a>Observaciones

Si la lista está vacía, el valor devuelto es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList:: GetNext

Llame a este método para devolver el siguiente elemento de la lista.

```cpp
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
Un valor de posición, devuelto por una llamada `GetNext`anterior a, [CAtlList:: GetHeadPosition](#getheadposition)u `CAtlList` otro método.

### <a name="return-value"></a>Valor devuelto

Si la lista es **const**, `GetNext` devuelve una copia del siguiente elemento de la lista. Esto permite que el método se use solo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.

Si la lista no es **const**, `GetNext` devuelve una referencia al siguiente elemento de la lista. Esto permite que el método se use en cualquier lado de una instrucción de asignación y, por tanto, permite que se modifiquen las entradas de la lista.

### <a name="remarks"></a>Observaciones

El contador de posición, *pos*, se actualiza para señalar al siguiente elemento de la lista o null si no hay más elementos. En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev

Llame a este método para devolver el elemento anterior de la lista.

```cpp
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
Un valor de posición, devuelto por una llamada `GetPrev`anterior a, [CAtlList:: GetTailPosition](#gettailposition)u `CAtlList` otro método.

### <a name="return-value"></a>Valor devuelto

Si la lista es **const**, `GetPrev` devuelve una copia de un elemento de la lista. Esto permite que el método se use solo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.

Si la lista no es **const**, `GetPrev` devuelve una referencia a un elemento de la lista. Esto permite que el método se use en cualquier lado de una instrucción de asignación y, por tanto, permite que se modifiquen las entradas de la lista.

### <a name="remarks"></a>Observaciones

El contador de posición, *pos*, se actualiza para señalar al elemento anterior de la lista o null si no hay más elementos. En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail

Llame a este método para devolver el elemento en la cola de la lista.

```cpp
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a, o una copia de, del elemento en la cola de la lista.

### <a name="remarks"></a>Observaciones

Si la lista es **const**, `GetTail` devuelve una copia del elemento en el encabezado de la lista. Esto permite que el método se use solo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.

Si la lista no es **const**, `GetTail` devuelve una referencia al elemento en el encabezado de la lista. Esto permite que el método se use en cualquier lado de una instrucción de asignación y, por tanto, permite que se modifiquen las entradas de la lista.

En las compilaciones de depuración, se producirá un error de aserción si el final de la lista apunta a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: addtail (](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

Llame a este método para obtener la posición del final de la lista.

```cpp
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición correspondiente al elemento en el final de la lista.

### <a name="remarks"></a>Observaciones

Si la lista está vacía, el valor devuelto es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

Tipo usado cuando se pasa un elemento como argumento de entrada.

```cpp
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList:: InsertAfter

Llame a este método para insertar un nuevo elemento en la lista después de la posición especificada.

```cpp
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
Valor de posición después del cual se insertará el nuevo elemento.

*Element*<br/>
Elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición del nuevo elemento.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si la lista no es válida, si se produce un error en la inserción o si se realiza un intento de insertar el elemento después de la cola.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList:: InsertBefore

Llame a este método para insertar un nuevo elemento en la lista antes de la posición especificada.

```cpp
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
El nuevo elemento se insertará en la lista antes de este valor de posición.

*Element*<br/>
Elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de posición del nuevo elemento.

### <a name="remarks"></a>Observaciones

En las compilaciones de depuración, se producirá un error de aserción si la lista no es válida, si se produce un error en la inserción o si se realiza un intento de insertar el elemento delante del encabezado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList:: IsEmpty

Llame a este método para determinar si la lista está vacía.

```cpp
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si la lista no contiene ningún objeto; de lo contrario, es false.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

Llame a este método para trasladar el elemento especificado al encabezado de la lista.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
Valor de posición del elemento que se va a mover.

### <a name="remarks"></a>Observaciones

El elemento especificado se mueve de su posición actual al encabezado de la lista. En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

Llame a este método para trasladar el elemento especificado al final de la lista.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
Valor de posición del elemento que se va a mover.

### <a name="remarks"></a>Observaciones

El elemento especificado se mueve desde su posición actual hasta el final de la lista. En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList:: RemoveAll

Llame a este método para quitar todos los elementos de la lista.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Observaciones

Este método quita todos los elementos de la lista y libera la memoria asignada. En el caso de las compilaciones de depuración, se generará una ATLASSERT si no se eliminan todos los elementos o si la estructura de la lista se ha dañado.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList:: RemoveAt

Llame a este método para quitar un solo elemento de la lista.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
Valor de posición del elemento que se va a quitar.

### <a name="remarks"></a>Observaciones

Se quita el elemento al que hace referencia *pos* y se libera la memoria. Es aceptable usar `RemoveAt` para quitar el encabezado o la cola de la lista.

En las compilaciones de depuración, se producirá un error de aserción si la lista no es válida o si al quitar el elemento hace que la lista tenga acceso a la memoria que no forma parte de la estructura de la lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

Llame a este método para quitar el elemento situado en el encabezado de la lista.

```cpp
E RemoveHead();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el elemento situado en el encabezado de la lista.

### <a name="remarks"></a>Observaciones

El elemento de encabezado se elimina de la lista y se libera la memoria. Se devuelve una copia del elemento. En las compilaciones de depuración, se producirá un error de aserción si la lista está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

Llame a este método para quitar el elemento del encabezado de la lista sin devolver un valor.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Observaciones

El elemento de encabezado se elimina de la lista y se libera la memoria. En las compilaciones de depuración, se producirá un error de aserción si la lista está vacía.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

Llame a este método para quitar el elemento en la cola de la lista.

```cpp
E RemoveTail();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el elemento situado en el final de la lista.

### <a name="remarks"></a>Observaciones

El elemento tail se elimina de la lista y se libera la memoria. Se devuelve una copia del elemento. En las compilaciones de depuración, se producirá un error de aserción si la lista está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

Llame a este método para quitar el elemento en la cola de la lista sin devolver un valor.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Observaciones

El elemento tail se elimina de la lista y se libera la memoria. En las compilaciones de depuración, se producirá un error de aserción si la lista está vacía.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList:: IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList:: SetAt

Llame a este método para establecer el valor del elemento en una posición determinada de la lista.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*abre*<br/>
Valor de posición correspondiente al elemento que se va a cambiar.

*Element*<br/>
Nuevo valor del elemento.

### <a name="remarks"></a>Observaciones

Reemplaza el valor existente por el *elemento*. En las compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

Llame a este método para intercambiar los elementos de la lista.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parámetros

*pos1*<br/>
Valor de la primera posición.

*pos2*<br/>
Segundo valor de posición.

### <a name="remarks"></a>Observaciones

Intercambia los elementos de las dos posiciones especificadas. En las compilaciones de depuración, se producirá un error de aserción si alguno de los valores de posición es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Consulte también

[CList (clase)](../../mfc/reference/clist-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
