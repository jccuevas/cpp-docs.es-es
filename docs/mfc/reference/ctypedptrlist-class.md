---
title: Clase CTypedPtrList
ms.date: 11/04/2016
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
helpviewer_keywords:
- CTypedPtrList [MFC], AddHead
- CTypedPtrList [MFC], AddTail
- CTypedPtrList [MFC], GetAt
- CTypedPtrList [MFC], GetHead
- CTypedPtrList [MFC], GetNext
- CTypedPtrList [MFC], GetPrev
- CTypedPtrList [MFC], GetTail
- CTypedPtrList [MFC], RemoveHead
- CTypedPtrList [MFC], RemoveTail
- CTypedPtrList [MFC], SetAt
ms.assetid: c273096e-1756-4340-864b-4a08b674a65e
ms.openlocfilehash: 485550fbd4d3fc483303cd6ba73d74e29cc7a006
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555889"
---
# <a name="ctypedptrlist-class"></a>Clase CTypedPtrList

Proporciona un "contenedor" de tipo seguro para objetos de clase `CPtrList`.

## <a name="syntax"></a>Sintaxis

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>Parámetros

*$BASE_CLASS*<br/>
Clase base de la clase de lista de puntero con tipo. debe ser una clase de lista de puntero ( `CObList` o `CPtrList`).

*TIPO*<br/>
Tipo de los elementos almacenados en la lista de clase base.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|Agrega un elemento (o todos los elementos de otra lista) en el encabezado de la lista (hace un nuevo encabezado).|
|[CTypedPtrList::AddTail](#addtail)|Agrega un elemento (o todos los elementos de otra lista) al final de la lista (crea una nueva cola).|
|[CTypedPtrList::GetAt](#getat)|Obtiene el elemento en una posición determinada.|
|[CTypedPtrList::GetHead](#gethead)|Devuelve el elemento de encabezado de la lista (no puede estar vacía).|
|[CTypedPtrList::GetNext](#getnext)|Obtiene el elemento siguiente para efectuar una iteración.|
|[CTypedPtrList::GetPrev](#getprev)|Obtiene el elemento anterior para efectuar una iteración.|
|[CTypedPtrList::GetTail](#gettail)|Devuelve el elemento final de la lista (no puede estar vacía).|
|[CTypedPtrList::RemoveHead](#removehead)|Quita el elemento del encabezado de la lista.|
|[CTypedPtrList::RemoveTail](#removetail)|Quita el elemento de la cola de la lista.|
|[CTypedPtrList::SetAt](#setat)|Establece el elemento en una posición determinada.|

## <a name="remarks"></a>Comentarios

Cuando usas `CTypedPtrList` lugar `CObList` o `CPtrList`, la utilidad de comprobación de tipos de C++ ayuda a eliminar errores causados por los tipos de puntero que no coinciden.

Además, el `CTypedPtrList` contenedor realiza gran parte de la conversión que sería necesaria si ha usado `CObList` o `CPtrList`.

Dado que todos los `CTypedPtrList` funciones están alineados, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.

Las listas se derivan `CObList` se puede serializar, pero los derivados de `CPtrList` no.

Cuando se elimina un objeto `CTypedPtrList`, o cuando se quitan sus elementos, solo se quitan los punteros, no las entidades a las que hacen referencia.

Para obtener más información sobre el uso de `CTypedPtrList`, consulte los artículos [colecciones](../../mfc/collections.md) y [clases basadas en plantillas](../../mfc/template-based-classes.md).

## <a name="example"></a>Ejemplo

Este ejemplo crea una instancia de `CTypedPtrList`, agrega un objeto, serializa la lista en el disco y, a continuación, elimina el objeto:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

##  <a name="addhead"></a>  CTypedPtrList::AddHead

Esta función miembro llama a `BASE_CLASS` **:: AddHead**.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Tipo de los elementos almacenados en la lista de clase base.

*newElement*<br/>
El puntero de objeto para agregarse a esta lista. Se permite un valor NULL.

*$BASE_CLASS*<br/>
Clase base de la clase de lista de puntero con tipo. debe ser una clase de lista de puntero ( [CObList](../../mfc/reference/coblist-class.md) o [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Un puntero a otro [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objeto. Los elementos de *pNewList* se agregará a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión, devuelve el valor de la posición del elemento recién insertado.

### <a name="remarks"></a>Comentarios

La primera versión agrega un nuevo elemento antes de la cabeza de la lista. La segunda versión agrega otra lista de elementos antes de la cabeza.

##  <a name="addtail"></a>  CTypedPtrList::AddTail

Esta función miembro llama a `BASE_CLASS` **:: AddTail**.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Tipo de los elementos almacenados en la lista de clase base.

*newElement*<br/>
El puntero de objeto para agregarse a esta lista. Se permite un valor NULL.

*$BASE_CLASS*<br/>
Clase base de la clase de lista de puntero con tipo. debe ser una clase de lista de puntero ( [CObList](../../mfc/reference/coblist-class.md) o [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Un puntero a otro [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objeto. Los elementos de *pNewList* se agregará a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión, devuelve el valor de la posición del elemento recién insertado.

### <a name="remarks"></a>Comentarios

La primera versión agrega un nuevo elemento después del final de la lista. La segunda versión agrega otra lista de elementos después del final de la lista.

##  <a name="getat"></a>  CTypedPtrList::GetAt

Una variable de tipo de posición es una clave para la lista.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

*Posición*<br/>
Un valor de posición devuelto por un método `GetHeadPosition` o `Find` llamada a función miembro.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a la lista mediante un puntero a un `const CTypedPtrList`, a continuación, `GetAt` devuelve un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará solo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.

Si se tiene acceso a la lista directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetAt` devuelve una referencia a un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará en ambos lados de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.

### <a name="remarks"></a>Comentarios

No es igual que un índice, y no puede funcionar en un valor de posición por su cuenta. `GetAt` Recupera el `CObject` puntero asociado a una posición determinada.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

Llama esta función inline `BASE_CLASS` **:: GetAt**.

##  <a name="gethead"></a>  CTypedPtrList::GetHead

Obtiene el puntero que representa el elemento principal de esta lista.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a la lista mediante un puntero a un `const CTypedPtrList`, a continuación, `GetHead` devuelve un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará solo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.

Si se tiene acceso a la lista directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetHead` devuelve una referencia a un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará en ambos lados de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.

### <a name="remarks"></a>Comentarios

Debe asegurarse de que la lista no está vacía antes de llamar a `GetHead`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene los elementos.

##  <a name="getnext"></a>  CTypedPtrList::GetNext

Obtiene el elemento de lista identificado por *rPosition*, a continuación, establece *rPosition* en el valor de posición de la siguiente entrada en la lista.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos contenidos en esta lista.

*rPosition*<br/>
Una referencia a un valor de posición devuelto por un método `GetNext`, `GetHeadPosition`, u otra llamada de función miembro.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a la lista mediante un puntero a un `const CTypedPtrList`, a continuación, `GetNext` devuelve un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará solo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.

Si se tiene acceso a la lista directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetNext` devuelve una referencia a un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará en ambos lados de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.

### <a name="remarks"></a>Comentarios

Puede usar `GetNext` en un bucle de iteración de avance, si establece la posición inicial con una llamada a `GetHeadPosition` o [CPtrList::Find](../../mfc/reference/coblist-class.md#find).

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

Si el elemento recuperado es el último en la lista, a continuación, el nuevo valor de *rPosition* se establece en NULL.

Es posible quitar un elemento durante una iteración. Vea el ejemplo de [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).

##  <a name="getprev"></a>  CTypedPtrList::GetPrev

Obtiene el elemento de lista identificado por *rPosition*, a continuación, establece *rPosition* en el valor de posición de la entrada en la lista anterior.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos contenidos en esta lista.

*rPosition*<br/>
Una referencia a un valor de posición devuelto por un método `GetPrev` u otra llamada de función miembro.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a la lista mediante un puntero a un `const CTypedPtrList`, a continuación, `GetPrev` devuelve un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará solo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.

Si se tiene acceso a la lista directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetPrev` devuelve una referencia a un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará en ambos lados de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.

### <a name="remarks"></a>Comentarios

Puede usar `GetPrev` en un bucle de iteración inversa, si establece la posición inicial con una llamada a `GetTailPosition` o `Find`.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

Si el elemento recuperado es el primero en la lista, a continuación, el nuevo valor de *rPosition* se establece en NULL.

##  <a name="gettail"></a>  CTypedPtrList::GetTail

Obtiene el puntero que representa el elemento principal de esta lista.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a la lista mediante un puntero a un `const CTypedPtrList`, a continuación, `GetTail` devuelve un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará solo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.

Si se tiene acceso a la lista directamente o a través de un puntero a un `CTypedPtrList`, a continuación, `GetTail` devuelve una referencia a un puntero de tipo especificado por el parámetro de plantilla *tipo*. Esto permite la función que se usará en ambos lados de una instrucción de asignación y, por tanto, permite modificar las entradas de la lista.

### <a name="remarks"></a>Comentarios

Debe asegurarse de que la lista no está vacía antes de llamar a `GetTail`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene los elementos.

##  <a name="removehead"></a>  CTypedPtrList::RemoveHead

Quita el elemento del encabezado de la lista y lo devuelve.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

### <a name="return-value"></a>Valor devuelto

El puntero previamente al principio de la lista. Este puntero es de tipo especificado por el parámetro de plantilla *tipo*.

### <a name="remarks"></a>Comentarios

Debe asegurarse de que la lista no está vacía antes de llamar a `RemoveHead`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene los elementos.

##  <a name="removetail"></a>  CTypedPtrList::RemoveTail

Quita el elemento de la cola de la lista y lo devuelve.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

### <a name="return-value"></a>Valor devuelto

El puntero previamente en la cola de la lista. Este puntero es de tipo especificado por el parámetro de plantilla *tipo*.

### <a name="remarks"></a>Comentarios

Debe asegurarse de que la lista no está vacía antes de llamar a `RemoveTail`. Si la lista está vacía, se valida la versión de depuración de la biblioteca Microsoft Foundation Class. Use [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene los elementos.

##  <a name="setat"></a>  CTypedPtrList::SetAt

Esta función miembro llama a `BASE_CLASS` **:: SetAt**.

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*punto de venta*<br/>
La posición del elemento que se puede establecer.

*TIPO*<br/>
Tipo de los elementos almacenados en la lista de clase base.

*newElement*<br/>
Puntero de objeto que se va a escribir en la lista.

### <a name="remarks"></a>Comentarios

Una variable de tipo de posición es una clave para la lista. No es igual que un índice, y no puede funcionar en un valor de posición por su cuenta. `SetAt` Escribe el puntero de objeto a la posición especificada en la lista.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

Para obtener comentarios más detallada, consulte [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPtrList (clase)](../../mfc/reference/cptrlist-class.md)<br/>
[CObList (clase)](../../mfc/reference/coblist-class.md)
