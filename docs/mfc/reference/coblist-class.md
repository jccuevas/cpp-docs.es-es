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
ms.openlocfilehash: 2fc3a3643c675394de555f1411030e278bcee775
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424036"
---
# <a name="coblist-class"></a>CObList (clase)

fSupports listas ordenadas de punteros `CObject` no únicos accesibles secuencialmente o por valor de puntero.

## <a name="syntax"></a>Sintaxis

```
class CObList : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObList:: CObList](#coblist)|Crea una lista vacía para los punteros de `CObject`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObList:: AddHead](#addhead)|Agrega un elemento (o todos los elementos de otra lista) al encabezado de la lista (crea un nuevo encabezado).|
|[CObList:: Addtail (](#addtail)|Agrega un elemento (o todos los elementos de otra lista) al final de la lista (crea una nueva cola).|
|[CObList:: Find](#find)|Obtiene la posición de un elemento especificado por el valor de puntero.|
|[CObList:: FindIndex](#findindex)|Obtiene la posición de un elemento especificado por un índice basado en cero.|
|[CObList:: GetAt](#getat)|Obtiene el elemento en una posición determinada.|
|[CObList:: GetCount](#getcount)|Devuelve el número de elementos de esta lista.|
|[CObList:: GetHead](#gethead)|Devuelve el elemento de encabezado de la lista (no puede estar vacío).|
|[CObList:: GetHeadPosition](#getheadposition)|Devuelve la posición del elemento de encabezado de la lista.|
|[CObList:: GetNext](#getnext)|Obtiene el siguiente elemento para recorrer en iteración.|
|[CObList:: GetPrev](#getprev)|Obtiene el elemento anterior para la iteración.|
|[CObList:: se obtiene](#getsize)|Devuelve el número de elementos de esta lista.|
|[CObList:: GetTail](#gettail)|Devuelve el elemento de cola de la lista (no puede estar vacío).|
|[CObList:: GetTailPosition](#gettailposition)|Devuelve la posición del elemento tail de la lista.|
|[CObList:: InsertAfter](#insertafter)|Inserta un nuevo elemento después de una posición determinada.|
|[CObList:: InsertBefore](#insertbefore)|Inserta un nuevo elemento antes de una posición determinada.|
|[CObList:: IsEmpty](#isempty)|Comprueba la condición de lista vacía (no hay elementos).|
|[CObList:: RemoveAll](#removeall)|Quita todos los elementos de esta lista.|
|[CObList:: RemoveAt](#removeat)|Quita un elemento de esta lista, especificado por la posición.|
|[CObList:: RemoveHead](#removehead)|Quita el elemento del encabezado de la lista.|
|[CObList:: RemoveTail](#removetail)|Quita el elemento del final de la lista.|
|[CObList:: SetAt](#setat)|Establece el elemento en una posición determinada.|

## <a name="remarks"></a>Observaciones

`CObList` listas se comportan como listas de vínculos dobles.

Una variable de tipo POSITION es una clave para la lista. Puede usar una variable de posición como un iterador para recorrer una lista secuencialmente y como marcador para contener un lugar. Sin embargo, una posición no es lo mismo que un índice.

La inserción de elementos es muy rápida en el encabezado de la lista, en la cola y en una posición conocida. Es necesaria una búsqueda secuencial para buscar un elemento por valor o índice. Esta búsqueda puede ser lenta si la lista es larga.

`CObList` incorpora la macro IMPLEMENT_SERIAL para admitir la serialización y el volcado de sus elementos. Si una lista de punteros de `CObject` se almacena en un archivo, ya sea con un operador de inserción sobrecargado o con la función miembro `Serialize`, cada elemento `CObject` se serializa a su vez.

Si necesita un volcado de elementos de `CObject` individuales en la lista, debe establecer la profundidad del contexto de volcado en 1 o más.

Cuando se elimina un objeto de `CObList`, o cuando se quitan sus elementos, solo se quitan los punteros de `CObject`, no los objetos a los que hacen referencia.

Puede derivar sus propias clases de `CObList`. La nueva clase de lista, diseñada para contener punteros a objetos derivados de `CObject`, agrega nuevos miembros de datos y nuevas funciones miembro. Tenga en cuenta que la lista resultante no tiene seguridad de tipos estricta, porque permite la inserción de cualquier puntero `CObject`.

> [!NOTE]
>  Debe utilizar la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) en la implementación de la clase derivada si desea serializar la lista.

Para obtener más información sobre el uso de `CObList`, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CObList`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

##  <a name="addhead"></a>CObList:: AddHead

Agrega un nuevo elemento o lista de elementos al encabezado de esta lista.

```
POSITION AddHead(CObject* newElement);
void AddHead(CObList* pNewList);
```

### <a name="parameters"></a>Parámetros

*newElement*<br/>
Puntero de `CObject` que se va a agregar a esta lista.

*pNewList*<br/>
Puntero a otra lista de `CObList`. Los elementos de *pNewList* se agregarán a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve el valor de posición del elemento que se acaba de insertar.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::AddHead`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position AddHead (void** <strong>\*</strong> `newElement` **);**<br /><br /> **void AddHead (CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position AddHead (const CString &** `newElement` **);**<br /><br /> **Posición AddHead (LPCTSTR** `newElement` **);**<br /><br /> **void AddHead (CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="remarks"></a>Observaciones

La lista puede estar vacía antes de la operación.

### <a name="example"></a>Ejemplo

  Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#89](../../mfc/codesnippet/cpp/coblist-class_1.cpp)]

Los resultados de este programa son los siguientes:

```Output
AddHead example: A CObList with 2 elements
a CAge at $44A8 40
a CAge at $442A 21
```

##  <a name="addtail"></a>CObList:: Addtail (

Agrega un nuevo elemento o lista de elementos al final de esta lista.

```
POSITION AddTail(CObject* newElement);
void AddTail(CObList* pNewList);
```

### <a name="parameters"></a>Parámetros

*newElement*<br/>
Puntero de `CObject` que se va a agregar a esta lista.

*pNewList*<br/>
Puntero a otra lista de `CObList`. Los elementos de *pNewList* se agregarán a esta lista.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve el valor de posición del elemento que se acaba de insertar.

### <a name="remarks"></a>Observaciones

La lista puede estar vacía antes de la operación.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::AddTail`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Position addtail ((void** <strong>\*</strong> `newElement` **);**<br /><br /> **void addtail ((CPtrList** <strong>\*</strong> `pNewList` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position addtail ((const CString &** `newElement` **);**<br /><br /> **Posición addtail ((LPCTSTR** `newElement` **);**<br /><br /> **void addtail ((CStringList** <strong>\*</strong> `pNewList` **);**|

### <a name="example"></a>Ejemplo

  Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#90](../../mfc/codesnippet/cpp/coblist-class_2.cpp)]

Los resultados de este programa son los siguientes:

```Output
AddTail example: A CObList with 2 elements
a CAge at $444A 21
a CAge at $4526 40
```

##  <a name="coblist"></a>CObList:: CObList

Construye una lista de punteros `CObject` vacía.

```
CObList(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Granularidad de asignación de memoria para extender la lista.

### <a name="remarks"></a>Observaciones

A medida que la lista aumenta, la memoria se asigna en unidades de entradas de *nBlockSize* . Si se produce un error en una asignación de memoria, se produce una `CMemoryException`.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::CObList`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**CPtrList (INT_PTR** `nBlockSize` **= 10);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CStringList (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Ejemplo

  A continuación se muestra una lista de la clase derivada de `CObject``CAge` que se usa en todos los ejemplos de colección:

[!code-cpp[NVC_MFCCollections#91](../../mfc/codesnippet/cpp/coblist-class_3.h)]

A continuación se muestra un ejemplo de uso del constructor de `CObList`:

[!code-cpp[NVC_MFCCollections#92](../../mfc/codesnippet/cpp/coblist-class_4.cpp)]

##  <a name="find"></a>CObList:: Find

Busca la lista secuencialmente para buscar el primer puntero `CObject` que coincida con el puntero de `CObject` especificado.

```
POSITION Find(
    CObject* searchValue,
    POSITION startAfter = NULL) const;
```

### <a name="parameters"></a>Parámetros

*searchValue*<br/>
Puntero de objeto que se va a buscar en esta lista.

*startAfter*<br/>
Posición inicial de la búsqueda.

### <a name="return-value"></a>Valor devuelto

Valor de posición que se puede utilizar para la recuperación del puntero de iteración o de objeto; Es NULL si no se encuentra el objeto.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que se comparan los valores de puntero, no el contenido de los objetos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::Find`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Posición de búsqueda (void** <strong>\*</strong> `searchValue` **, posición** `startAfter` **= null) Const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Posición de búsqueda (LPCTSTR** `searchValue` **, posición** `startAfter` **= null) Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#93](../../mfc/codesnippet/cpp/coblist-class_5.cpp)]

##  <a name="findindex"></a>CObList:: FindIndex

Usa el valor de *NINDEX* como índice en la lista.

```
POSITION FindIndex(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del elemento de lista que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Valor de posición que se puede utilizar para la recuperación del puntero de iteración o de objeto; Es NULL si *NINDEX* es demasiado grande. (El marco de trabajo genera una aserción si *NINDEX* es negativo).

### <a name="remarks"></a>Observaciones

Inicia un examen secuencial desde el principio de la lista y se detiene en el elemento *n*.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::FindIndex`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Posición FindIndex (INT_PTR** `nIndex` **) Const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Posición FindIndex (INT_PTR** `nIndex` **) Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#94](../../mfc/codesnippet/cpp/coblist-class_6.cpp)]

##  <a name="getat"></a>CObList:: GetAt

Una variable de tipo POSITION es una clave para la lista.

```
CObject*& GetAt(POSITION position);
const CObject*& GetAt(POSITION position) const;
```

### <a name="parameters"></a>Parámetros

*position*<br/>
Un valor de posición devuelto por una llamada de función miembro `GetHeadPosition` o `Find` anterior.

### <a name="return-value"></a>Valor devuelto

Vea la descripción del valor devuelto para [GetHead](#gethead).

### <a name="remarks"></a>Observaciones

No es lo mismo que un índice y no puede trabajar en un valor de posición. `GetAt` recupera el puntero de `CObject` asociado a una posición determinada.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, la versión de depuración del biblioteca MFC valida.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetAd (** *posición* de posición **) Const;**<br /><br /> **void\*& GetAd (** *posición* de posición **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetAd (** *posición* de posición **) Const;**<br /><br /> **CString & GetAd (** *posición* de posición **);**|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [FindIndex](#findindex).

##  <a name="getcount"></a>CObList:: GetCount

Obtiene el número de elementos de esta lista.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Valor entero que contiene el recuento de elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetCount`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR GetCount () Const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR GetCount () Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#95](../../mfc/codesnippet/cpp/coblist-class_7.cpp)]

##  <a name="gethead"></a>CObList:: GetHead

Obtiene el puntero `CObject` que representa el elemento de encabezado de esta lista.

```
CObject*& GetHead();
const CObject*& GetHead() const;
```

### <a name="return-value"></a>Valor devuelto

Si se tiene acceso a la lista a través de un puntero a un `const CObList`, `GetHead` devuelve un puntero de `CObject`. Esto permite que la función se use solo en el lado derecho de una instrucción de asignación y, por tanto, protege la lista de la modificación.

Si se tiene acceso a la lista directamente o a través de un puntero a un `CObList`, `GetHead` devuelve una referencia a un puntero de `CObject`. Esto permite que la función se use en cualquier lado de una instrucción de asignación y, por tanto, permite que se modifiquen las entradas de la lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la lista no esté vacía antes de llamar a `GetHead`. Si la lista está vacía, la versión de depuración del biblioteca MFC valida. Use [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetHead`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetHead () Const; void\*& GetHead ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetHead () Const; CString & GetHead ();**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

En el ejemplo siguiente se muestra el uso de `GetHead` en el lado izquierdo de una instrucción de asignación.

[!code-cpp[NVC_MFCCollections#96](../../mfc/codesnippet/cpp/coblist-class_8.cpp)]

##  <a name="getheadposition"></a>CObList:: GetHeadPosition

Obtiene la posición del elemento de encabezado de esta lista.

```
POSITION GetHeadPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de posición que se puede utilizar para la recuperación del puntero de iteración o de objeto; Es NULL si la lista está vacía.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetHeadPosition`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetHeadPosition () Const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetHeadPosition () Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#97](../../mfc/codesnippet/cpp/coblist-class_9.cpp)]

##  <a name="getnext"></a>CObList:: GetNext

Obtiene el elemento de lista identificado por *rPosition*y, a continuación, establece *rPosition* en el valor `POSITION` de la entrada siguiente en la lista.

```
CObject*& GetNext(POSITION& rPosition);
const CObject* GetNext(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*rPosition*<br/>
Referencia a un valor de posición devuelto por una `GetNext`anterior, `GetHeadPosition`u otra llamada de función miembro.

### <a name="return-value"></a>Valor devuelto

Vea la descripción del valor devuelto para [GetHead](#gethead).

### <a name="remarks"></a>Observaciones

Puede usar `GetNext` en un bucle de iteración hacia delante si establece la posición inicial con una llamada a `GetHeadPosition` o `Find`.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, la versión de depuración del biblioteca MFC valida.

Si el elemento recuperado es el último de la lista, el nuevo valor de *rPosition* se establece en NULL.

Es posible quitar un elemento durante una iteración. Vea el ejemplo de [RemoveAt](#removeat).

> [!NOTE]
>  A partir de MFC 8,0, la versión const de este método ha cambiado para devolver `const CObject*` en lugar de `const CObject*&`.  Este cambio se realizó para que el compilador cumpla con el C++ estándar.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetNext`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const void* GetNext( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetNext( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetNext( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Ejemplo

  Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#98](../../mfc/codesnippet/cpp/coblist-class_10.cpp)]

Los resultados de este programa son los siguientes:

```Output
a CAge at $479C 40
a CAge at $46C0 21
```

##  <a name="getprev"></a>CObList:: GetPrev

Obtiene el elemento de lista identificado por *rPosition*y, a continuación, establece *rPosition* en el valor de posición de la entrada anterior en la lista.

```
CObject*& GetPrev(POSITION& rPosition);
const CObject* GetPrev(POSITION& rPosition) const;
```

### <a name="parameters"></a>Parámetros

*rPosition*<br/>
Referencia a un valor de posición devuelto por una `GetPrev` anterior u otra llamada de función miembro.

### <a name="return-value"></a>Valor devuelto

Vea la descripción del valor devuelto para [GetHead](#gethead).

### <a name="remarks"></a>Observaciones

Puede usar `GetPrev` en un bucle de iteración inversa si establece la posición inicial con una llamada a `GetTailPosition` o `Find`.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, la versión de depuración del biblioteca MFC valida.

Si el elemento recuperado es el primero de la lista, el nuevo valor de *rPosition* se establece en NULL.

> [!NOTE]
>  A partir de MFC 8,0, la versión const de este método ha cambiado para devolver `const CObject*` en lugar de `const CObject*&`.  Este cambio se realizó para que el compilador cumpla con el C++ estándar.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetPrev`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|`void*& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const void* GetPrev( POSITION&` `rPosition` `) const;`|
|[CStringList](../../mfc/reference/cstringlist-class.md)|`CString& GetPrev( POSITION&` `rPosition` `);`<br /><br /> `const CString& GetPrev( POSITION&` `rPosition` `) const;`|

### <a name="example"></a>Ejemplo

  Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#99](../../mfc/codesnippet/cpp/coblist-class_11.cpp)]

Los resultados de este programa son los siguientes:

```Output
a CAge at $421C 21
a CAge at $421C 40
```

##  <a name="getsize"></a>CObList:: se obtiene

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
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**INT_PTR se obtiene () Const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**INT_PTR se obtiene () Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#100](../../mfc/codesnippet/cpp/coblist-class_12.cpp)]

##  <a name="gettail"></a>CObList:: GetTail

Obtiene el puntero `CObject` que representa el elemento tail de esta lista.

```
CObject*& GetTail();
const CObject*& GetTail() const;
```

### <a name="return-value"></a>Valor devuelto

Vea la descripción del valor devuelto para [GetHead](#gethead).

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la lista no esté vacía antes de llamar a `GetTail`. Si la lista está vacía, la versión de depuración del biblioteca MFC valida. Use [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetTail`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**const void\*& GetTail () Const; void\*& GetTail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**const CString & GetTail () Const; CString & GetTail ();**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#101](../../mfc/codesnippet/cpp/coblist-class_13.cpp)]

##  <a name="gettailposition"></a>CObList:: GetTailPosition

Obtiene la posición del elemento tail de esta lista; Es **null** si la lista está vacía.

```
POSITION GetTailPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de posición que se puede utilizar para la recuperación del puntero de iteración o de objeto; Es NULL si la lista está vacía.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::GetTailPosition`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**POSITION GetTailPosition () Const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**POSITION GetTailPosition () Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#102](../../mfc/codesnippet/cpp/coblist-class_14.cpp)]

##  <a name="insertafter"></a>CObList:: InsertAfter

Agrega un elemento a esta lista después del elemento en la posición especificada.

```
POSITION InsertAfter(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*position*<br/>
Un valor de posición devuelto por una llamada anterior a la función miembro `GetNext`, `GetPrev`o `Find`.

*newElement*<br/>
Puntero de objeto que se va a agregar a esta lista.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::InsertAfter`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Posición InsertAfter (** *posición* **de posición, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Position InsertAfter (** *posición* **de posición, const CString &** `newElement` **);**<br /><br /> La **posición InsertAfter (** *posición* **de posición, LPCTSTR** `newElement` **);**|

### <a name="return-value"></a>Valor devuelto

Valor de posición que es igual que el parámetro de *posición* .

### <a name="example"></a>Ejemplo

  Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#103](../../mfc/codesnippet/cpp/coblist-class_15.cpp)]

Los resultados de este programa son los siguientes:

```Output
InsertAfter example: A CObList with 3 elements
a CAge at $4A44 40
a CAge at $4A64 65
a CAge at $4968 21
```

##  <a name="insertbefore"></a>CObList:: InsertBefore

Agrega un elemento a esta lista delante del elemento en la posición especificada.

```
POSITION InsertBefore(
    POSITION position,
    CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*position*<br/>
Un valor de posición devuelto por una llamada anterior a la función miembro `GetNext`, `GetPrev`o `Find`.

*newElement*<br/>
Puntero de objeto que se va a agregar a esta lista.

### <a name="return-value"></a>Valor devuelto

Valor de posición que se puede utilizar para la recuperación del puntero de iteración o de objeto; Es NULL si la lista está vacía.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::InsertBefore`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**Posición de InsertBefore (** *position* **, void** <strong>\*</strong> `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**Posición InsertBefore (** *posición* **de posición, const CString &** `newElement` **);**<br /><br /> **Posición de InsertBefore (** *position* **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Ejemplo

  Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#104](../../mfc/codesnippet/cpp/coblist-class_16.cpp)]

Los resultados de este programa son los siguientes:

```Output
InsertBefore example: A CObList with 3 elements
a CAge at $4AE2 40
a CAge at $4B02 65
a CAge at $49E6 21
```

##  <a name="isempty"></a>CObList:: IsEmpty

Indica si esta lista no contiene elementos.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si esta lista está vacía; de lo contrario, es 0.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::IsEmpty`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**BOOL IsEmpty () Const;**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**BOOL IsEmpty () Const;**|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [RemoveAll](#removeall).

##  <a name="removeall"></a>CObList:: RemoveAll

Quita todos los elementos de esta lista y libera la memoria `CObList` asociada.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Si la lista ya está vacía, no se genera ningún error.

Cuando se quitan elementos de un `CObList`, se quitan los punteros de objeto de la lista. Es su responsabilidad eliminar los propios objetos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::RemoveAll`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAll ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#105](../../mfc/codesnippet/cpp/coblist-class_17.cpp)]

##  <a name="removeat"></a>CObList:: RemoveAt

Quita el elemento especificado de esta lista.

```
void RemoveAt(POSITION position);
```

### <a name="parameters"></a>Parámetros

*position*<br/>
Posición del elemento que se va a quitar de la lista.

### <a name="remarks"></a>Observaciones

Al quitar un elemento de un `CObList`, se quita el puntero de objeto de la lista. Es su responsabilidad eliminar los propios objetos.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, la versión de depuración del biblioteca MFC valida.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::RemoveAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void RemoveAt (** *posición* de posición **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void RemoveAt (** *posición* de posición **);**|

### <a name="example"></a>Ejemplo

  Tenga cuidado al quitar un elemento durante una iteración de la lista. En el ejemplo siguiente se muestra una técnica de eliminación que garantiza un valor de **posición** válido para [Getnext](#getnext).

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#106](../../mfc/codesnippet/cpp/coblist-class_18.cpp)]

Los resultados de este programa son los siguientes:

`RemoveAt example: A CObList with 2 elements`

`a CAge at $4C1E 65`

`a CAge at $4B22 21`

##  <a name="removehead"></a>CObList:: RemoveHead

Quita el elemento del encabezado de la lista y le devuelve un puntero.

```
CObject* RemoveHead();
```

### <a name="return-value"></a>Valor devuelto

El puntero `CObject` previamente en el encabezado de la lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la lista no esté vacía antes de llamar a `RemoveHead`. Si la lista está vacía, la versión de depuración del biblioteca MFC valida. Use [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::RemoveHead`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveHead ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveHead ();**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#107](../../mfc/codesnippet/cpp/coblist-class_19.cpp)]

##  <a name="removetail"></a>CObList:: RemoveTail

Quita el elemento del final de la lista y le devuelve un puntero.

```
CObject* RemoveTail();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto que estaba en el final de la lista.

### <a name="remarks"></a>Observaciones

Debe asegurarse de que la lista no esté vacía antes de llamar a `RemoveTail`. Si la lista está vacía, la versión de depuración del biblioteca MFC valida. Use [IsEmpty](#isempty) para comprobar que la lista contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::RemoveTail`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void\* RemoveTail ();**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**CString RemoveTail ();**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#108](../../mfc/codesnippet/cpp/coblist-class_20.cpp)]

##  <a name="setat"></a>CObList:: SetAt

Establece el elemento en una posición determinada.

```
void SetAt(
    POSITION pos,
    CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*pos*<br/>
POSICIÓN del elemento que se va a establecer.

*newElement*<br/>
Puntero de `CObject` que se va a escribir en la lista.

### <a name="remarks"></a>Observaciones

Una variable de tipo POSITION es una clave para la lista. No es lo mismo que un índice y no puede trabajar en un valor de posición. `SetAt` escribe el puntero de `CObject` en la posición especificada de la lista.

Debe asegurarse de que el valor de posición representa una posición válida en la lista. Si no es válido, la versión de depuración del biblioteca MFC valida.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObList::SetAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CPtrList](../../mfc/reference/cptrlist-class.md)|**void SetAt (POSITION** `pos` **, const CString &** `newElement` **);**|
|[CStringList](../../mfc/reference/cstringlist-class.md)|**void SetAt (POSITION** `pos` **, LPCTSTR** `newElement` **);**|

### <a name="example"></a>Ejemplo

  Vea [CObList:: CObList](#coblist) para obtener una lista de la clase `CAge`.

[!code-cpp[NVC_MFCCollections#109](../../mfc/codesnippet/cpp/coblist-class_21.cpp)]

Los resultados de este programa son los siguientes:

```Output
SetAt example: A CObList with 2 elements
a CAge at $4D98 40
a CAge at $4DB8 65
```

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CStringList (clase)](../../mfc/reference/cstringlist-class.md)<br/>
[CPtrList (clase)](../../mfc/reference/cptrlist-class.md)
