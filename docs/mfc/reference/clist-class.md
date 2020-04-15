---
title: Clase CList
ms.date: 11/04/2016
f1_keywords:
- CList
- AFXTEMPL/CList
- AFXTEMPL/CList::CList
- AFXTEMPL/CList::AddHead
- AFXTEMPL/CList::AddTail
- AFXTEMPL/CList::Find
- AFXTEMPL/CList::FindIndex
- AFXTEMPL/CList::GetAt
- AFXTEMPL/CList::GetCount
- AFXTEMPL/CList::GetHead
- AFXTEMPL/CList::GetHeadPosition
- AFXTEMPL/CList::GetNext
- AFXTEMPL/CList::GetPrev
- AFXTEMPL/CList::GetSize
- AFXTEMPL/CList::GetTail
- AFXTEMPL/CList::GetTailPosition
- AFXTEMPL/CList::InsertAfter
- AFXTEMPL/CList::InsertBefore
- AFXTEMPL/CList::IsEmpty
- AFXTEMPL/CList::RemoveAll
- AFXTEMPL/CList::RemoveAt
- AFXTEMPL/CList::RemoveHead
- AFXTEMPL/CList::RemoveTail
- AFXTEMPL/CList::SetAt
helpviewer_keywords:
- CList [MFC], CList
- CList [MFC], AddHead
- CList [MFC], AddTail
- CList [MFC], Find
- CList [MFC], FindIndex
- CList [MFC], GetAt
- CList [MFC], GetCount
- CList [MFC], GetHead
- CList [MFC], GetHeadPosition
- CList [MFC], GetNext
- CList [MFC], GetPrev
- CList [MFC], GetSize
- CList [MFC], GetTail
- CList [MFC], GetTailPosition
- CList [MFC], InsertAfter
- CList [MFC], InsertBefore
- CList [MFC], IsEmpty
- CList [MFC], RemoveAll
- CList [MFC], RemoveAt
- CList [MFC], RemoveHead
- CList [MFC], RemoveTail
- CList [MFC], SetAt
ms.assetid: 6f6273c3-c8f6-47f5-ac2a-0a950379ae5d
ms.openlocfilehash: 253cf12033af497115ad600e457630ae834cc69c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372244"
---
# <a name="clist-class"></a>Clase CList

Admite listas ordenadas de objetos no únicos accesibles secuencialmente o por valor.

## <a name="syntax"></a>Sintaxis

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CList::CList](#clist)|Construye una lista ordenada vacía.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CList::AddHead](#addhead)|Agrega un elemento (o todos los elementos de otra lista) al jefe de la lista (hace una nueva cabeza).|
|[CList::AddTail](#addtail)|Agrega un elemento (o todos los elementos de otra lista) a la cola de la lista (hace una nueva cola).|
|[CList::Buscar](#find)|Obtiene la posición de un elemento especificado por el valor del puntero.|
|[CList::FindIndex](#findindex)|Obtiene la posición de un elemento especificado por un índice de base cero.|
|[CList::GetAt](#getat)|Obtiene el elemento en una posición determinada.|
|[CList::GetCount](#getcount)|Devuelve el número de elementos de esta lista.|
|[CList::GetHead](#gethead)|Devuelve el elemento head de la lista (no puede estar vacío).|
|[CList::GetHeadPosition](#getheadposition)|Devuelve la posición del elemento head de la lista.|
|[CList::GetNext](#getnext)|Obtiene el siguiente elemento para iterar.|
|[CList::GetPrev](#getprev)|Obtiene el elemento anterior para iterar.|
|[CList::GetSize](#getsize)|Devuelve el número de elementos de esta lista.|
|[CList::GetTail](#gettail)|Devuelve el elemento tail de la lista (no puede estar vacío).|
|[CList::GetTailPosition](#gettailposition)|Devuelve la posición del elemento de cola de la lista.|
|[CList::InsertAfter](#insertafter)|Inserta un nuevo elemento después de una posición determinada.|
|[CList::InsertBefore](#insertbefore)|Inserta un nuevo elemento antes de una posición determinada.|
|[CList::IsEmpty](#isempty)|Comprueba la condición de lista vacía (sin elementos).|
|[CList::RemoveAll](#removeall)|Elimina todos los elementos de esta lista.|
|[CList::RemoveAt](#removeat)|Quita un elemento de esta lista, especificado por position.|
|[CList::RemoveHead](#removehead)|Quita el elemento del jefe de la lista.|
|[CList::RemoveTail](#removetail)|Quita el elemento de la cola de la lista.|
|[CList::SetAt](#setat)|Establece el elemento en una posición determinada.|

#### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Tipo de objeto almacenado en la lista.

*ARG_TYPE*<br/>
Tipo utilizado para hacer referencia a objetos almacenados en la lista. Puede ser una referencia.

## <a name="remarks"></a>Observaciones

`CList`las listas se comportan como listas doblemente vinculadas.

Una variable de tipo POSITION es una clave para la lista. Puede utilizar una variable POSITION como iterador para recorrer una lista secuencialmente y como marcador para mantener un lugar. Sin embargo, una posición no es lo mismo que un índice.

La inserción de elementos es muy rápida en el cabezal de lista, en la cola y en una POSICIÓN conocida. Una búsqueda secuencial es necesaria para buscar un elemento por valor o índice. Esta búsqueda puede ser lenta si la lista es larga.

Si necesita un volcado de elementos individuales en la lista, debe establecer la profundidad del contexto de volcado en 1 o superior.

Ciertas funciones miembro de esta clase llaman a funciones auxiliares globales que se deben personalizar para la mayoría de los usos de la `CList` clase. Consulte [Ayudantes de clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección "Macros y globales".

Para obtener más `CList`información sobre el uso , vea el artículo [Colecciones](../../mfc/collections.md).

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

## <a name="clistaddhead"></a><a name="addhead"></a>CList::AddHead

Agrega un nuevo elemento o lista de elementos al jefe de esta lista.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Parámetros

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elemento de lista (puede ser una referencia).

*newElement*<br/>
Nuevo elemento.

*pNewList*<br/>
Un puntero `CList` a otra lista. Los elementos de *pNewList* se agregarán a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve el valor POSITION del elemento recién insertado.

### <a name="remarks"></a>Observaciones

La lista puede estar vacía antes de la operación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

## <a name="clistaddtail"></a><a name="addtail"></a>CList::AddTail

Agrega un nuevo elemento o lista de elementos a la cola de esta lista.

```
POSITION AddTail(ARG_TYPE newElement);
void AddTail(CList* pNewList);
```

### <a name="parameters"></a>Parámetros

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elemento de lista (puede ser una referencia).

*newElement*<br/>
Elemento que se va a agregar a esta lista.

*pNewList*<br/>
Un puntero `CList` a otra lista. Los elementos de *pNewList* se agregarán a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve el valor POSITION del elemento recién insertado.

### <a name="remarks"></a>Observaciones

La lista puede estar vacía antes de la operación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

## <a name="clistclist"></a><a name="clist"></a>CList::CList

Construye una lista ordenada vacía.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
La granularidad de asignación de memoria para ampliar la lista.

### <a name="remarks"></a>Observaciones

A medida que crece la lista, la memoria se asigna en unidades de entradas *nBlockSize.*

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

## <a name="clistfind"></a><a name="find"></a>CList::Buscar

Busca la lista secuencialmente para buscar el primer elemento que coincida con el *valor de búsqueda*especificado.

```
POSITION Find(
    ARG_TYPE searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parámetros

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elemento de lista (puede ser una referencia).

*searchValue*<br/>
El valor que se encuentra en la lista.

*startAfter*<br/>
La posición inicial de la búsqueda. Si no se especifica ningún valor, la búsqueda comienza con el elemento head.

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si no se encuentra el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

## <a name="clistfindindex"></a><a name="findindex"></a>CList::FindIndex

Utiliza el valor de *nIndex* como índice en la lista.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del elemento de lista que se va a encontrar.

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si *nIndex* es negativo o demasiado grande.

### <a name="remarks"></a>Observaciones

Inicia un análisis secuencial desde el jefe de la lista, deteniéndose en el *nésimo*elemento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

## <a name="clistgetat"></a><a name="getat"></a>CList::GetAt

Obtiene el elemento de lista en una posición determinada.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de objeto de la lista.

*Posición*<br/>
La posición en la lista del elemento que se va a obtener.

### <a name="return-value"></a>Valor devuelto

Consulte la descripción `GetHead`del valor devuelto para .

### <a name="remarks"></a>Observaciones

`GetAt`devuelve el elemento (o una referencia al elemento) asociado a una posición determinada. No es lo mismo que un índice y no puede operar en un valor POSITION usted mismo. Una variable de tipo POSITION es una clave para la lista.

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CList::GetHeadPosition](#getheadposition).

## <a name="clistgetcount"></a><a name="getcount"></a>CList::GetCount

Obtiene el número de elementos de esta lista.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Valor entero que contiene el recuento de elementos.

### <a name="remarks"></a>Observaciones

Llamar a este método generará el mismo resultado que el [CList::GetSize](#getsize) método.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CList::RemoveHead](#removehead).

## <a name="clistgethead"></a><a name="gethead"></a>CList::GetHead

Obtiene el elemento head (o una referencia al elemento head) de esta lista.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de objeto de la lista.

### <a name="return-value"></a>Valor devuelto

Si la lista es `GetHead` **const**, devuelve una copia del elemento en la cabecera de la lista. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y protege la lista de modificaciones.

Si la lista no es `GetHead` **const**, devuelve una referencia al elemento en la cabecera de la lista. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `GetHead`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

## <a name="clistgetheadposition"></a><a name="getheadposition"></a>CList::GetHeadPosition

Obtiene la posición del elemento head de esta lista.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si la lista está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

## <a name="clistgetnext"></a><a name="getnext"></a>CList::GetNext

Obtiene el elemento de lista identificado por *rPosition*y, a continuación, establece *rPosition* en el valor POSITION de la siguiente entrada de la lista.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de los elementos de la lista.

*rPosición*<br/>
Una referencia a un valor `GetNext`POSITION devuelto por una llamada anterior, [GetHeadPosition](#getheadposition)u otra función miembro.

### <a name="return-value"></a>Valor devuelto

Si la lista es `GetNext` **const**, devuelve una copia de un elemento de la lista. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y protege la lista de modificaciones.

Si la lista no es `GetNext` **const**, devuelve una referencia a un elemento de la lista. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

Puede utilizar `GetNext` en un bucle de iteración directa `GetHeadPosition` si `Find`establece la posición inicial con una llamada a o .

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Si el elemento recuperado es el último de la `rPosition` lista, el nuevo valor de se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

## <a name="clistgetprev"></a><a name="getprev"></a>CList::GetPrev

Obtiene el elemento de `rPosition`lista `rPosition` identificado por , a continuación, establece en el valor POSITION de la entrada anterior de la lista.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de los elementos de la lista.

*rPosición*<br/>
Una referencia a un valor `GetPrev` POSITION devuelto por una llamada a una función miembro anterior u otra.

### <a name="return-value"></a>Valor devuelto

Si la lista es `GetPrev` **const**, devuelve una copia del elemento en la cabecera de la lista. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y protege la lista de modificaciones.

Si la lista no es `GetPrev` **const**, devuelve una referencia a un elemento de la lista. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

Puede utilizar `GetPrev` en un bucle de iteración inversa `GetTailPosition` `Find`si establece la posición inicial con una llamada a o .

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Si el elemento recuperado es el primero de la lista, el nuevo valor de *rPosition* se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

## <a name="clistgetsize"></a><a name="getsize"></a>CList::GetSize

Devuelve el número de elementos de lista.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos de la lista.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de elementos de la lista.  Llamar a este método generará el mismo resultado que el [CList::GetCount](#getcount) método.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

## <a name="clistgettail"></a><a name="gettail"></a>CList::GetTail

Obtiene el `CObject` puntero que representa el elemento de cola de esta lista.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos de la lista.

### <a name="return-value"></a>Valor devuelto

Consulte la descripción del valor devuelto para [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `GetTail`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

## <a name="clistgettailposition"></a><a name="gettailposition"></a>CList::GetTailPosition

Obtiene la posición del elemento de cola de esta lista; NULL si la lista está vacía.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si la lista está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

## <a name="clistinsertafter"></a><a name="insertafter"></a>CList::InsertAfter

Agrega un elemento a esta lista después del elemento en la posición especificada.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
Un valor POSITION devuelto `GetNext` `GetPrev`por `Find` una llamada a una función anterior , , o miembro.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo del elemento de lista.

*newElement*<br/>
Elemento que se va a agregar a esta lista.

### <a name="return-value"></a>Valor devuelto

Valor POSITION que puede usarse para la recuperación de elementos de lista o iteración.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

## <a name="clistinsertbefore"></a><a name="insertbefore"></a>CList::InsertBefore

Agrega un elemento a esta lista delante del elemento en la posición especificada.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
Un valor POSITION devuelto `GetNext` `GetPrev`por `Find` una llamada a una función anterior , , o miembro.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elemento de lista (puede ser una referencia).

*newElement*<br/>
Elemento que se va a agregar a esta lista.

### <a name="return-value"></a>Valor devuelto

Valor POSITION que puede usarse para la recuperación de elementos de lista o iteración.

### <a name="remarks"></a>Observaciones

Si *position* es NULL, el elemento se inserta en la cabecera de la lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

## <a name="clistisempty"></a><a name="isempty"></a>CList::IsEmpty

Indica si esta lista no contiene elementos.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si esta lista está vacía; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

## <a name="clistremoveall"></a><a name="removeall"></a>CList::RemoveAll

Elimina todos los elementos de esta lista y libera la memoria asociada.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

No se genera ningún error si la lista ya está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

## <a name="clistremoveat"></a><a name="removeat"></a>CList::RemoveAt

Quita el elemento especificado de esta lista.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
La posición del elemento que se va a eliminar de la lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

## <a name="clistremovehead"></a><a name="removehead"></a>CList::RemoveHead

Quita el elemento del jefe de la lista y devuelve un puntero a él.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos de la lista.

### <a name="return-value"></a>Valor devuelto

El elemento anteriormente en la cabecera de la lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `RemoveHead`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

## <a name="clistremovetail"></a><a name="removetail"></a>CList::RemoveTail

Quita el elemento de la cola de la lista y devuelve un puntero a él.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos de la lista.

### <a name="return-value"></a>Valor devuelto

El elemento que estaba en la cola de la lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `RemoveTail`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

## <a name="clistsetat"></a><a name="setat"></a>CList::SetAt

Una variable de tipo POSITION es una clave para la lista.

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
POSITION del elemento que se va a establecer.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elemento de lista (puede ser una referencia).

*newElement*<br/>
El elemento que se agregará a la lista.

### <a name="remarks"></a>Observaciones

No es lo mismo que un índice y no puede operar en un valor POSITION usted mismo. `SetAt`escribe el elemento en la posición especificada en la lista.

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Consulte también

[RECOPILACIÓN de muestras de MFC](../../overview/visual-cpp-samples.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CMap](../../mfc/reference/cmap-class.md)<br/>
[CArray (clase)](../../mfc/reference/carray-class.md)
