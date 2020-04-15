---
title: CMapStringToOb (clase)
ms.date: 11/04/2016
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
helpviewer_keywords:
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
ms.openlocfilehash: 12de7bd72f643f08cebf948634703172d6725ce6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370103"
---
# <a name="cmapstringtoob-class"></a>CMapStringToOb (clase)

Una clase de colección de diccionarios que asigna objetos `CString` únicos a punteros `CObject` .

## <a name="syntax"></a>Sintaxis

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToOb::GetCount](#getcount)|Devuelve el número de elementos de este mapa.|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Obtiene el siguiente elemento para iterar.|
|[CMapStringToOb::GetSize](#getsize)|Devuelve el número de elementos de este mapa.|
|[CMapStringToOb::GetStartPosition](#getstartposition)|Devuelve la posición del primer elemento.|
|[CMapStringToOb::HashKey](#hashkey)|Calcula el valor hash de una clave especificada.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicializa la tabla hash.|
|[CMapStringToOb::IsEmpty](#isempty)|Comprueba la condición de mapa vacío (sin elementos).|
|[CMapStringToOb::Lookup](#lookup)|Busca un puntero void basado en la clave del puntero void. El valor del puntero, no la entidad a la que apunta, se utiliza para la comparación de claves.|
|[CMapStringToOb::LookupKey](#lookupkey)|Devuelve una referencia a la clave asociada al valor de clave especificado.|
|[CMapStringToOb::RemoveAll](#removeall)|Elimina todos los elementos de este mapa.|
|[CMapStringToOb::RemoveKey](#removekey)|Quita un elemento especificado por una clave.|
|[CMapStringToOb::SetAt](#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToOb::operator \[\]](#operator_at)|Inserta un elemento en el mapa `SetAt`— sustitución del operador para .|

## <a name="remarks"></a>Observaciones

Una vez que `CString` -  `CObject*` haya insertado un par (elemento) en el mapa, puede `CString` recuperar o eliminar el par de forma eficaz utilizando una cadena o un valor como clave. También puede iterar sobre todos los elementos del mapa.

Una variable de tipo POSITION se utiliza para el acceso de entrada alternativo en todas las variaciones de mapa. Puede utilizar una POSITION para "recordar" una entrada y recorrer en iteración el mapa. Podría pensar que esta iteración es secuencial por valor de clave; no lo es. La secuencia de elementos recuperados es indeterminada.

`CMapStringToOb` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Cada elemento se serializa a su vez si se almacena un mapa **<<** en un `Serialize` archivo, ya sea con el operador de inserción sobrecargado ( ) o con la función miembro.

Si necesita un volcado de diagnóstico de los `CString` elementos `CObject` individuales del mapa (el valor y el contenido), debe establecer la profundidad del contexto de volcado en 1 o superior.

Cuando `CMapStringToOb` se elimina un objeto, o cuando `CString` se `CObject` quitan sus elementos, se quitan los objetos y los punteros. Los objetos `CObject` a los que hacen referencia los punteros no se destruyen.

La derivación de la clase de mapa es similar a la derivación de lista. Consulte el artículo [Colecciones](../../mfc/collections.md) para obtener una ilustración de la derivación de una clase de lista de propósito especial.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll.h

## <a name="cmapstringtoobcmapstringtoob"></a><a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb

Construye un `CString` `CObject*` mapa vacío a.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Especifica la granularidad de asignación de memoria para extender el mapa.

### <a name="remarks"></a>Observaciones

A medida que el mapa crece, la memoria se asigna en unidades de entradas *nBlockSize.*

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb:: CMapStringToOb`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr( INT_PTR** `nBlockSize` **a 10 );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord( INT_PTR** `nBlockSize` **á 10 );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr( INT_PTR** `nBlockSize` **a 10 );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString( INT_PTR** `nBlockSize` **á 10 );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb( INT_PTR** `nBlockSize` **a 10 );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr( INT_PTR** `nBlockSize` **a 10 );**|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

## <a name="cmapstringtoobgetcount"></a><a name="getcount"></a>CMapStringToOb::GetCount

Determina cuántos elementos hay en el mapa.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos de este mapa.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetCount`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

## <a name="cmapstringtoobgethashtablesize"></a><a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize

Determina el número actual de elementos de la tabla hash.

```
UINT GetHashTableSize() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de elementos de la tabla hash.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetHashTableSize`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize( ) const;**|

## <a name="cmapstringtoobgetnextassoc"></a><a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc

Recupera el elemento de mapa en *rNextPosition*y, a continuación, actualiza *rNextPosition* para hacer referencia al siguiente elemento del mapa.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parámetros

*rNextPosition*<br/>
Especifica una referencia a un valor `GetNextAssoc` POSITION `GetStartPosition` devuelto por una llamada o anterior.

*rKey*<br/>
Especifica la clave devuelta del elemento recuperado (una cadena).

*rValue*<br/>
Especifica el valor devuelto del elemento `CObject` recuperado (un puntero). Consulte Comentarios para obtener más información sobre este parámetro.

### <a name="remarks"></a>Observaciones

Esta función es más útil para recorrer en iteración todos los elementos del mapa. Tenga en cuenta que la secuencia de posición no es necesariamente la misma que la secuencia de valores de clave.

Si el elemento recuperado es el último del mapa, el nuevo valor de *rNextPosition* se establece en NULL.

Para el parámetro *rValue,* asegúrese de convertir el tipo de objeto a **\*CObject**, que es lo que requiere el compilador, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

Esto no es `GetNextAssoc` cierto para los mapas basados en plantillas.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetNextAssoc`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\* ** *rKey* **, void\* ** *rValue* **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\* ** *rKey* **, WORD&** *rValue* **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, void\* ** *rValue* **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, CString&** *rKey* **, CString&** *rValue* **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, CObject\* ** *rValue* **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, void\* ** *rValue* **) const;**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Los resultados de este programa son los siguientes:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

## <a name="cmapstringtoobgetsize"></a><a name="getsize"></a>CMapStringToOb::GetSize

Devuelve el número de elementos de mapa.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos en el mapa.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de elementos en el mapa.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetSize`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetSize( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

## <a name="cmapstringtoobgetstartposition"></a><a name="getstartposition"></a>CMapStringToOb::GetStartPosition

Inicia una iteración de mapa devolviendo `GetNextAssoc` un valor POSITION que se puede pasar a una llamada.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que indica una posición inicial para iterar el mapa; null si el mapa está vacío.

### <a name="remarks"></a>Observaciones

La secuencia de iteración no es predecible; por lo tanto, el "primer elemento en el mapa" no tiene un significado especial.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetStartPosition`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition( ) const;**|

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMapStringToOb::GetNextAssoc](#getnextassoc).

## <a name="cmapstringtoobhashkey"></a><a name="hashkey"></a>CMapStringToOb::HashKey

Calcula el valor hash de una clave especificada.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
La clave cuyo valor hash se va a calcular.

### <a name="return-value"></a>Valor devuelto

El valor hash de la clave

### <a name="remarks"></a>Observaciones

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::HashKey`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey( void** <strong>\*</strong> `key` **) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey( void** <strong>\*</strong> `key` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey( LPCTSTR** `key` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT HashKey( WORD** `key` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT HashKey( WORD** `key` **) const;**|

## <a name="cmapstringtoobinithashtable"></a><a name="inithashtable"></a>CMapStringToOb::InitHashTable

Inicializa la tabla hash.

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Parámetros

*hashSize*<br/>
Número de entradas en la tabla hash.

*bAllocNow*<br/>
Si TRUE, asigna la tabla hash tras la inicialización; de lo contrario, la tabla se asigna cuando es necesario.

### <a name="remarks"></a>Observaciones

Para obtener el mejor rendimiento, el tamaño de la tabla hash debe ser un número primo. Para minimizar las colisiones, el tamaño debe ser aproximadamente un 20 por ciento mayor que el conjunto de datos previsto más grande.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::InitHashTable`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable( UINT** `hashSize` **, BOOL** `bAllocNow` **- TRUE );**|

## <a name="cmapstringtoobisempty"></a><a name="isempty"></a>CMapStringToOb::IsEmpty

Determina si el mapa está vacío.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si este mapa no contiene elementos; de lo contrario 0.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [RemoveAll](#removeall).

### <a name="remarks"></a>Observaciones

En la tabla siguiente se muestran otras funciones miembro que son similares a **CMapStringToOb:: IsEmpty**.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty( ) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty( ) const;**|

## <a name="cmapstringtooblookup"></a><a name="lookup"></a>CMapStringToOb::Lookup

Devuelve `CObject` un puntero `CString` basado en un valor.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave de cadena que identifica el elemento que se va a buscar.

*rValue*<br/>
Especifica el valor devuelto desde el elemento buscado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró el elemento; de lo contrario 0.

### <a name="remarks"></a>Observaciones

`Lookup`utiliza un algoritmo hash para encontrar rápidamente el elemento `CString` de mapa con una clave que coincida exactamente (valor).

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::LookUp`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Lookup( void** <strong>\*</strong> `key` **, void\* ** `rValue` ) **const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Lookup( void** <strong>\*</strong> `key` **, WORD&** `rValue` **) const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup( LPCTSTR** `key` **, void\* ** `rValue` ) **const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL Lookup( LPCTSTR** `key` **, CString&** `rValue` **) const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup( WORD** `key` **\* , CObject** `rValue` **) const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup( WORD** `key` **, void\* ** `rValue` ) **const;**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

## <a name="cmapstringtooblookupkey"></a><a name="lookupkey"></a>CMapStringToOb::LookupKey

Devuelve una referencia a la clave asociada al valor de clave especificado.

```
BOOL LookupKey(
    LPCTSTR key,
    LPCTSTR& rKey) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave de cadena que identifica el elemento que se va a buscar.

*rKey*<br/>
La referencia a la clave asociada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la clave; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El uso de una referencia a una clave no es seguro si se utiliza después de que el elemento asociado se haya quitado del mapa o después de que se haya destruido el mapa.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb:: LookupKey`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey( LPCTSTR** `key` **, LPCTSTR&** `rKey` **) const;**|

## <a name="cmapstringtooboperator--"></a><a name="operator_at"></a>CMapStringToOb::operator [ ]

Un sustituto conveniente `SetAt` para la función miembro.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Valor devuelto

Una referencia a un `CObject` puntero a un objeto; o NULL si el mapa está vacío o la *clave* está fuera del rango.

### <a name="remarks"></a>Observaciones

Por lo tanto, solo se puede utilizar en el lado izquierdo de una instrucción de asignación (un valor l). Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento.

No hay ningún "lado derecho" (valor r) equivalente a este operador porque existe la posibilidad de que no se encuentre una clave en el mapa. Utilice `Lookup` la función miembro para la recuperación de elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::operator []`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>vacío\*&\[operador \* ](void</strong> `key` ** \);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Operador WORD\[& ](void** <strong>\*</strong> `key` ** \);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**vacío\*&\[operador ](lpctstr** `key` ** \);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString operador\[& ](lpctstr** `key` ** \);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*&\[operador ](palabra** `key` ** \);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**vacío\*&\[operador ](palabra** `key` ** \);**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Los resultados de este programa son los siguientes:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

## <a name="cmapstringtoobremoveall"></a><a name="removeall"></a>CMapStringToOb::RemoveAll

Elimina todos los elementos de este `CString` mapa y destruye los objetos clave.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Los `CObject` objetos a los que hace referencia cada clave no se destruyen. La `RemoveAll` función puede provocar pérdidas de memoria `CObject` si no se asegura de que se destruyen los objetos a los que se hace referencia.

La función funciona correctamente si el mapa ya está vacío.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::RemoveAll`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll( );**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll( );**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll( );**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll( );**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll( );**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

## <a name="cmapstringtoobremovekey"></a><a name="removekey"></a>CMapStringToOb::RemoveKey

Busca la entrada de mapa correspondiente a la clave suministrada; entonces, si se encuentra la clave, quita la entrada.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la cadena utilizada para la búsqueda de mapas.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la entrada se encontró y se quitó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esto puede provocar pérdidas `CObject` de memoria si el objeto no se elimina en otro lugar.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::RemoveKey`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey( void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey( LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey( LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey( WORD** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey( WORD** `key` **);**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Los resultados de este programa son los siguientes:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

## <a name="cmapstringtoobsetat"></a><a name="setat"></a>CMapStringToOb::SetAt

El principal significa insertar un elemento en un mapa.

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la cadena que es la clave del nuevo elemento.

*newValue*<br/>
Especifica el `CObject` puntero que es el valor del nuevo elemento.

### <a name="remarks"></a>Observaciones

Primero, la llave se mira hacia arriba. Si se encuentra la clave, se cambia el valor correspondiente; de lo contrario se crea un nuevo elemento clave-valor.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::SetAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt( void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt( void** <strong>\*</strong> `key` **, WORD** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt( LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt( WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt( WORD** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Ejemplo

Vea [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) para obtener `CAge` una lista de la clase utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#71](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]

Los resultados de este programa son los siguientes:

```Output
before Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $493C 11
[Bart] = a CAge at $4654 13
after Lisa's birthday: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $49C0 12
[Bart] = a CAge at $4654 13
```

## <a name="see-also"></a>Consulte también

[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr (clase)](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[Clase CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)<br/>
[Clase CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString (clase)](../../mfc/reference/cmapstringtostring-class.md)<br/>
[Clase CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)<br/>
[Clase CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)
