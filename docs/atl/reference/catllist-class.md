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
ms.openlocfilehash: 0e4ea8eef51431c100f5d3119d7f75e9673e276e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748738"
---
# <a name="catllist-class"></a>Clase CAtlList

Esta clase proporciona métodos para crear y administrar un objeto de lista.

## <a name="syntax"></a>Sintaxis

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlList
```

#### <a name="parameters"></a>Parámetros

*E*<br/>
El tipo de elemento.

*ETraits*<br/>
El código utilizado para copiar o mover elementos. Consulte [CElementTraits (Clase)](../../atl/reference/celementtraits-class.md) para obtener más detalles.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CAtlList::INARGTYPE](#inargtype)||

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlList::CAtlList](#catllist)|El constructor.|
|[CAtlList::-CAtlList](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlList::AddHead](#addhead)|Llame a este método para agregar un elemento al jefe de la lista.|
|[CAtlList::AddHeadList](#addheadlist)|Llame a este método para agregar una lista existente al jefe de la lista.|
|[CAtlList::AddTail](#addtail)|Llame a este método para agregar un elemento a la cola de esta lista.|
|[CAtlList::AddTailList](#addtaillist)|Llame a este método para agregar una lista existente a la cola de esta lista.|
|[CAtlList::AssertValid](#assertvalid)|Llame a este método para confirmar que la lista es válida.|
|[CAtlList::Buscar](#find)|Llame a este método para buscar en la lista el elemento especificado.|
|[CAtlList::FindIndex](#findindex)|Llame a este método para obtener la posición de un elemento, dado un valor de índice.|
|[CAtlList::GetAt](#getat)|Llame a este método para devolver el elemento en una posición especificada en la lista.|
|[CAtlList::GetCount](#getcount)|Llame a este método para devolver el número de objetos de la lista.|
|[CAtlList::GetHead](#gethead)|Llame a este método para devolver el elemento en la cabecera de la lista.|
|[CAtlList::GetHeadPosition](#getheadposition)|Llame a este método para obtener la posición del jefe de la lista.|
|[CAtlList::GetNext](#getnext)|Llame a este método para devolver el siguiente elemento de la lista.|
|[CAtlList::GetPrev](#getprev)|Llame a este método para devolver el elemento anterior de la lista.|
|[CAtlList::GetTail](#gettail)|Llame a este método para devolver el elemento en la cola de la lista.|
|[CAtlList::GetTailPosition](#gettailposition)|Llame a este método para obtener la posición de la cola de la lista.|
|[CAtlList::InsertAfter](#insertafter)|Llame a este método para insertar un nuevo elemento en la lista después de la posición especificada.|
|[CAtlList::InsertBefore](#insertbefore)|Llame a este método para insertar un nuevo elemento en la lista antes de la posición especificada.|
|[CAtlList::IsEmpty](#isempty)|Llame a este método para determinar si la lista está vacía.|
|[CAtlList::MoveToHead](#movetohead)|Llame a este método para mover el elemento especificado al jefe de la lista.|
|[CAtlList::MoveToTail](#movetotail)|Llame a este método para mover el elemento especificado a la cola de la lista.|
|[CAtlList::RemoveAll](#removeall)|Llame a este método para quitar todos los elementos de la lista.|
|[CAtlList::RemoveAt](#removeat)|Llame a este método para quitar un solo elemento de la lista.|
|[CAtlList::RemoveHead](#removehead)|Llame a este método para quitar el elemento en la cabecera de la lista.|
|[CAtlList::RemoveHeadNoReturn](#removeheadnoreturn)|Llame a este método para quitar el elemento en la cabecera de la lista sin devolver un valor.|
|[CAtlList::RemoveTail](#removetail)|Llame a este método para quitar el elemento en la cola de la lista.|
|[CAtlList::RemoveTailNoReturn](#removetailnoreturn)|Llame a este método para quitar el elemento en la cola de la lista sin devolver un valor.|
|[CAtlList::SetAt](#setat)|Llame a este método para establecer el valor del elemento en una posición determinada de la lista.|
|[CAtlList::SwapElements](#swapelements)|Llame a este método para intercambiar elementos en la lista.|

## <a name="remarks"></a>Observaciones

La `CAtlList` clase admite listas ordenadas de objetos no únicos accesibles secuencialmente o por valor. `CAtlList`las listas se comportan como listas doblemente vinculadas. Cada lista tiene una cabeza y una cola, y se pueden agregar nuevos elementos (o listas en algunos casos) a cualquiera de los extremos de la lista, o insertarse antes o después de elementos específicos.

La mayoría `CAtlList` de los métodos hacen uso de un valor de posición. Los métodos utilizan este valor para hacer referencia a la ubicación de memoria real donde se almacenan los elementos y no se debe calcular ni predecir directamente. Si es necesario tener acceso al *n*ésimo elemento de la lista, el método [CAtlList::FindIndex](#findindex) devolverá el valor de posición correspondiente para un índice determinado. Los métodos [CAtlList::GetNext](#getnext) y [CAtlList::GetPrev](#getprev) se pueden utilizar para recorrer en iteración los objetos de la lista.

Para obtener más información sobre las clases de colección disponibles con ATL, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="catllistaddhead"></a><a name="addhead"></a>CAtlList::AddHead

Llame a este método para agregar un elemento al jefe de la lista.

```
POSITION AddHead();
POSITION AddHead(INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*Elemento*<br/>
Nuevo elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve la posición del elemento recién agregado.

### <a name="remarks"></a>Observaciones

Si se utiliza la primera versión, se crea un elemento vacío utilizando su constructor predeterminado, en lugar de su constructor de copia.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#13](../../atl/codesnippet/cpp/catllist-class_1.cpp)]

## <a name="catllistaddheadlist"></a><a name="addheadlist"></a>CAtlList::AddHeadList

Llame a este método para agregar una lista existente al jefe de la lista.

```cpp
void AddHeadList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parámetros

*plNew*<br/>
Lista que se va a agregar.

### <a name="remarks"></a>Observaciones

La lista señalada por *plNew* se inserta al principio de la lista existente. En compilaciones de depuración, se producirá un error de aserción si *plNew* es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#14](../../atl/codesnippet/cpp/catllist-class_2.cpp)]

## <a name="catllistaddtail"></a><a name="addtail"></a>CAtlList::AddTail

Llame a este método para agregar un elemento a la cola de esta lista.

```
POSITION AddTail();
POSITION AddTail(INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*Elemento*<br/>
Elemento que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Devuelve la POSITION del elemento recién agregado.

### <a name="remarks"></a>Observaciones

Si se utiliza la primera versión, se crea un elemento vacío utilizando su constructor predeterminado, en lugar de su constructor de copia. El elemento se agrega al final de la lista, por lo que ahora se convierte en la cola. Este método se puede utilizar con una lista vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#15](../../atl/codesnippet/cpp/catllist-class_3.cpp)]

## <a name="catllistaddtaillist"></a><a name="addtaillist"></a>CAtlList::AddTailList

Llame a este método para agregar una lista existente a la cola de esta lista.

```cpp
void AddTailList(const CAtlList<E, ETraits>* plNew);
```

### <a name="parameters"></a>Parámetros

*plNew*<br/>
Lista que se va a agregar.

### <a name="remarks"></a>Observaciones

La lista señalada por *plNew* se inserta después del último elemento (si existe) en el objeto de lista. Por lo tanto, el último elemento de la lista *plNew* se convierte en la cola. En compilaciones de depuración, se producirá un error de aserción si *plNew* es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#16](../../atl/codesnippet/cpp/catllist-class_4.cpp)]

## <a name="catllistassertvalid"></a><a name="assertvalid"></a>CAtlList::AssertValid

Llame a este método para confirmar que la lista es válida.

```cpp
void AssertValid() const;
```

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido. Para ser válida, una lista vacía debe tener la cabeza y la cola que apunten a NULL, y una lista que no está vacía debe tener la cabeza y la cola que apunten a direcciones válidas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#17](../../atl/codesnippet/cpp/catllist-class_5.cpp)]

## <a name="catllistcatllist"></a><a name="catllist"></a>CAtlList::CAtlList

El constructor.

```
CAtlList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Tamaño de bloque.

### <a name="remarks"></a>Observaciones

El constructor `CAtlList` del objeto. El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#18](../../atl/codesnippet/cpp/catllist-class_6.cpp)]

## <a name="catllistcatllist"></a><a name="dtor"></a>CAtlList::-CAtlList

Destructor.

```
~CAtlList() throw();
```

### <a name="remarks"></a>Observaciones

Libera todos los recursos asignados, incluida una llamada a [CAtlList::RemoveAll](#removeall) para quitar todos los elementos de la lista.

En compilaciones de depuración, se producirá un error de `RemoveAll`aserción si la lista todavía contiene algunos elementos después de la llamada a .

## <a name="catllistfind"></a><a name="find"></a>CAtlList::Buscar

Llame a este método para buscar en la lista el elemento especificado.

```
POSITION Find(INARGTYPE element, POSITION posStartAfter = NULL) const throw();
```

### <a name="parameters"></a>Parámetros

*Elemento*<br/>
El elemento que se encuentra en la lista.

*posStartAfter*<br/>
La posición inicial de la búsqueda. Si no se especifica ningún valor, la búsqueda comienza con el elemento head.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor POSITION del elemento si se encuentra, de lo contrario devuelve NULL.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido o si el valor *posStartAfter* está fuera del intervalo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#19](../../atl/codesnippet/cpp/catllist-class_7.cpp)]

## <a name="catllistfindindex"></a><a name="findindex"></a>CAtlList::FindIndex

Llame a este método para obtener la posición de un elemento, dado un valor de índice.

```
POSITION FindIndex(size_t iElement) const throw();
```

### <a name="parameters"></a>Parámetros

*iElement*<br/>
El índice de base cero del elemento de lista requerido.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor POSITION correspondiente, o NULL si *iElement* está fuera del intervalo.

### <a name="remarks"></a>Observaciones

Este método devuelve la POSITION correspondiente a un valor de índice determinado, lo que permite el acceso al elemento *n*th de la lista.

En compilaciones de depuración, se producirá un error de aserción si el objeto de lista no es válido.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#20](../../atl/codesnippet/cpp/catllist-class_8.cpp)]

## <a name="catllistgetat"></a><a name="getat"></a>CAtlList::GetAt

Llame a este método para devolver el elemento en una posición especificada en la lista.

```
E& GetAt(POSITION pos) throw();
const E& GetAt(POSITION pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El valor POSITION que especifica un elemento determinado.

### <a name="return-value"></a>Valor devuelto

Una referencia o copia del elemento.

### <a name="remarks"></a>Observaciones

Si la lista es `GetAt` **const**, devuelve una copia del elemento. Esto permite que el método se utilice solo en el lado derecho de una instrucción de asignación y protege la lista de modificaciones.

Si la lista no es `GetAt` **const**, devuelve una referencia al elemento. Esto permite que el método se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::FindIndex](#findindex).

## <a name="catllistgetcount"></a><a name="getcount"></a>CAtlList::GetCount

Llame a este método para devolver el número de objetos de la lista.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos de la lista.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::Find](#find).

## <a name="catllistgethead"></a><a name="gethead"></a>CAtlList::GetHead

Llame a este método para devolver el elemento en la cabecera de la lista.

```
E& GetHead() throw();
const E& GetHead() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia o una copia del elemento en el jefe de la lista.

### <a name="remarks"></a>Observaciones

Si la lista es `GetHead` **const**, devuelve una copia del elemento en la cabecera de la lista. Esto permite que el método se utilice solo en el lado derecho de una instrucción de asignación y protege la lista de modificaciones.

Si la lista no es `GetHead` **const**, devuelve una referencia al elemento en la cabecera de la lista. Esto permite que el método se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

En compilaciones de depuración, se producirá un error de aserción si el jefe de la lista apunta a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::AddHead](#addhead).

## <a name="catllistgetheadposition"></a><a name="getheadposition"></a>CAtlList::GetHeadPosition

Llame a este método para obtener la posición del jefe de la lista.

```
POSITION GetHeadPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor POSITION correspondiente al elemento en la cabecera de la lista.

### <a name="remarks"></a>Observaciones

Si la lista está vacía, el valor devuelto es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#21](../../atl/codesnippet/cpp/catllist-class_9.cpp)]

## <a name="catllistgetnext"></a><a name="getnext"></a>CAtlList::GetNext

Llame a este método para devolver el siguiente elemento de la lista.

```
E& GetNext(POSITION& pos) throw();
const E& GetNext(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Un valor POSITION, devuelto por `GetNext`una llamada anterior a , [CAtlList::GetHeadPosition](#getheadposition)u otro `CAtlList` método.

### <a name="return-value"></a>Valor devuelto

Si la lista es `GetNext` **const**, devuelve una copia del siguiente elemento de la lista. Esto permite que el método se utilice solo en el lado derecho de una instrucción de asignación y protege la lista de modificaciones.

Si la lista no es `GetNext` **const**, devuelve una referencia al siguiente elemento de la lista. Esto permite que el método se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

El contador POSITION, *pos*, se actualiza para que apunte al siguiente elemento de la lista, o NULL si no hay más elementos. En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::GetHeadPosition](#getheadposition).

## <a name="catllistgetprev"></a><a name="getprev"></a>CAtlList::GetPrev

Llame a este método para devolver el elemento anterior de la lista.

```
E& GetPrev(POSITION& pos) throw();
const E& GetPrev(POSITION& pos) const throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Un valor POSITION, devuelto por `GetPrev`una llamada anterior a , [CAtlList::GetTailPosition](#gettailposition)u otro `CAtlList` método.

### <a name="return-value"></a>Valor devuelto

Si la lista es `GetPrev` **const**, devuelve una copia de un elemento de la lista. Esto permite que el método se utilice solo en el lado derecho de una instrucción de asignación y protege la lista de modificaciones.

Si la lista no es `GetPrev` **const**, devuelve una referencia a un elemento de la lista. Esto permite que el método se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

El contador POSITION, *pos*, se actualiza para que apunte al elemento anterior de la lista, o NULL si no hay más elementos. En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::GetTailPosition](#gettailposition).

## <a name="catllistgettail"></a><a name="gettail"></a>CAtlList::GetTail

Llame a este método para devolver el elemento en la cola de la lista.

```
E& GetTail() throw();
const E& GetTail() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia o una copia del elemento en la cola de la lista.

### <a name="remarks"></a>Observaciones

Si la lista es `GetTail` **const**, devuelve una copia del elemento en la cabecera de la lista. Esto permite que el método se utilice solo en el lado derecho de una instrucción de asignación y protege la lista de modificaciones.

Si la lista no es `GetTail` **const**, devuelve una referencia al elemento en la cabecera de la lista. Esto permite que el método se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

En compilaciones de depuración, se producirá un error de aserción si la cola de la lista apunta a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::AddTail](#addtail).

## <a name="catllistgettailposition"></a><a name="gettailposition"></a>CAtlList::GetTailPosition

Llame a este método para obtener la posición de la cola de la lista.

```
POSITION GetTailPosition() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor POSITION correspondiente al elemento en la cola de la lista.

### <a name="remarks"></a>Observaciones

Si la lista está vacía, el valor devuelto es NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#22](../../atl/codesnippet/cpp/catllist-class_10.cpp)]

## <a name="catllistinargtype"></a><a name="inargtype"></a>CAtlList::INARGTYPE

Tipo utilizado cuando se pasa un elemento como argumento de entrada.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catllistinsertafter"></a><a name="insertafter"></a>CAtlList::InsertAfter

Llame a este método para insertar un nuevo elemento en la lista después de la posición especificada.

```
POSITION InsertAfter(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El valor POSITION después del cual se insertará el nuevo elemento.

*Elemento*<br/>
El elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor POSITION del nuevo elemento.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si la lista no es válida, si se produce un error en la inserción o si se intenta insertar el elemento después de la cola.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#23](../../atl/codesnippet/cpp/catllist-class_11.cpp)]

## <a name="catllistinsertbefore"></a><a name="insertbefore"></a>CAtlList::InsertBefore

Llame a este método para insertar un nuevo elemento en la lista antes de la posición especificada.

```
POSITION InsertBefore(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El nuevo elemento se insertará en la lista antes de este valor POSITION.

*Elemento*<br/>
El elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor POSITION del nuevo elemento.

### <a name="remarks"></a>Observaciones

En compilaciones de depuración, se producirá un error de aserción si la lista no es válida, si se produce un error en la inserción o si se intenta insertar el elemento antes del cabezal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#24](../../atl/codesnippet/cpp/catllist-class_12.cpp)]

## <a name="catllistisempty"></a><a name="isempty"></a>CAtlList::IsEmpty

Llame a este método para determinar si la lista está vacía.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve true si la lista no contiene objetos, de lo contrario false.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#25](../../atl/codesnippet/cpp/catllist-class_13.cpp)]

## <a name="catllistmovetohead"></a><a name="movetohead"></a>CAtlList::MoveToHead

Llame a este método para mover el elemento especificado al jefe de la lista.

```cpp
void MoveToHead(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El valor POSITION del elemento que se va a mover.

### <a name="remarks"></a>Observaciones

El elemento especificado se mueve de su posición actual al jefe de la lista. En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#26](../../atl/codesnippet/cpp/catllist-class_14.cpp)]

## <a name="catllistmovetotail"></a><a name="movetotail"></a>CAtlList::MoveToTail

Llame a este método para mover el elemento especificado a la cola de la lista.

```cpp
void MoveToTail(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El valor POSITION del elemento que se va a mover.

### <a name="remarks"></a>Observaciones

El elemento especificado se mueve de su posición actual a la cola de la lista. En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::MoveToHead](#movetohead).

## <a name="catllistremoveall"></a><a name="removeall"></a>CAtlList::RemoveAll

Llame a este método para quitar todos los elementos de la lista.

```cpp
void RemoveAll() throw();
```

### <a name="remarks"></a>Observaciones

Este método quita todos los elementos de la lista y libera la memoria asignada. En las compilaciones de depuración, se generará un ATLASSERT si no se eliminan todos los elementos o si la estructura de lista se ha dañado.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::IsEmpty](#isempty).

## <a name="catllistremoveat"></a><a name="removeat"></a>CAtlList::RemoveAt

Llame a este método para quitar un solo elemento de la lista.

```cpp
void RemoveAt(POSITION pos) throw();
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El valor POSITION del elemento que se va a quitar.

### <a name="remarks"></a>Observaciones

Se elimina el elemento al que hace referencia *pos* y se libera memoria. Es aceptable utilizar `RemoveAt` para quitar la cabeza o la cola de la lista.

En compilaciones de depuración, se producirá un error de aserción si la lista no es válida o si quitar el elemento hace que la lista tiene acceso a la memoria que no forma parte de la estructura de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#27](../../atl/codesnippet/cpp/catllist-class_15.cpp)]

## <a name="catllistremovehead"></a><a name="removehead"></a>CAtlList::RemoveHead

Llame a este método para quitar el elemento en la cabecera de la lista.

```
E RemoveHead();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el elemento en la cabecera de la lista.

### <a name="remarks"></a>Observaciones

El elemento head se elimina de la lista y se libera memoria. Se devuelve una copia del elemento. En compilaciones de depuración, se producirá un error de aserción si la lista está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#28](../../atl/codesnippet/cpp/catllist-class_16.cpp)]

## <a name="catllistremoveheadnoreturn"></a><a name="removeheadnoreturn"></a>CAtlList::RemoveHeadNoReturn

Llame a este método para quitar el elemento en la cabecera de la lista sin devolver un valor.

```cpp
void RemoveHeadNoReturn() throw();
```

### <a name="remarks"></a>Observaciones

El elemento head se elimina de la lista y se libera memoria. En compilaciones de depuración, se producirá un error de aserción si la lista está vacía.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::IsEmpty](#isempty).

## <a name="catllistremovetail"></a><a name="removetail"></a>CAtlList::RemoveTail

Llame a este método para quitar el elemento en la cola de la lista.

```
E RemoveTail();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el elemento en la cola de la lista.

### <a name="remarks"></a>Observaciones

El elemento tail se elimina de la lista y se libera memoria. Se devuelve una copia del elemento. En compilaciones de depuración, se producirá un error de aserción si la lista está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#29](../../atl/codesnippet/cpp/catllist-class_17.cpp)]

## <a name="catllistremovetailnoreturn"></a><a name="removetailnoreturn"></a>CAtlList::RemoveTailNoReturn

Llame a este método para quitar el elemento en la cola de la lista sin devolver un valor.

```cpp
void RemoveTailNoReturn() throw();
```

### <a name="remarks"></a>Observaciones

El elemento tail se elimina de la lista y se libera memoria. En compilaciones de depuración, se producirá un error de aserción si la lista está vacía.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAtlList::IsEmpty](#isempty).

## <a name="catllistsetat"></a><a name="setat"></a>CAtlList::SetAt

Llame a este método para establecer el valor del elemento en una posición determinada de la lista.

```cpp
void SetAt(POSITION pos, INARGTYPE element);
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
El valor POSITION correspondiente al elemento que se va a cambiar.

*Elemento*<br/>
El nuevo valor del elemento.

### <a name="remarks"></a>Observaciones

Reemplaza el valor existente por *el elemento*. En compilaciones de depuración, se producirá un error de aserción si *pos* es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#30](../../atl/codesnippet/cpp/catllist-class_18.cpp)]

## <a name="catllistswapelements"></a><a name="swapelements"></a>CAtlList::SwapElements

Llame a este método para intercambiar elementos en la lista.

```cpp
void SwapElements(POSITION pos1, POSITION pos2) throw();
```

### <a name="parameters"></a>Parámetros

*pos1*<br/>
El primer valor POSITION.

*pos2*<br/>
El segundo valor POSITION.

### <a name="remarks"></a>Observaciones

Intercambia los elementos en las dos posiciones especificadas. En compilaciones de depuración, se producirá un error de aserción si cualquiera de los valores de posición es igual a NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#31](../../atl/codesnippet/cpp/catllist-class_19.cpp)]

## <a name="see-also"></a>Consulte también

[Clase CList](../../mfc/reference/clist-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
