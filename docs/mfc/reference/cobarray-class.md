---
title: Clase CObArray
ms.date: 11/04/2016
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: c19715f62704bfc97059421451929cbbec2506ce
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754471"
---
# <a name="cobarray-class"></a>Clase CObArray

Admite matrices de punteros `CObject` .

## <a name="syntax"></a>Sintaxis

```
class CObArray : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObArray::CObArray](#cobarray)|Construye una matriz `CObject` vacía para los punteros.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObArray::Add](#add)|Agrega un elemento al final de la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CObArray::Append](#append)|Anexa otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CObArray::Copy](#copy)|Copia otra matriz a la matriz; aumenta el tamaño de la matriz si es necesario.|
|[CObArray::ElementAt](#elementat)|Devuelve una referencia temporal al puntero del elemento dentro de la matriz.|
|[CObArray::FreeExtra](#freeextra)|Libera toda la memoria no usada por encima del límite superior actual.|
|[CObarray::GetAt](#getat)|Devuelve el valor en un índice dado.|
|[CObArray::GetCount](#getcount)|Obtiene el número de elementos de esta matriz.|
|[CObArray::GetData](#getdata)|Permite el acceso a los elementos de la matriz. Puede ser NULL.|
|[CObArray::GetSize](#getsize)|Obtiene el número de elementos de esta matriz.|
|[CObArray::GetUpperBound](#getupperbound)|Devuelve el índice válido de mayor tamaño.|
|[CObArray::InsertAt](#insertat)|Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.|
|[CObArray::IsEmpty](#isempty)|Determina si la matriz está vacía.|
|[CObArray::RemoveAll](#removeall)|Quita todos los elementos de esta matriz.|
|[CObArray::RemoveAt](#removeat)|Quita un elemento en un índice específico.|
|[CObArray::SetAt](#setat)|Establece el valor de un índice dado; la matriz no puede aumentar de tamaño.|
|[CObArray::SetAtGrow](#setatgrow)|Establece el valor de un índice dado; aumenta el tamaño de la matriz si es necesario.|
|[CObArray::SetSize](#setsize)|Establece el número de elementos que contendrá esta matriz.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CObArray::operator \[\]](#operator_at)|Establece u obtiene el elemento en el índice especificado.|

## <a name="remarks"></a>Observaciones

Estas matrices de objetos son similares a las matrices C, pero pueden reducirse y crecer dinámicamente según sea necesario.

Los índices de matriz siempre comienzan en la posición 0. Puede decidir si desea corregir el límite superior o permitir que la matriz se expanda al agregar elementos más allá del límite actual. La memoria se asigna de forma contigua al límite superior, incluso si algunos elementos son null.

En Win32, el `CObArray` tamaño de un objeto se limita únicamente a la memoria disponible.

Al igual que con una matriz `CObArray` C, el tiempo de acceso para un elemento indizado es constante y es independiente del tamaño de la matriz.

`CObArray`incorpora la macro IMPLEMENT_SERIAL para admitir la serialización y el volcado de sus elementos. Si una `CObject` matriz de punteros se almacena en un archivo, `Serialize` ya sea `CObject` con el operador de inserción sobrecargado o con la función miembro, cada elemento se serializa, a su vez, junto con su índice de matriz.

Si necesita un volcado `CObject` de elementos individuales en una `CDumpContext` matriz, debe establecer la profundidad del objeto en 1 o superior.

Cuando `CObArray` se elimina un objeto, o cuando `CObject` se quitan sus elementos, solo se quitan los punteros, no los objetos a los que hacen referencia.

> [!NOTE]
> Antes de usar una matriz, use `SetSize` para establecer su tamaño y asignarle memoria. Si no usa `SetSize`, al agregar elementos a la matriz, esta se reasigna y se copia con frecuencia. La reasignación y copia frecuentes son ineficaces y pueden fragmentar la memoria.

La derivación de la clase de matriz es similar a la derivación de lista. Para obtener más información sobre la derivación de una clase de lista de propósito especial, vea el artículo [Colecciones](../../mfc/collections.md).

> [!NOTE]
> Debe usar la macro IMPLEMENT_SERIAL en la implementación de la clase derivada si tiene la intención de serializar la matriz.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll.h

## <a name="cobarrayadd"></a><a name="add"></a>CObArray::Add

Agrega un nuevo elemento al final de una matriz, aumentando la matriz en 1.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*newElement*<br/>
El `CObject` puntero que se agregará a esta matriz.

### <a name="return-value"></a>Valor devuelto

El índice del elemento agregado.

### <a name="remarks"></a>Observaciones

Si [SetSize](#setsize) se ha utilizado con un *nGrowBy* valor mayor que 1, a continuación, se puede asignar memoria adicional. Sin embargo, el límite superior aumentará en sólo 1.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::Add`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Add( BYTE** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Add( DWORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Add( void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Add( LPCTSTR** `newElement` **); throw( CMemoryException\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Add( UINT** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR Add( WORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Ejemplo

  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Los resultados de este programa son los siguientes:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray::Append

Llame a esta función miembro para agregar el contenido de otra matriz al final de la matriz dada.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Origen de los elementos que se van a anexar a la matriz.

### <a name="return-value"></a>Valor devuelto

El índice del primer elemento anexado.

### <a name="remarks"></a>Observaciones

Las matrices deben ser del mismo tipo.

Si es `Append` necesario, puede asignar memoria adicional para dar cabida a los elementos anexados a la matriz.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::Append`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Append( const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Append( const CDWordArray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Append( const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Append( const CStringArray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Append( const CUIntArray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR Append( const CWordArray&** *src* **);**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObArray::Copy

Llame a esta función miembro para sobrescribir los elementos de la matriz dada con los elementos de otra matriz del mismo tipo.

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
Origen de los elementos que se van a copiar en la matriz.

### <a name="remarks"></a>Observaciones

`Copy`no libera memoria; sin embargo, `Copy` si es necesario, puede asignar memoria adicional para acomodar los elementos copiados en la matriz.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::Copy`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void Copy( const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Copy( const CDWordArray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Copy( const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void Copy( const CStringArray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void Copy( const CUIntArray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void Copy( const CWordArray&** *src* **);**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObArray::CObArray

Construye una `CObject` matriz de punteros vacía.

```
CObArray();
```

### <a name="remarks"></a>Observaciones

La matriz crece un elemento a la vez.

En la tabla siguiente se muestran otros constructores similares a `CObArray::CObArray`.

|Clase|Constructor|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObArray::ElementAt

Devuelve una referencia temporal al puntero del elemento dentro de la matriz.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y `GetUpperBound`menor o igual que el valor devuelto por .

### <a name="return-value"></a>Valor devuelto

Una referencia `CObject` a un puntero.

### <a name="remarks"></a>Observaciones

Se utiliza para implementar el operador de asignación del lado izquierdo para matrices. Tenga en cuenta que se trata de una función avanzada que solo se debe usar para implementar operadores de matriz especiales.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::ElementAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& ElementAt( INT_PTR** `nIndex` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& ElementAt( INT_PTR** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**vacío\*& ElementAt( INT_PTR** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& ElementAt( INT_PTR** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& ElementAt( INT_PTR** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& ElementAt( INT_PTR** `nIndex` **);**|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CObArray::GetSize](#getsize).

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObArray::FreeExtra

Libera cualquier memoria adicional que se haya asignado mientras se cultivaba la matriz.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Observaciones

Esta función no tiene ningún efecto sobre el tamaño o el límite superior de la matriz.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::FreeExtra`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**vacío FreeExtra( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**vacío FreeExtra( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**vacío FreeExtra( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**vacío FreeExtra( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**vacío FreeExtra( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**vacío FreeExtra( );**|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CObArray::GetData](#getdata).

## <a name="cobarraygetat"></a><a name="getat"></a>CObarray::GetAt

Devuelve el elemento de matriz en el índice especificado.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y `GetUpperBound`menor o igual que el valor devuelto por .

### <a name="return-value"></a>Valor devuelto

El `CObject` elemento de puntero actualmente en este índice.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Si se pasa un valor negativo o `GetUpperBound` un valor mayor que el valor devuelto por, se producirá un error en la aserción.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::GetAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE GetAt( INT_PTR** `nIndex` **) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt( INT_PTR** `nIndex` **) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt( INT_PTR** `nIndex` **) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt( INT_PTR** `nIndex` **) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt( INT_PTR** `nIndex` **) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObArray::GetCount

Devuelve el número de elementos de matriz.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la matriz.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de elementos de la matriz. Dado que los índices se basan en cero, el tamaño es 1 mayor que el índice más grande.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::GetCount`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObArray::GetData

Utilice esta función miembro para obtener acceso directo a los elementos de la matriz.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a `CObject` la matriz de punteros.

### <a name="remarks"></a>Observaciones

Si no hay `GetData` elementos disponibles, devuelve un valor nulo.

Aunque el acceso directo a los elementos de una matriz `GetData`puede ayudarle a trabajar más rápidamente, tenga cuidado al llamar; los errores que comete afectan directamente a los elementos de la matriz.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::GetData`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const\* BYTE GetData( ) const; BYTE\* GetData( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD\* GetData( ) const;DWORD\* GetData( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const\* \* void GetData( ) const;void\* \* GetData( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* GetData( ) const; CString\* GetData( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT\* GetData( ) const; UINT\* GetData( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const\* WORD GetData( ) const; WORD\* GetData( );**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObArray::GetSize

Devuelve el tamaño de la matriz.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Observaciones

Dado que los índices se basan en cero, el tamaño es 1 mayor que el índice más grande.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::GetSize`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObArray::GetUpperBound

Devuelve el límite superior actual de esta matriz.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Valor devuelto

El índice del límite superior (basado en cero).

### <a name="remarks"></a>Observaciones

Dado que los índices de matriz se basan `GetSize`en cero, esta función devuelve un valor 1 menor que .

La `GetUpperBound( )` condición -1 indica que la matriz no contiene elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::GetUpperBound`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObArray::InsertAt

Inserta un elemento (o todos los elementos de otra matriz) en un índice especificado.

```cpp
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que puede ser `GetUpperBound`mayor que el valor devuelto por .

*newElement*<br/>
El `CObject` puntero que se colocará en esta matriz. Se permite *un newElement* de valor NULL.

*nCount*<br/>
El número de veces que se debe insertar este elemento (valor predeterminado es 1).

*nStartIndex*<br/>
Un índice entero que puede ser `GetUpperBound`mayor que el valor devuelto por .

*pNewArray*<br/>
Otra matriz que contiene elementos que se agregarán a esta matriz.

### <a name="remarks"></a>Observaciones

La primera `InsertAt` versión de inserta un elemento (o varias copias de un elemento) en un índice especificado en una matriz. En el proceso, desplaza hacia arriba (incrementando el índice) el elemento existente en este índice y desplaza hacia arriba todos los elementos por encima de él.

La segunda versión inserta todos `CObArray` los elementos de otra colección, comenzando en la posición *nStartIndex.*

La `SetAt` función, en cambio, reemplaza un elemento de matriz especificado y no desplaza ningún elemento.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::InsertAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, BYTE** `newElement` **, int** `nCount` **á 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` **1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` , **int** `nCount` **1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CStringArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, UINT** `newElement` , **int** `nCount` **1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CUIntArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Ejemplo

  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Los resultados de este programa son los siguientes:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObArray::IsEmpty

Determina si la matriz está vacía.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la matriz está vacía; de lo contrario 0.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray::operador [ ]

Estos operadores de subíndice `SetAt` sson un sustituto conveniente para las funciones. `GetAt`

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Observaciones

El primer operador, llamado para matrices que no son **const**, se puede utilizar en la derecha (valor r) o a la izquierda (valor l) de una instrucción de asignación. El segundo, llamado para **matrices const,** sólo se puede utilizar a la derecha.

La versión de depuración de la biblioteca afirma si el subíndice (ya sea en el lado izquierdo o derecho de una instrucción de asignación) está fuera de los límites.

En la tabla siguiente se `CObArray::operator []`muestran otros operadores similares a .

|Clase|Operator|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& operador [](int_ptr** `nindex` ** \);**<br /><br /> **Operador BYTE [](int_ptr** `nindex` ** \) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& operador [](int_ptr** `nindex` ** \);**<br /><br /> **Operador DWORD [](int_ptr** `nindex` ** \) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**operador\* de& vacío [](int_ptr** `nindex` ** \);**<br /><br /> **operador\* void [](int_ptr** `nindex` ** \) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString operador& [](int_ptr** `nindex` ** \);**<br /><br /> **Operador CString [](int_ptr** `nindex` ** \) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Operador de& UINT [](int_ptr** `nindex` ** \);**<br /><br /> **Operador UINT [](int_ptr** `nindex` ** \) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Operador de& WORD [](int_ptr** `nindex` ** \);**<br /><br /> **Operador WORD [](int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObArray::RemoveAll

Quita todos los punteros de esta matriz, `CObject` pero en realidad no elimina los objetos.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Si la matriz ya está vacía, la función sigue funcionando.

La `RemoveAll` función libera toda la memoria utilizada para el almacenamiento de punteros.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::RemoveAll`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObArray::RemoveAt

Quita uno o varios elementos a partir de un índice especificado en una matriz.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y `GetUpperBound`menor o igual que el valor devuelto por .

*nCount*<br/>
Número de elementos que se va a quitar.

### <a name="remarks"></a>Observaciones

En el proceso, desplaza hacia abajo todos los elementos por encima de los elementos eliminados. Disminuye el límite superior de la matriz, pero no libera memoria.

Si intenta quitar más elementos de los que se encuentran en la matriz por encima del punto de eliminación, la versión de depuración de la biblioteca afirma.

La `RemoveAt` función `CObject` quita el puntero de la matriz, pero no elimina el propio objeto.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::RemoveAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **1 );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** *nCount* **1 );**|

### <a name="example"></a>Ejemplo

  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Los resultados de este programa son los siguientes:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObArray::SetAt

Establece el elemento de matriz en el índice especificado.

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0 y `GetUpperBound`menor o igual que el valor devuelto por .

*newElement*<br/>
El puntero de objeto que se va a insertar en esta matriz. Se permite un valor NULL.

### <a name="remarks"></a>Observaciones

`SetAt`no hará que la matriz crezca. Utilícelo `SetAtGrow` si desea que la matriz crezca automáticamente.

Debe asegurarse de que el valor de índice representa una posición válida en la matriz. Si está fuera de los límites, la versión de depuración de la biblioteca afirma.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::SetAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt( INT_PTR** `nIndex` **, BYTE** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, UINT** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>Ejemplo

  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Los resultados de este programa son los siguientes:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObArray::SetAtGrow

Establece el elemento de matriz en el índice especificado.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Un índice entero que es mayor o igual que 0.

*newElement*<br/>
El puntero de objeto que se agregará a esta matriz. Se permite un valor NULL.

### <a name="remarks"></a>Observaciones

La matriz crece automáticamente si es necesario (es decir, el límite superior se ajusta para dar cabida al nuevo elemento).

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::SetAtGrow`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Ejemplo

  Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Los resultados de este programa son los siguientes:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObArray::SetSize

Establece el tamaño de una matriz vacía o existente; asigna memoria si es necesario.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parámetros

*nNewSize*<br/>
El nuevo tamaño de matriz (número de elementos). Debe ser mayor o igual que 0.

*nGrowBy*<br/>
El número mínimo de ranuras de elementos que se asignarán si es necesario un aumento de tamaño.

### <a name="remarks"></a>Observaciones

Si el nuevo tamaño es menor que el tamaño anterior, la matriz se trunca y se libera toda la memoria no utilizada. Para mayor eficiencia, llame `SetSize` para establecer el tamaño de la matriz antes de usarla. Esto evita la necesidad de reasignar y copiar la matriz cada vez que se agrega un elemento.

El parámetro *nGrowBy* afecta a la asignación de memoria interna mientras la matriz está creciendo. Su uso nunca afecta al `GetSize` `GetUpperBound`tamaño de la matriz según lo reportado por y .

Si el tamaño de la matriz ha crecido, todos los punteros **CObject** <strong>\*</strong> recién asignados se establecen en NULL.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CObArray::SetSize`.

|Clase|Función miembro|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` **-1 );**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CObArray::GetData](#getdata).

## <a name="see-also"></a>Vea también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CStringArray (clase)](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray (clase)](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray (clase)](../../mfc/reference/cbytearray-class.md)<br/>
[Clase CWordArray](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray (clase)](../../mfc/reference/cdwordarray-class.md)
