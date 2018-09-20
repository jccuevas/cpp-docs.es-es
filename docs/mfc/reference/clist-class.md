---
title: CList (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7eedcd5a50db64b72fd654e46ad870c9428ea77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425293"
---
# <a name="clist-class"></a>CList (clase)

Admite listas ordenadas de objetos no únicos accesibles secuencialmente o por valor.

## <a name="syntax"></a>Sintaxis

```
template<class TYPE, class ARG_TYPE = const TYPE&>
class CList : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CList::CList](#clist)|Construye una lista ordenada vacía.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CList::AddHead](#addhead)|Agrega un elemento (o todos los elementos de otra lista) en el encabezado de la lista (hace un nuevo encabezado).|
|[CList::AddTail](#addtail)|Agrega un elemento (o todos los elementos de otra lista) al final de la lista (crea una nueva cola).|
|[CList::Find](#find)|Obtiene la posición de un elemento especificado por el valor de puntero.|
|[CList::FindIndex](#findindex)|Obtiene la posición de un elemento especificado por un índice de base cero.|
|[CList::GetAt](#getat)|Obtiene el elemento en una posición determinada.|
|[CList::GetCount](#getcount)|Devuelve el número de elementos de esta lista.|
|[CList::GetHead](#gethead)|Devuelve el elemento de encabezado de la lista (no puede estar vacía).|
|[CList::GetHeadPosition](#getheadposition)|Devuelve la posición del elemento principal de la lista.|
|[CList::](#getnext)|Obtiene el elemento siguiente para efectuar una iteración.|
|[CList::GetPrev](#getprev)|Obtiene el elemento anterior para efectuar una iteración.|
|[CList::GetSize](#getsize)|Devuelve el número de elementos de esta lista.|
|[CList::GetTail](#gettail)|Devuelve el elemento final de la lista (no puede estar vacía).|
|[CList::GetTailPosition](#gettailposition)|Devuelve la posición del elemento final de la lista.|
|[CList::InsertAfter](#insertafter)|Inserta un nuevo elemento después de una posición determinada.|
|[CList::InsertBefore](#insertbefore)|Inserta un nuevo elemento antes de una posición especificada.|
|[CList::IsEmpty](#isempty)|Comprueba si la condición de la lista vacía (no hay elementos).|
|[CList::RemoveAll](#removeall)|Quita todos los elementos de esta lista.|
|[CList::RemoveAt](#removeat)|Quita un elemento de esta lista, especificada por posición.|
|[CList::RemoveHead](#removehead)|Quita el elemento del encabezado de la lista.|
|[CList::RemoveTail](#removetail)|Quita el elemento de la cola de la lista.|
|[CList::SetAt](#setat)|Establece el elemento en una posición determinada.|

#### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Tipo de objeto almacenado en la lista.

*ARG_TYPE*<br/>
Tipo usado para hacer referencia a los objetos almacenados en la lista. Puede ser una referencia.

## <a name="remarks"></a>Comentarios

`CList` las listas se comportan como listas doblemente vinculadas.

Una variable de tipo de posición es una clave para la lista. Puede usar una variable de posición como un iterador para recorrer una lista secuencialmente y como un marcador para contener un solo lugar. Una posición no es igual que un índice, sin embargo.

Inserción de elementos es muy rápido en el encabezado de lista, en la cola y en una posición conocida. Una búsqueda secuencial es necesaria buscar un elemento por valor o por índice. Esta búsqueda puede ser lenta si la lista es larga.

Si necesita un volcado de elementos individuales en la lista, debe establecer la profundidad del contexto de volcado en 1 o mayor.

Algunas funciones de miembro de esta llamada de clase auxiliar global de funciones que deben personalizarse para usos de la mayoría de los `CList` clase. Consulte [aplicaciones auxiliares de clase de colección](../../mfc/reference/collection-class-helpers.md) en la sección "Macros y variables globales".

Para obtener más información sobre el uso de `CList`, consulte el artículo [colecciones](../../mfc/collections.md).

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#35](../../mfc/codesnippet/cpp/clist-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

##  <a name="addhead"></a>  CList::AddHead

Agrega un nuevo elemento o una lista de elementos al principio de esta lista.

```
POSITION AddHead(ARG_TYPE newElement);
void AddHead(CList* pNewList);
```

### <a name="parameters"></a>Parámetros

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elemento de lista (puede ser una referencia).

*newElement*<br/>
El nuevo elemento.

*pNewList*<br/>
Un puntero a otro `CList` lista. Los elementos de *pNewList* se agregará a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión, devuelve el valor de la posición del elemento recién insertado.

### <a name="remarks"></a>Comentarios

La lista puede estar vacía antes de la operación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#36](../../mfc/codesnippet/cpp/clist-class_2.cpp)]

##  <a name="addtail"></a>  CList::AddTail

Agrega un nuevo elemento o una lista de elementos al final de esta lista.

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
Un puntero a otro `CList` lista. Los elementos de *pNewList* se agregará a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión, devuelve el valor de la posición del elemento recién insertado.

### <a name="remarks"></a>Comentarios

La lista puede estar vacía antes de la operación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#37](../../mfc/codesnippet/cpp/clist-class_3.cpp)]

##  <a name="clist"></a>  CList::CList

Construye una lista ordenada vacía.

```
CList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
La granularidad de asignación de memoria para ampliar la lista.

### <a name="remarks"></a>Comentarios

A medida que crece la lista, se asigna memoria en unidades de *nBlockSize* entradas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#38](../../mfc/codesnippet/cpp/clist-class_4.cpp)]

##  <a name="find"></a>  CList::Find

Busca en la lista secuencialmente para buscar el primer elemento coincidente especificado *searchValue*.

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
La posición inicial de la búsqueda. Si se especifica ningún valor, la búsqueda comienza con el elemento de encabezado.

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para la iteración o recuperación de objetos de puntero; Es NULL si no se encuentra el objeto.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#39](../../mfc/codesnippet/cpp/clist-class_5.cpp)]

##  <a name="findindex"></a>  CList::FindIndex

Usa el valor de *nIndex* como un índice en la lista.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del elemento de lista que se encuentra.

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para la iteración o recuperación de objetos de puntero; NULL si *nIndex* es negativo o demasiado grande.

### <a name="remarks"></a>Comentarios

Iniciar un examen secuencial desde el principio de la lista, deteniendo en la *n*elemento th.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#40](../../mfc/codesnippet/cpp/clist-class_6.cpp)]

##  <a name="getat"></a>  CList::GetAt

Obtiene el elemento de lista en una posición determinada.

```
TYPE& GetAt(POSITION position);
const TYPE& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de objeto en la lista.

*Posición*<br/>
La posición del elemento que se obtiene en la lista.

### <a name="return-value"></a>Valor devuelto

Consulte la descripción del valor devuelto de `GetHead`.

### <a name="remarks"></a>Comentarios

`GetAt` Devuelve el elemento (o una referencia al elemento) asociada a una posición determinada. No es igual que un índice, y no puede funcionar en un valor de posición por su cuenta. Una variable de tipo de posición es una clave para la lista.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CList::GetHeadPosition](#getheadposition).

##  <a name="getcount"></a>  CList::GetCount

Obtiene el número de elementos de esta lista.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Valor entero que contiene el número de elementos.

### <a name="remarks"></a>Comentarios

Llamar a este método generará el mismo resultado que la [CList::GetSize](#getsize) método.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CList::RemoveHead](#removehead).

##  <a name="gethead"></a>  CList::GetHead

Obtiene el elemento de encabezado (o una referencia al elemento de encabezado) de esta lista.

```
const TYPE& GetHead() const;

TYPE& GetHead();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de objeto en la lista.

### <a name="return-value"></a>Valor devuelto

Si la lista es **const**, `GetHead` devuelve una copia del elemento al principio de la lista. Esto permite la función que se usará solo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.

Si la lista no es **const**, `GetHead` devuelve una referencia al elemento al principio de la lista. Esto permite la función que se usará en ambos lados de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.

### <a name="remarks"></a>Comentarios

Debe asegurarse de que la lista no está vacía antes de llamar a `GetHead`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](#isempty) para comprobar que la lista contiene los elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#41](../../mfc/codesnippet/cpp/clist-class_7.cpp)]

##  <a name="getheadposition"></a>  CList::GetHeadPosition

Obtiene la posición del elemento principal de esta lista.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para la iteración o recuperación de objetos de puntero; Es NULL si la lista está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#42](../../mfc/codesnippet/cpp/clist-class_8.cpp)]

##  <a name="getnext"></a>  CList::

Obtiene el elemento de lista identificado por *rPosition*, a continuación, establece *rPosition* en el valor de posición de la siguiente entrada en la lista.

```
TYPE& GetNext(POSITION& rPosition);
const TYPE& GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de los elementos de la lista.

*rPosition*<br/>
Una referencia a un valor de posición devuelto por un método `GetNext`, [GetHeadPosition](#getheadposition), u otra llamada de función miembro.

### <a name="return-value"></a>Valor devuelto

Si la lista es **const**, `GetNext` devuelve una copia de un elemento de la lista. Esto permite la función que se usará solo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.

Si la lista no es **const**, `GetNext` devuelve una referencia a un elemento de la lista. Esto permite la función que se usará en ambos lados de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.

### <a name="remarks"></a>Comentarios

Puede usar `GetNext` en un bucle de iteración de avance, si establece la posición inicial con una llamada a `GetHeadPosition` o `Find`.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

Si el elemento recuperado es el último en la lista, a continuación, el nuevo valor de `rPosition` se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#43](../../mfc/codesnippet/cpp/clist-class_9.cpp)]

##  <a name="getprev"></a>  CList::GetPrev

Obtiene el elemento de lista identificado por `rPosition`, a continuación, establece `rPosition` en el valor de posición de la entrada en la lista anterior.

```
TYPE& GetPrev(POSITION& rPosition);
const TYPE& GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de los elementos de la lista.

*rPosition*<br/>
Una referencia a un valor de posición devuelto por un método `GetPrev` u otra llamada de función miembro.

### <a name="return-value"></a>Valor devuelto

Si la lista es **const**, `GetPrev` devuelve una copia del elemento al principio de la lista. Esto permite la función que se usará solo en el lado derecho de una instrucción de asignación y protege la lista de la modificación.

Si la lista no es **const**, `GetPrev` devuelve una referencia a un elemento de la lista. Esto permite la función que se usará en ambos lados de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.

### <a name="remarks"></a>Comentarios

Puede usar `GetPrev` en un bucle de iteración inversa, si establece la posición inicial con una llamada a `GetTailPosition` o `Find`.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

Si el elemento recuperado es el primero en la lista, a continuación, el nuevo valor de *rPosition* se establece en NULL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#44](../../mfc/codesnippet/cpp/clist-class_10.cpp)]

##  <a name="getsize"></a>  CList::GetSize

Devuelve el número de elementos de la lista.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la lista.

### <a name="remarks"></a>Comentarios

Llame a este método para recuperar el número de elementos de la lista.  Llamar a este método generará el mismo resultado que la [CList::GetCount](#getcount) método.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#45](../../mfc/codesnippet/cpp/clist-class_11.cpp)]

##  <a name="gettail"></a>  CList::GetTail

Obtiene el `CObject` puntero que representa el elemento final de esta lista.

```
TYPE& GetTail();
const TYPE& GetTail() const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos de la lista.

### <a name="return-value"></a>Valor devuelto

Consulte la descripción del valor devuelto de [GetHead](../../mfc/reference/coblist-class.md#gethead).

### <a name="remarks"></a>Comentarios

Debe asegurarse de que la lista no está vacía antes de llamar a `GetTail`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene los elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#46](../../mfc/codesnippet/cpp/clist-class_12.cpp)]

##  <a name="gettailposition"></a>  CList::GetTailPosition

Obtiene la posición del elemento final de esta lista. Es NULL si la lista está vacía.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para la iteración o recuperación de objetos de puntero; Es NULL si la lista está vacía.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#47](../../mfc/codesnippet/cpp/clist-class_13.cpp)]

##  <a name="insertafter"></a>  CList::InsertAfter

Agrega un elemento a esta lista después del elemento en la posición especificada.

```
POSITION InsertAfter(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
Un valor de posición devuelto por un método `GetNext`, `GetPrev`, o `Find` llamada a función miembro.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo del elemento de lista.

*newElement*<br/>
Elemento que se va a agregar a esta lista.

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para la recuperación de elementos de lista o iteración.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#48](../../mfc/codesnippet/cpp/clist-class_14.cpp)]

##  <a name="insertbefore"></a>  CList::InsertBefore

Agrega un elemento a esta lista delante del elemento en la posición especificada.

```
POSITION InsertBefore(POSITION position, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
Un valor de posición devuelto por un método `GetNext`, `GetPrev`, o `Find` llamada a función miembro.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elemento de lista (puede ser una referencia).

*newElement*<br/>
Elemento que se va a agregar a esta lista.

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para la recuperación de elementos de lista o iteración.

### <a name="remarks"></a>Comentarios

Si *posición* es NULL, el elemento se inserta al principio de la lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#49](../../mfc/codesnippet/cpp/clist-class_15.cpp)]

##  <a name="isempty"></a>  CList::IsEmpty

Indica si esta lista no contiene ningún elemento.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si esta lista está vacía. en caso contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#50](../../mfc/codesnippet/cpp/clist-class_16.cpp)]

##  <a name="removeall"></a>  CList::RemoveAll

Quita todos los elementos de esta lista y libera la memoria asociada.

```
void RemoveAll();
```

### <a name="remarks"></a>Comentarios

Si la lista está vacía, se genera ningún error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#51](../../mfc/codesnippet/cpp/clist-class_17.cpp)]

##  <a name="removeat"></a>  CList::RemoveAt

Quita el elemento especificado de esta lista.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
La posición del elemento que se va a quitar de la lista.

### <a name="remarks"></a>Comentarios

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#52](../../mfc/codesnippet/cpp/clist-class_18.cpp)]

##  <a name="removehead"></a>  CList::RemoveHead

Quita el elemento del encabezado de la lista y devuelve un puntero a él.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos de la lista.

### <a name="return-value"></a>Valor devuelto

El elemento previamente al principio de la lista.

### <a name="remarks"></a>Comentarios

Debe asegurarse de que la lista no está vacía antes de llamar a `RemoveHead`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](#isempty) para comprobar que la lista contiene los elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#53](../../mfc/codesnippet/cpp/clist-class_19.cpp)]

##  <a name="removetail"></a>  CList::RemoveTail

Quita el elemento de la cola de la lista y devuelve un puntero a él.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos de la lista.

### <a name="return-value"></a>Valor devuelto

El elemento que estaba en la cola de la lista.

### <a name="remarks"></a>Comentarios

Debe asegurarse de que la lista no está vacía antes de llamar a `RemoveTail`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](#isempty) para comprobar que la lista contiene los elementos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#54](../../mfc/codesnippet/cpp/clist-class_20.cpp)]

##  <a name="setat"></a>  CList::SetAt

Una variable de tipo de posición es una clave para la lista.

```
void SetAt(POSITION pos, ARG_TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
La posición del elemento que se puede establecer.

*ARG_TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elemento de lista (puede ser una referencia).

*newElement*<br/>
El elemento que se agrega a la lista.

### <a name="remarks"></a>Comentarios

No es igual que un índice, y no puede funcionar en un valor de posición por su cuenta. `SetAt` Escribe el elemento en la posición especificada en la lista.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#55](../../mfc/codesnippet/cpp/clist-class_21.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMap (clase)](../../mfc/reference/cmap-class.md)<br/>
[CArray (clase)](../../mfc/reference/carray-class.md)
