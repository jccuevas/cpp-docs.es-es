---
title: CObList (clase)
ms.date: 11/04/2016
f1_keywords:
- CObList
- AFXCOLL/CObList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 80699c93-33d8-4f8b-b8cf-7b58aeab64ca
ms.openlocfilehash: f24965357e0b71f28ba39b82d045600e7e1a44e2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749689"
---
# <a name="coblist-class"></a>CObList (clase)

fSupports listas ordenadas `CObject` de punteros no únicos accesibles secuencialmente o por valor de puntero.

## <a name="syntax"></a>Sintaxis

```
class CObList : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObList::CObList](#coblist)|Construye una lista `CObject` vacía para los punteros.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObList::AddHead](#addhead)|Agrega un elemento (o todos los elementos de otra lista) al jefe de la lista (hace una nueva cabeza).|
|[CObList::AddTail](#addtail)|Agrega un elemento (o todos los elementos de otra lista) a la cola de la lista (hace una nueva cola).|
|[CObList::Buscar](#find)|Obtiene la posición de un elemento especificado por el valor del puntero.|
|[CObList::FindIndex](#findindex)|Obtiene la posición de un elemento especificado por un índice de base cero.|
|[COblist::GetAt](#getat)|Obtiene el elemento en una posición determinada.|
|[CObList::GetCount](#getcount)|Devuelve el número de elementos de esta lista.|
|[CObList::GetHead](#gethead)|Devuelve el elemento head de la lista (no puede estar vacío).|
|[CObList::GetHeadPosition](#getheadposition)|Devuelve la posición del elemento head de la lista.|
|[CObList::GetNext](#getnext)|Obtiene el siguiente elemento para iterar.|
|[CObList::GetPrev](#getprev)|Obtiene el elemento anterior para iterar.|
|[CObList::GetSize](#getsize)|Devuelve el número de elementos de esta lista.|
|[CObList::GetTail](#gettail)|Devuelve el elemento tail de la lista (no puede estar vacío).|
|[CObList::GetTailPosition](#gettailposition)|Devuelve la posición del elemento de cola de la lista.|
|[CObList::InsertAfter](#insertafter)|Inserta un nuevo elemento después de una posición determinada.|
|[CObList::InsertBefore](#insertbefore)|Inserta un nuevo elemento antes de una posición determinada.|
|[CObList::IsEmpty](#isempty)|Comprueba la condición de lista vacía (sin elementos).|
|[CObList::RemoveAll](#removeall)|Elimina todos los elementos de esta lista.|
|[COblist::RemoveAt](#removeat)|Quita un elemento de esta lista, especificado por position.|
|[CObList::RemoveHead](#removehead)|Quita el elemento del jefe de la lista.|
|[CObList::RemoveTail](#removetail)|Quita el elemento de la cola de la lista.|
|[COblist::SetAt](#setat)|Establece el elemento en una posición determinada.|

## <a name="remarks"></a>Observaciones

`CObList`las listas se comportan como listas doblemente vinculadas.

Una variable de tipo POSITION es una clave para la lista. Puede utilizar una variable POSITION como iterador para recorrer una lista secuencialmente y como marcador para mantener un lugar. Sin embargo, una posición no es lo mismo que un índice.

La inserción de elementos es muy rápida en el cabezal de lista, en la cola y en una POSICIÓN conocida. Una búsqueda secuencial es necesaria para buscar un elemento por valor o índice. Esta búsqueda puede ser lenta si la lista es larga.

`CObList`incorpora la macro IMPLEMENT_SERIAL para admitir la serialización y el volcado de sus elementos. Si se `CObject` almacena una lista de punteros en un archivo, `Serialize` ya sea `CObject` con un operador de inserción sobrecargado o con la función miembro, cada elemento se serializa a su vez.

Si necesita un volcado `CObject` de elementos individuales en la lista, debe establecer la profundidad del contexto de volcado en 1 o superior.

Cuando `CObList` se elimina un objeto, o cuando `CObject` se quitan sus elementos, solo se quitan los punteros, no los objetos a los que hacen referencia.

Puede derivar sus propias clases de `CObList`. La nueva clase de lista, diseñada para `CObject`contener punteros a objetos derivados de , agrega nuevos miembros de datos y nuevas funciones miembro. Tenga en cuenta que la lista resultante no es `CObject` estrictamente segura para el tipo, ya que permite la inserción de cualquier puntero.

> [!NOTE]
> Debe usar la [macro IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) en la implementación de la clase derivada si tiene la intención de serializar la lista.

Para obtener más `CObList`información sobre el uso , vea el artículo [Colecciones](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll.h

## <a name="coblistaddhead"></a><a name="addhead"></a>CObList::AddHead

Agrega un nuevo elemento o lista de elementos al jefe de esta lista.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parámetros

*newElement*<br/>
El `CObject` puntero que se agregará a esta lista.

*pNewList*<br/>
Un puntero `CObList` a otra lista. Los elementos de *pNewList* se agregarán a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve el valor POSITION del elemento recién insertado.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::AddHead`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddHead( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddHead(const CString&** `newElement` **);**<br /><br /> **POSITION AddHead(LPCTSTR** `newElement` **);**<br /><br /> **void AddHead(CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Observaciones

La lista puede estar vacía antes de la operación.

### <a name="example"></a>Ejemplo

  Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Los resultados de este programa son los siguientes:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

## <a name="coblistaddtail"></a><a name="addtail"></a>CObList::AddTail

Agrega un nuevo elemento o lista de elementos a la cola de esta lista.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parámetros

*newElement*<br/>
El `CObject` puntero que se agregará a esta lista.

*pNewList*<br/>
Un puntero `CObList` a otra lista. Los elementos de *pNewList* se agregarán a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve el valor POSITION del elemento recién insertado.

### <a name="remarks"></a>Observaciones

La lista puede estar vacía antes de la operación.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::AddTail`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION AddTail( void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddTail( CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION AddTail( const CString&** `newElement` **);**<br /><br /> **POSITION AddTail( LPCTSTR** `newElement` **);**<br /><br /> **void AddTail( CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Ejemplo

  Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Los resultados de este programa son los siguientes:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

## <a name="coblistcoblist"></a><a name="coblist"></a>CObList::CObList

Construye una `CObject` lista de punteros vacía.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
La granularidad de asignación de memoria para ampliar la lista.

### <a name="remarks"></a>Observaciones

A medida que crece la lista, la memoria se asigna en unidades de entradas *nBlockSize.* Si se produce un `CMemoryException` error en una asignación de memoria, se produce a.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::CObList`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList( INT_PTR** `nBlockSize` **a 10 );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList( INT_PTR** `nBlockSize` **a 10 );**|

### <a name="example"></a>Ejemplo

  A continuación se `CObject`muestra una `CAge` lista de la clase -derived utilizada en todos los ejemplos de colección:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

A continuación se `CObList` muestra un ejemplo del uso del constructor:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

## <a name="coblistfind"></a><a name="find"></a>CObList::Buscar

Busca la lista secuencialmente para `CObject` buscar el `CObject` primer puntero que coincida con el puntero especificado.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parámetros

*searchValue*<br/>
El puntero de objeto que se encuentra en esta lista.

*startAfter*<br/>
La posición inicial de la búsqueda.

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si no se encuentra el objeto.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que se comparan los valores del puntero, no el contenido de los objetos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::Find`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION Find( void** <strong>\*</strong> `searchValue` **, POSITION** `startAfter` **- NULL ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION Find( LPCTSTR** `searchValue` **, POSITION** `startAfter` **- NULL ) const;**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

## <a name="coblistfindindex"></a><a name="findindex"></a>CObList::FindIndex

Utiliza el valor de *nIndex* como índice en la lista.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del elemento de lista que se va a encontrar.

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si *nIndex* es demasiado grande. (El marco de trabajo genera una aserción si *nIndex* es negativo.)

### <a name="remarks"></a>Observaciones

Inicia un análisis secuencial desde el jefe de la lista, deteniéndose en el *nésimo*elemento.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::FindIndex`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION FindIndex( INT_PTR** `nIndex` **) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION FindIndex( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

## <a name="coblistgetat"></a><a name="getat"></a>COblist::GetAt

Una variable de tipo POSITION es una clave para la lista.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
Un valor POSITION devuelto `GetHeadPosition` `Find` por una llamada a una función anterior o miembro.

### <a name="return-value"></a>Valor devuelto

Consulte la descripción del valor devuelto para [GetHead](#gethead).

### <a name="remarks"></a>Observaciones

No es lo mismo que un índice y no puede operar en un valor POSITION usted mismo. `GetAt`recupera el `CObject` puntero asociado a una posición determinada.

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetAt( POSITION** *position* **) const;**<br /><br /> **vacío\*& GetAt( posición POSITION** *position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetAt( POSITION** *position* **) const;**<br /><br /> **CString& GetAt( POSITION** *position* **);**|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [FindIndex](#findindex).

## <a name="coblistgetcount"></a><a name="getcount"></a>CObList::GetCount

Obtiene el número de elementos de esta lista.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Valor entero que contiene el recuento de elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetCount`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

## <a name="coblistgethead"></a><a name="gethead"></a>CObList::GetHead

Obtiene el `CObject` puntero que representa el elemento head de esta lista.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a `const CObList`la `GetHead` lista `CObject` a través de un puntero a un , a continuación, devuelve un puntero. Esto permite que la función se utilice solo en el lado derecho de una instrucción de asignación y, por lo tanto, protege la lista de modificaciones.

Si se tiene acceso a la `CObList`lista `GetHead` directamente o `CObject` a través de un puntero a un , a continuación, devuelve una referencia a un puntero. Esto permite que la función se utilice a ambos lados de una instrucción de asignación y, por lo tanto, permite modificar las entradas de lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `GetHead`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetHead`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetHead( ) const; vacío\*& GetHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetHead( ) const; CString& GetHead( );**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

En el ejemplo siguiente `GetHead` se muestra el uso de en el lado izquierdo de una instrucción de asignación.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

## <a name="coblistgetheadposition"></a><a name="getheadposition"></a>CObList::GetHeadPosition

Obtiene la posición del elemento head de esta lista.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si la lista está vacía.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetHeadPosition`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition( ) const;**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

## <a name="coblistgetnext"></a><a name="getnext"></a>CObList::GetNext

Obtiene el elemento de lista identificado por *rPosition*y, a continuación, establece *rPosition* en el `POSITION` valor de la siguiente entrada de la lista.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*rPosición*<br/>
Una referencia a un valor `GetNext`POSITION `GetHeadPosition`devuelto por una llamada a una función anterior , , u otra función miembro.

### <a name="return-value"></a>Valor devuelto

Consulte la descripción del valor devuelto para [GetHead](#gethead).

### <a name="remarks"></a>Observaciones

Puede utilizar `GetNext` en un bucle de iteración directa `GetHeadPosition` si `Find`establece la posición inicial con una llamada a o .

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Si el elemento recuperado es el último de la lista, el nuevo valor de *rPosition* se establece en NULL.

Es posible quitar un elemento durante una iteración. Vea el ejemplo de [RemoveAt](#removeat).

> [!NOTE]
> A partir de MFC 8.0 la versión const de este método ha cambiado para devolver `const CObject*` en lugar de `const CObject*&`.  Este cambio se realizó para que el compilador se ajuste al estándar C++.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetNext`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Ejemplo

  Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Los resultados de este programa son los siguientes:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

## <a name="coblistgetprev"></a><a name="getprev"></a>CObList::GetPrev

Obtiene el elemento de lista identificado por *rPosition*y, a continuación, establece *rPosition* en el valor POSITION de la entrada anterior de la lista.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*rPosición*<br/>
Una referencia a un valor `GetPrev` POSITION devuelto por una llamada a una función miembro anterior u otra.

### <a name="return-value"></a>Valor devuelto

Consulte la descripción del valor devuelto para [GetHead](#gethead).

### <a name="remarks"></a>Observaciones

Puede utilizar `GetPrev` en un bucle de iteración inversa `GetTailPosition` `Find`si establece la posición inicial con una llamada a o .

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Si el elemento recuperado es el primero de la lista, el nuevo valor de *rPosition* se establece en NULL.

> [!NOTE]
> A partir de MFC 8.0 la versión const de este método ha cambiado para devolver `const CObject*` en lugar de `const CObject*&`.  Este cambio se realizó para que el compilador se ajuste al estándar C++.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetPrev`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Ejemplo

  Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Los resultados de este programa son los siguientes:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

## <a name="coblistgetsize"></a><a name="getsize"></a>CObList::GetSize

Devuelve el número de elementos de lista.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos de la lista.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de elementos de la lista.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetSize`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetSize( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

## <a name="coblistgettail"></a><a name="gettail"></a>CObList::GetTail

Obtiene el `CObject` puntero que representa el elemento de cola de esta lista.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Valor devuelto

Consulte la descripción del valor devuelto para [GetHead](#gethead).

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `GetTail`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetTail`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const\* void& GetTail( ) const; vacío\*& GetTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString& GetTail( ) const; CString& GetTail( );**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

## <a name="coblistgettailposition"></a><a name="gettailposition"></a>CObList::GetTailPosition

Obtiene la posición del elemento de cola de esta lista; **NULL** si la lista está vacía.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si la lista está vacía.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetTailPosition`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition( ) const;**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

## <a name="coblistinsertafter"></a><a name="insertafter"></a>CObList::InsertAfter

Agrega un elemento a esta lista después del elemento en la posición especificada.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
Un valor POSITION devuelto `GetNext` `GetPrev`por `Find` una llamada a una función anterior , , o miembro.

*newElement*<br/>
El puntero de objeto que se agregará a esta lista.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::InsertAfter`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertAfter( POSITION** *position* , **void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertAfter( POSITION** *position* , **const CString&** `newElement` **);**<br /><br /> **POSITION InsertAfter( POSITION** *position* , **LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que es el mismo que el parámetro *position.*

### <a name="example"></a>Ejemplo

  Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Los resultados de este programa son los siguientes:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

## <a name="coblistinsertbefore"></a><a name="insertbefore"></a>CObList::InsertBefore

Agrega un elemento a esta lista delante del elemento en la posición especificada.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
Un valor POSITION devuelto `GetNext` `GetPrev`por `Find` una llamada a una función anterior , , o miembro.

*newElement*<br/>
El puntero de objeto que se agregará a esta lista.

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si la lista está vacía.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::InsertBefore`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION InsertBefore( POSITION** *position* , **void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION InsertBefore( POSITION** *position* , **const CString&** `newElement` **);**<br /><br /> **POSITION InsertBefore( POSITION** *position* , **LPCTSTR** `newElement` **);**|

### <a name="example"></a>Ejemplo

  Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Los resultados de este programa son los siguientes:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

## <a name="coblistisempty"></a><a name="isempty"></a>CObList::IsEmpty

Indica si esta lista no contiene elementos.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si esta lista está vacía; de lo contrario 0.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::IsEmpty`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty( ) const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty( ) const;**|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [RemoveAll](#removeall).

## <a name="coblistremoveall"></a><a name="removeall"></a>CObList::RemoveAll

Elimina todos los elementos de esta `CObList` lista y libera la memoria asociada.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

No se genera ningún error si la lista ya está vacía.

Cuando se quitan `CObList`elementos de un , se quitan los punteros de objeto de la lista. Es su responsabilidad eliminar los propios objetos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::RemoveAll`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

## <a name="coblistremoveat"></a><a name="removeat"></a>COblist::RemoveAt

Quita el elemento especificado de esta lista.

```cpp
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parámetros

*Posición*<br/>
La posición del elemento que se va a eliminar de la lista.

### <a name="remarks"></a>Observaciones

Cuando se quita un `CObList`elemento de un , se quita el puntero de objeto de la lista. Es su responsabilidad eliminar los propios objetos.

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::RemoveAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt( POSITION** *position* **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt( POSITION** *position* **);**|

### <a name="example"></a>Ejemplo

  Tenga cuidado al quitar un elemento durante una iteración de lista. En el ejemplo siguiente se muestra una técnica de eliminación que garantiza un valor **POSITION** válido para [GetNext](#getnext).

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Los resultados de este programa son los siguientes:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

## <a name="coblistremovehead"></a><a name="removehead"></a>CObList::RemoveHead

Quita el elemento del jefe de la lista y devuelve un puntero a él.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Valor devuelto

El `CObject` puntero anteriormente en la cabecera de la lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `RemoveHead`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::RemoveHead`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead( );**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

## <a name="coblistremovetail"></a><a name="removetail"></a>CObList::RemoveTail

Quita el elemento de la cola de la lista y devuelve un puntero a él.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto que estaba en la cola de la lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la `RemoveTail`lista no está vacía antes de llamar a . Si la lista está vacía, la versión de depuración de la biblioteca microsoft Foundation Class afirma. Utilice [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::RemoveTail`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail( );**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail( );**|

### <a name="example"></a>Ejemplo

Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

## <a name="coblistsetat"></a><a name="setat"></a>COblist::SetAt

Establece el elemento en una posición determinada.

```cpp
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
POSITION del elemento que se va a establecer.

*newElement*<br/>
El `CObject` puntero que se va a escribir en la lista.

### <a name="remarks"></a>Observaciones

Una variable de tipo POSITION es una clave para la lista. No es lo mismo que un índice y no puede operar en un valor POSITION usted mismo. `SetAt`escribe el `CObject` puntero a la posición especificada en la lista.

Debe asegurarse de que el valor POSITION representa una posición válida en la lista. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::SetAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt( POSITION** `pos` **, const CString&** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt( POSITION** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Ejemplo

  Consulte [CObList::CObList](#coblist) para obtener `CAge` una lista de la clase.

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Los resultados de este programa son los siguientes:

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Vea también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CStringList](../../mfc/reference/cstringlist-class.md)<br/>
[Clase CPtrList](../../mfc/reference/cptrlist-class.md)
