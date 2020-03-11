---
title: Clase CMapStringToOb
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
ms.openlocfilehash: b56e9052533269ba62d248312f07ac16db71bf4a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876379"
---
# <a name="cmapstringtoob-class"></a>Clase CMapStringToOb

Una clase de colección de diccionarios que asigna objetos `CString` únicos a punteros `CObject` .

## <a name="syntax"></a>Sintaxis

```
class CMapStringToOb : public CObject
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToOb:: GetCount](#getcount)|Devuelve el número de elementos de este mapa.|
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Obtiene el siguiente elemento para recorrer en iteración.|
|[CMapStringToOb:: obtiene](#getsize)|Devuelve el número de elementos de este mapa.|
|[CMapStringToOb::GetStartPosition](#getstartposition)|Devuelve la posición del primer elemento.|
|[CMapStringToOb::HashKey](#hashkey)|Calcula el valor hash de una clave especificada.|
|[CMapStringToOb::InitHashTable](#inithashtable)|Inicializa la tabla hash.|
|[CMapStringToOb:: IsEmpty](#isempty)|Comprueba la condición de asignación vacía (no hay elementos).|
|[CMapStringToOb:: Lookup](#lookup)|Busca un puntero void basado en la clave del puntero void. El valor de puntero, no la entidad a la que apunta, se usa para la comparación de claves.|
|[CMapStringToOb:: LookupKey](#lookupkey)|Devuelve una referencia a la clave asociada al valor de clave especificado.|
|[CMapStringToOb:: RemoveAll](#removeall)|Quita todos los elementos de esta asignación.|
|[CMapStringToOb::RemoveKey](#removekey)|Quita un elemento especificado por una clave.|
|[CMapStringToOb:: SetAt](#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToOb:: Operator \[ \]](#operator_at)|Inserta un elemento en la asignación: sustitución de operador para `SetAt`.|

## <a name="remarks"></a>Observaciones

Una vez que haya insertado un `CString`- `CObject*` par (elemento) en el mapa, puede recuperar o eliminar de forma eficaz el par mediante una cadena o un valor de `CString` como una clave. También puede recorrer en iteración todos los elementos del mapa.

Una variable de tipo POSITION se usa para el acceso de entrada alternativo en todas las variaciones de mapa. Puede usar una posición para "recordar" una entrada y recorrer en iteración el mapa. Podría pensar que esta iteración es secuencial por valor de clave; no lo es. La secuencia de elementos recuperados es indeterminada.

`CMapStringToOb` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Cada elemento se serializa a su vez si una asignación se almacena en un archivo, ya sea con el operador de inserción sobrecargado ( **<<** ) o con la función miembro `Serialize`.

Si necesita un volcado de diagnóstico de los elementos individuales de la asignación (el valor de `CString` y el contenido de `CObject`), debe establecer la profundidad del contexto de volcado en 1 o más.

Cuando se elimina un objeto de `CMapStringToOb`, o cuando se quitan sus elementos, se quitan los objetos `CString` y los punteros `CObject`. Los objetos a los que hacen referencia los punteros de `CObject` no se destruyen.

La derivación de clases de mapa es similar a la derivación de la lista. Vea las [colecciones](../../mfc/collections.md) de artículos para ver una ilustración de la derivación de una clase de lista de propósito especial.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToOb`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

##  <a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb

Construye un mapa de `CString`a `CObject*` vacío.

```
CMapStringToOb(INT_PTR nBlockSize = 10);
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Especifica la granularidad de asignación de memoria para extender la asignación.

### <a name="remarks"></a>Observaciones

A medida que crece el mapa, la memoria se asigna en unidades de entradas de *nBlockSize* .

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb:: CMapStringToOb`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#63](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de colección.

##  <a name="getcount"></a>CMapStringToOb:: GetCount

Determina el número de elementos que hay en el mapa.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de esta asignación.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetCount`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR GetCount () Const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR GetCount () Const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR GetCount () Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR GetCount () Const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR GetCount () Const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR GetCount () Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#64](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]

##  <a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize

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
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT GetHashTableSize () Const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT GetHashTableSize () Const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT GetHashTableSize () Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT GetHashTableSize () Const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT GetHashTableSize () Const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT GetHashTableSize () Const;**|

##  <a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc

Recupera el elemento de mapa en *rNextPosition*y, a continuación, actualiza *rNextPosition* para hacer referencia al siguiente elemento del mapa.

```
void GetNextAssoc(
    POSITION& rNextPosition,
    CString& rKey,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parámetros

*rNextPosition*<br/>
Especifica una referencia a un valor de posición devuelto por una llamada anterior `GetNextAssoc` o `GetStartPosition`.

*rKey*<br/>
Especifica la clave devuelta del elemento recuperado (una cadena).

*rValue*<br/>
Especifica el valor devuelto del elemento recuperado (un puntero `CObject`). Vea la sección Comentarios para obtener más información sobre este parámetro.

### <a name="remarks"></a>Observaciones

Esta función es muy útil para recorrer en iteración todos los elementos del mapa. Tenga en cuenta que la secuencia de posición no es necesariamente la misma que la secuencia de valor de clave.

Si el elemento recuperado es el último en el mapa, el nuevo valor de *rNextPosition* se establece en NULL.

En el caso del parámetro *rValue* , asegúrese de convertir el tipo de objeto a **CObject\*&** , que es lo que el compilador requiere, tal como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFCCollections#65](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]

Esto no es cierto en `GetNextAssoc` para las asignaciones basadas en plantillas.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetNextAssoc`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, void\*&** *rKey* **, void\*&** *rValue* **) Const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, void\*&** *rKey* **, Word &** *rValue* **) Const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, CString &** *rKey* **, void\*&** *rValue* **) Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, cstring &** *rKey* **, CString &** *rValue* **) Const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, WORD &** *rKey* **, CObject\*&** *rValue* **) Const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc (POSITION &** *rNextPosition* **, WORD &** *rKey* **, void\*&** *rValue* **) Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#66](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]

Los resultados de este programa son los siguientes:

```Output
Lisa : a CAge at $4724 11
Marge : a CAge at $47A8 35
Homer : a CAge at $4766 36
Bart : a CAge at $45D4 13
```

##  <a name="getsize"></a>CMapStringToOb:: obtiene

Devuelve el número de elementos de mapa.

```
INT_PTR GetSize() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del mapa.

### <a name="remarks"></a>Observaciones

Llame a este método para recuperar el número de elementos del mapa.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetSize`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**INT_PTR se obtiene () Const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**INT_PTR se obtiene () Const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**INT_PTR se obtiene () Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**INT_PTR se obtiene () Const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**INT_PTR se obtiene () Const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**INT_PTR se obtiene () Const;**|

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#67](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]

##  <a name="getstartposition"></a>CMapStringToOb::GetStartPosition

Inicia una iteración de mapa devolviendo un valor de posición que se puede pasar a una llamada `GetNextAssoc`.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de posición que indica una posición inicial para recorrer en iteración el mapa; o NULL si la asignación está vacía.

### <a name="remarks"></a>Observaciones

La secuencia de iteración no es predecible; por lo tanto, el "primer elemento del mapa" no tiene una importancia especial.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::GetStartPosition`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSITION GetStartPosition () Const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSITION GetStartPosition () Const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSITION GetStartPosition () Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSITION GetStartPosition () Const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSITION GetStartPosition () Const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSITION GetStartPosition () Const;**|

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CMapStringToOb:: GetNextAssoc](#getnextassoc).

##  <a name="hashkey"></a>CMapStringToOb::HashKey

Calcula el valor hash de una clave especificada.

```
UINT HashKey(LPCTSTR key) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave cuyo valor hash se va a calcular.

### <a name="return-value"></a>Valor devuelto

Valor hash de la clave.

### <a name="remarks"></a>Observaciones

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::HashKey`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Uint HashKey (void** <strong>\*</strong> `key` **) Const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Uint HashKey (void** <strong>\*</strong> `key` **) Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Uint HashKey (LPCTSTR** `key` **) Const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Uint HashKey (LPCTSTR** `key` **) Const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Uint HashKey (WORD** `key` **) Const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Uint HashKey (WORD** `key` **) Const;**|

##  <a name="inithashtable"></a>CMapStringToOb::InitHashTable

Inicializa la tabla hash.

```
void InitHashTable(
    UINT hashSize,
    BOOL bAllocNow = TRUE);
```

### <a name="parameters"></a>Parámetros

*hashSize*<br/>
Número de entradas de la tabla hash.

*bAllocNow*<br/>
Si es TRUE, asigna la tabla hash al inicializarse; de lo contrario, se asignará la tabla cuando sea necesario.

### <a name="remarks"></a>Observaciones

Para obtener el mejor rendimiento, el tamaño de la tabla hash debe ser un número primo. Para minimizar las colisiones, el tamaño debe ser aproximadamente un 20 por ciento mayor que el conjunto de datos previsto más grande.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::InitHashTable`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, bool** `bAllocNow` **= true);**|

##  <a name="isempty"></a>CMapStringToOb:: IsEmpty

Determina si la asignación está vacía.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si esta asignación no contiene elementos; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [RemoveAll](#removeall).

### <a name="remarks"></a>Observaciones

En la tabla siguiente se muestran otras funciones miembro que son similares a **CMapStringToOb:: IsEmpty**.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL IsEmpty () Const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL IsEmpty () Const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL IsEmpty () Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL IsEmpty () Const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL IsEmpty () Const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL IsEmpty () Const;**|

##  <a name="lookup"></a>CMapStringToOb:: Lookup

Devuelve un puntero de `CObject` basado en un valor de `CString`.

```
BOOL Lookup(
    LPCTSTR key,
    CObject*& rValue) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la clave de cadena que identifica el elemento que se va a buscar.

*rValue*<br/>
Especifica el valor devuelto del elemento buscado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró el elemento; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

`Lookup` usa un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincida exactamente (valor `CString`).

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::LookUp`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Bool Lookup (void** <strong>\*</strong> `key` **, void\*&** `rValue` **) Const;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Bool Lookup (void** <strong>\*</strong> `key` **, Word &** `rValue` **) Const;**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool Lookup (LPCTSTR** `key` **, void\*&** `rValue` **) Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Bool Lookup (LPCTSTR** `key` **, CString &** `rValue` **) Const;**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|La **búsqueda de bool (WORD** `key` **, CObject\*&** `rValue` **) Const;**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Bool Lookup (WORD** `key` **, void\*&** `rValue` **) Const;**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#68](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]

##  <a name="lookupkey"></a>CMapStringToOb:: LookupKey

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
Referencia a la clave asociada.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la clave; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El uso de una referencia a una clave no es seguro si se utiliza después de quitar el elemento asociado de la asignación o después de que se destruye el mapa.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb:: LookupKey`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool LookupKey (lpctstr** `key` **, LPCTSTR &** `rKey` **) Const;**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Bool LookupKey (lpctstr** `key` **, LPCTSTR &** `rKey` **) Const;**|

##  <a name="operator_at"></a>CMapStringToOb:: Operator []

Un sustituto adecuado para la función miembro `SetAt`.

```
CObject*& operator[ ](lpctstr key);
```

### <a name="return-value"></a>Valor devuelto

Referencia a un puntero a un objeto `CObject`; o NULL si la asignación está vacía o la *clave* está fuera del intervalo.

### <a name="remarks"></a>Observaciones

Por lo tanto, solo se puede usar en el lado izquierdo de una instrucción de asignación (un valor l). Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento.

No hay ningún "lado derecho" (valor r) equivalente a este operador porque existe la posibilidad de que una clave no se encuentre en el mapa. Utilice la función miembro `Lookup` para la recuperación de elementos.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::operator []`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|<strong>void\*& operador\[] (void \*</strong> `key`\) **;**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Operador de & de WORD\[] (void** <strong>\*</strong> `key` **\);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& operador\[] (lpctstr** `key` **\);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString & operador\[] (lpctstr** `key` **\);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& operador\[] (word** `key` **\);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& operador\[] (word** `key` **\);**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#72](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]

Los resultados de este programa son los siguientes:

```Output
Operator [] example: A CMapStringToOb with 2 elements
[Lisa] = a CAge at $4A02 11
[Bart] = a CAge at $497E 13
```

##  <a name="removeall"></a>CMapStringToOb:: RemoveAll

Quita todos los elementos de esta asignación y destruye los objetos de clave `CString`dos.

```
void RemoveAll();
```

### <a name="remarks"></a>Observaciones

Los objetos `CObject` a los que hace referencia cada clave no se destruyen. La función `RemoveAll` puede producir fugas de memoria si no se asegura de que los objetos de `CObject` a los que se hace referencia se destruyan.

La función funciona correctamente si la asignación ya está vacía.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::RemoveAll`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll ();**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll ();**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll ();**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll ();**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll ();**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#69](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]

##  <a name="removekey"></a>CMapStringToOb::RemoveKey

Busca la entrada de mapa correspondiente a la clave proporcionada; a continuación, si se encuentra la clave, quita la entrada.

```
BOOL RemoveKey(LPCTSTR key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la cadena que se usa para la búsqueda de asignaciones.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la entrada se ha encontrado y se ha quitado correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esto puede producir pérdidas de memoria si el objeto de `CObject` no se elimina en otro lugar.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::RemoveKey`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**Bool removeKey (void** <strong>\*</strong> `key` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**Bool removeKey (void** <strong>\*</strong> `key` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**Bool removeKey (LPCTSTR** `key` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Bool removeKey (LPCTSTR** `key` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**Bool removeKey (WORD** `key` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**Bool removeKey (WORD** `key` **);**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de colección.

[!code-cpp[NVC_MFCCollections#70](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]

Los resultados de este programa son los siguientes:

```Output
RemoveKey example: A CMapStringToOb with 3 elements
[Marge] = a CAge at $49A0 35
[Homer] = a CAge at $495E 36
[Bart] = a CAge at $4634 13
```

##  <a name="setat"></a>CMapStringToOb:: SetAt

La principal significa insertar un elemento en un mapa.

```
void SetAt(
    LPCTSTR key,
    CObject* newValue);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Especifica la cadena que es la clave del nuevo elemento.

*newValue*<br/>
Especifica el puntero `CObject` que es el valor del nuevo elemento.

### <a name="remarks"></a>Observaciones

En primer lugar, se busca la clave. Si se encuentra la clave, se cambia el valor correspondiente; en caso contrario, se crea un nuevo elemento de clave-valor.

En la tabla siguiente se muestran otras funciones miembro que son similares a `CMapStringToOb::SetAt`.

|Clase|Función miembro|
|-----------|---------------------|
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt (void** <strong>\*</strong> `key` **, Word** `newValue` **);**|
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt (LPCTSTR** `key` **, void** <strong>\*</strong> `newValue` **);**|
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt (lpctstr** `key` **, LPCTSTR** `newValue` **);**|
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt (WORD** `key` **, CObject** <strong>\*</strong> `newValue` **);**|
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt (WORD** `key` **, void** <strong>\*</strong> `newValue` **);**|

### <a name="example"></a>Ejemplo

Vea [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) para obtener una lista de la clase `CAge` utilizada en todos los ejemplos de colección.

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

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr (clase)](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord (clase)](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapStringToPtr (clase)](../../mfc/reference/cmapstringtoptr-class.md)<br/>
[CMapStringToString (clase)](../../mfc/reference/cmapstringtostring-class.md)<br/>
[CMapWordToOb (clase)](../../mfc/reference/cmapwordtoob-class.md)<br/>
[CMapWordToPtr (clase)](../../mfc/reference/cmapwordtoptr-class.md)
