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
ms.openlocfilehash: 40dbfb822e71309e9675aba14d46d333ffa4ee06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373261"
---
# <a name="ctypedptrlist-class"></a>Clase CTypedPtrList

Proporciona un "contenedor" de tipo seguro para objetos de clase `CPtrList`.

## <a name="syntax"></a>Sintaxis

```
template<class BASE_CLASS, class TYPE>
class CTypedPtrList : public BASE_CLASS
```

#### <a name="parameters"></a>Parámetros

*BASE_CLASS*<br/>
Clase base de la clase de lista de punteros con tipo; debe ser una clase `CObList` `CPtrList`de lista de punteros ( o ).

*TIPO*<br/>
Tipo de los elementos almacenados en la lista de clase base.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTypedPtrList::AddHead](#addhead)|Agrega un elemento (o todos los elementos de otra lista) al jefe de la lista (hace una nueva cabeza).|
|[CTypedPtrList::AddTail](#addtail)|Agrega un elemento (o todos los elementos de otra lista) a la cola de la lista (hace una nueva cola).|
|[CTypedPtrList::GetAt](#getat)|Obtiene el elemento en una posición determinada.|
|[CTypedPtrList::GetHead](#gethead)|Devuelve el elemento head de la lista (no puede estar vacío).|
|[CTypedPtrList::GetNext](#getnext)|Obtiene el siguiente elemento para iterar.|
|[CTypedPtrList::GetPrev](#getprev)|Obtiene el elemento anterior para iterar.|
|[CTypedPtrList::GetTail](#gettail)|Devuelve el elemento tail de la lista (no puede estar vacío).|
|[CTypedPtrList::RemoveHead](#removehead)|Quita el elemento del jefe de la lista.|
|[CTypedPtrList::RemoveTail](#removetail)|Quita el elemento de la cola de la lista.|
|[CTypedPtrList::SetAt](#setat)|Establece el elemento en una posición determinada.|

## <a name="remarks"></a>Observaciones

Cuando se `CTypedPtrList` utiliza `CObList` `CPtrList`en lugar de o , la función de comprobación de tipos C++ ayuda a eliminar los errores causados por tipos de puntero no coincidentes.

Además, `CTypedPtrList` el contenedor realiza gran parte de la `CObList` `CPtrList`fundición que sería necesaria si se utiliza o .

Dado `CTypedPtrList` que todas las funciones están en línea, el uso de esta plantilla no afecta significativamente al tamaño o la velocidad del código.

Las listas `CObList` derivadas de se pueden serializar, pero las derivadas de `CPtrList` no.

Cuando se elimina un objeto `CTypedPtrList`, o cuando se quitan sus elementos, solo se quitan los punteros, no las entidades a las que hacen referencia.

Para obtener más `CTypedPtrList`información sobre el uso de , vea los artículos [Colecciones](../../mfc/collections.md) y [Clases basadas en plantillas](../../mfc/template-based-classes.md).

## <a name="example"></a>Ejemplo

En este ejemplo `CTypedPtrList`se crea una instancia de , agrega un objeto, serializa la lista al disco y, a continuación, se elimina el objeto:

[!code-cpp[NVC_MFCCollections#110](../../mfc/codesnippet/cpp/ctypedptrlist-class_1.cpp)]

[!code-cpp[NVC_MFCCollections#111](../../mfc/codesnippet/cpp/ctypedptrlist-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BASE_CLASS`

`_CTypedPtrList`

`CTypedPtrList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

## <a name="ctypedptrlistaddhead"></a><a name="addhead"></a>CTypedPtrList::AddHead

Esta función `BASE_CLASS`miembro llama **a ::AddHead**.

```
POSITION AddHead(TYPE newElement);
void AddHead(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Tipo de los elementos almacenados en la lista de clase base.

*newElement*<br/>
El puntero de objeto que se agregará a esta lista. Se permite un valor NULL.

*BASE_CLASS*<br/>
Clase base de la clase de lista de punteros con tipo; debe ser una clase de lista de punteros ( [CObList](../../mfc/reference/coblist-class.md) o [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Un puntero a otro [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objeto. Los elementos de *pNewList* se agregarán a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve el valor POSITION del elemento recién insertado.

### <a name="remarks"></a>Observaciones

La primera versión agrega un nuevo elemento antes del jefe de la lista. La segunda versión añade otra lista de elementos antes de la cabeza.

## <a name="ctypedptrlistaddtail"></a><a name="addtail"></a>CTypedPtrList::AddTail

Esta función `BASE_CLASS`miembro llama **a ::AddTail**.

```
POSITION AddTail(TYPE newElement);
void AddTail(CTypedPtrList<BASE_CLASS, TYPE>* pNewList);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Tipo de los elementos almacenados en la lista de clase base.

*newElement*<br/>
El puntero de objeto que se agregará a esta lista. Se permite un valor NULL.

*BASE_CLASS*<br/>
Clase base de la clase de lista de punteros con tipo; debe ser una clase de lista de punteros ( [CObList](../../mfc/reference/coblist-class.md) o [CPtrList](../../mfc/reference/cptrlist-class.md)).

*pNewList*<br/>
Un puntero a otro [CTypedPtrList](../../mfc/reference/ctypedptrlist-class.md) objeto. Los elementos de *pNewList* se agregarán a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve el valor POSITION del elemento recién insertado.

### <a name="remarks"></a>Observaciones

La primera versión agrega un nuevo elemento después de la cola de la lista. La segunda versión añade otra lista de elementos después de la cola de la lista.

## <a name="ctypedptrlistgetat"></a><a name="getat"></a>CTypedPtrList::GetAt

Una variable de tipo POSITION es una clave para la lista.

```
TYPE& GetAt(POSITION position);
TYPE GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

*Posición*<br/>
Un valor POSITION devuelto `GetHeadPosition` `Find` por una llamada a una función anterior o miembro.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a `const CTypedPtrList`la `GetAt` lista a través de un puntero a un , a continuación, devuelve un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y, por lo tanto, protege la lista de modificaciones.

Si se tiene acceso a la `CTypedPtrList`lista `GetAt` directamente o a través de un puntero a un , a continuación, devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

No es lo mismo que un índice y no puede operar en un valor POSITION usted mismo. `GetAt`recupera el `CObject` puntero asociado a una posición determinada.

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Esta función `BASE_CLASS`en línea llama **a ::GetAt**.

## <a name="ctypedptrlistgethead"></a><a name="gethead"></a>CTypedPtrList::GetHead

Obtiene el puntero que representa el elemento head de esta lista.

```
TYPE& GetHead();
TYPE GetHead() const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a `const CTypedPtrList`la `GetHead` lista a través de un puntero a un , a continuación, devuelve un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y, por lo tanto, protege la lista de modificaciones.

Si se tiene acceso a la `CTypedPtrList`lista `GetHead` directamente o a través de un puntero a un , a continuación, devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `GetHead`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.

## <a name="ctypedptrlistgetnext"></a><a name="getnext"></a>CTypedPtrList::GetNext

Obtiene el elemento de lista identificado por *rPosition*y, a continuación, establece *rPosition* en el valor POSITION de la siguiente entrada de la lista.

```
TYPE& GetNext(POSITION& rPosition);
TYPE GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos contenidos en esta lista.

*rPosición*<br/>
Una referencia a un valor `GetNext`POSITION `GetHeadPosition`devuelto por una llamada a una función anterior , , u otra función miembro.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a `const CTypedPtrList`la `GetNext` lista a través de un puntero a un , a continuación, devuelve un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y, por lo tanto, protege la lista de modificaciones.

Si se tiene acceso a la `CTypedPtrList`lista `GetNext` directamente o a través de un puntero a un , a continuación, devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

Puede utilizar `GetNext` en un bucle de iteración directa `GetHeadPosition` si establece la posición inicial con una llamada a o [CPtrList::Find](../../mfc/reference/coblist-class.md#find).

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Si el elemento recuperado es el último de la lista, el nuevo valor de *rPosition* se establece en NULL.

Es posible quitar un elemento durante una iteración. Vea el ejemplo de [CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat).

## <a name="ctypedptrlistgetprev"></a><a name="getprev"></a>CTypedPtrList::GetPrev

Obtiene el elemento de lista identificado por *rPosition*y, a continuación, establece *rPosition* en el valor POSITION de la entrada anterior de la lista.

```
TYPE& GetPrev(POSITION& rPosition);
TYPE GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos contenidos en esta lista.

*rPosición*<br/>
Una referencia a un valor `GetPrev` POSITION devuelto por una llamada a una función miembro anterior u otra.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a `const CTypedPtrList`la `GetPrev` lista a través de un puntero a un , a continuación, devuelve un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y, por lo tanto, protege la lista de modificaciones.

Si se tiene acceso a la `CTypedPtrList`lista `GetPrev` directamente o a través de un puntero a un , a continuación, devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

Puede utilizar `GetPrev` en un bucle de iteración inversa `GetTailPosition` `Find`si establece la posición inicial con una llamada a o .

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Si el elemento recuperado es el primero de la lista, el nuevo valor de *rPosition* se establece en NULL.

## <a name="ctypedptrlistgettail"></a><a name="gettail"></a>CTypedPtrList::GetTail

Obtiene el puntero que representa el elemento head de esta lista.

```
TYPE& GetTail();
TYPE GetTail() const;
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a `const CTypedPtrList`la `GetTail` lista a través de un puntero a un , a continuación, devuelve un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y, por lo tanto, protege la lista de modificaciones.

Si se tiene acceso a la `CTypedPtrList`lista `GetTail` directamente o a través de un puntero a un , a continuación, devuelve una referencia a un puntero del tipo especificado por el parámetro de plantilla *TYPE*. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `GetTail`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.

## <a name="ctypedptrlistremovehead"></a><a name="removehead"></a>CTypedPtrList::RemoveHead

Quita el elemento del jefe de la lista y lo devuelve.

```
TYPE RemoveHead();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

### <a name="return-value"></a>Valor devuelto

El puntero anteriormente en la cabecera de la lista. Este puntero es del tipo especificado por el parámetro de plantilla *TYPE*.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `RemoveHead`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.

## <a name="ctypedptrlistremovetail"></a><a name="removetail"></a>CTypedPtrList::RemoveTail

Quita el elemento de la cola de la lista y lo devuelve.

```
TYPE RemoveTail();
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos almacenados en la lista.

### <a name="return-value"></a>Valor devuelto

El puntero anteriormente en la cola de la lista. Este puntero es del tipo especificado por el parámetro de plantilla *TYPE*.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `RemoveTail`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](../../mfc/reference/coblist-class.md#isempty) para comprobar que la lista contiene elementos.

## <a name="ctypedptrlistsetat"></a><a name="setat"></a>CTypedPtrList::SetAt

Esta función `BASE_CLASS`miembro llama **a ::SetAt**.

```
void SetAt(POSITION pos, TYPE newElement);
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
POSITION del elemento que se va a establecer.

*TIPO*<br/>
Tipo de los elementos almacenados en la lista de clase base.

*newElement*<br/>
El puntero de objeto que se va a escribir en la lista.

### <a name="remarks"></a>Observaciones

Una variable de tipo POSITION es una clave para la lista. No es lo mismo que un índice y no puede operar en un valor POSITION usted mismo. `SetAt`escribe el puntero del objeto a la posición especificada en la lista.

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Para obtener comentarios más detallados, vea [CObList::SetAt](../../mfc/reference/coblist-class.md#setat).

## <a name="see-also"></a>Consulte también

[RECOPILACIÓN de muestras de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CPtrList](../../mfc/reference/cptrlist-class.md)<br/>
[CObList (clase)](../../mfc/reference/coblist-class.md)
