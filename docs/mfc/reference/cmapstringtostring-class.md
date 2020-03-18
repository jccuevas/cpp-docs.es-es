---
title: Clase CMapStringToString
ms.date: 11/04/2016
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToString::CMapStringToString
- AFXCOLL/CMapStringToString::GetCount
- AFXCOLL/CMapStringToString::GetHashTableSize
- AFXCOLL/CMapStringToString::GetNextAssoc
- AFXCOLL/CMapStringToString::GetSize
- AFXCOLL/CMapStringToString::GetStartPosition
- AFXCOLL/CMapStringToString::HashKey
- AFXCOLL/CMapStringToString::InitHashTable
- AFXCOLL/CMapStringToString::IsEmpty
- AFXCOLL/CMapStringToString::Lookup
- AFXCOLL/CMapStringToString::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToString::RemoveAll
- AFXCOLL/CMapStringToString::RemoveKey
- AFXCOLL/CMapStringToString::SetAt
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToString [MFC], CMapStringToString
- CMapStringToString [MFC], GetCount
- CMapStringToString [MFC], GetHashTableSize
- CMapStringToString [MFC], GetNextAssoc
- CMapStringToString [MFC], GetSize
- CMapStringToString [MFC], GetStartPosition
- CMapStringToString [MFC], HashKey
- CMapStringToString [MFC], InitHashTable
- CMapStringToString [MFC], IsEmpty
- CMapStringToString [MFC], Lookup
- CMapStringToString [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToString [MFC], RemoveAll
- CMapStringToString [MFC], RemoveKey
- CMapStringToString [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
ms.openlocfilehash: a2ffcf7ce7ee6eccc56382501a5969ddec6c9e22
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442592"
---
# <a name="cmapstringtostring-class"></a>Clase CMapStringToString

Admite mapas de objetos `CString` con clave de objetos `CString` .

## <a name="syntax"></a>Sintaxis

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Members

Las funciones miembro de `CMapStringToString` son similares a las funciones miembro de la clase [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para obtener información específica de la función miembro. Siempre que vea un puntero `CObject` como un valor devuelto o un parámetro de la función "Output", sustituya un puntero a **Char**. Siempre que vea un puntero `CObject` como un parámetro de función "Input", sustituya un puntero a **Char**.

`BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`

por ejemplo, se traduce en

`BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`

### <a name="public-structures"></a>Estructuras públicas

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToString::CPair](#cpair)|Estructura anidada que contiene un valor de clave y el valor del objeto de cadena asociado.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToString::CMapStringToString](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToString:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Devuelve el número de elementos de este mapa.|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtiene el siguiente elemento para recorrer en iteración.|
|[CMapStringToString:: obtiene](../../mfc/reference/cmapstringtoob-class.md#getsize)|Devuelve el número de elementos de este mapa.|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Devuelve la posición del primer elemento.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcula el valor hash de una clave especificada.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializa la tabla hash.|
|[CMapStringToString:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Comprueba la condición de asignación vacía (no hay elementos).|
|[CMapStringToString:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Busca un puntero void basado en la clave del puntero void. El valor de puntero, no la entidad a la que apunta, se usa para la comparación de claves.|
|[CMapStringToString:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Devuelve una referencia a la clave asociada al valor de clave especificado.|
|[CMapStringToString::P GetFirstAssoc](#pgetfirstassoc)|Obtiene un puntero al primer `CString` del mapa.|
|[CMapStringToString::P GetNextAssoc](#pgetnextassoc)|Obtiene un puntero al `CString` siguiente para la iteración.|
|[CMapStringToString::P búsqueda](#plookup)|Devuelve un puntero a una `CString` cuyo valor coincide con el valor especificado.|
|[CMapStringToString:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Quita todos los elementos de esta asignación.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Quita un elemento especificado por una clave.|
|[CMapStringToString:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToString:: Operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Inserta un elemento en la asignación: sustitución de operador para `SetAt`.|

## <a name="remarks"></a>Observaciones

`CMapStringToString` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Cada elemento se serializa a su vez si una asignación se almacena en un archivo, ya sea con el operador de inserción sobrecargado ( **<<** ) o con la función miembro `Serialize`.

Si necesita un volcado de `CString`individuales - elementos `CString`, debe establecer la profundidad del contexto de volcado en 1 o más.

Cuando se elimina un objeto de `CMapStringToString`, o cuando se quitan sus elementos, se quitan los objetos `CString` según corresponda.

Para obtener más información sobre `CMapStringToString`, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

##  <a name="cpair"></a>CMapStringToString::CPair

Contiene un valor de clave y el valor del objeto de cadena asociado.

### <a name="remarks"></a>Observaciones

Se trata de una estructura anidada dentro de la clase [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

La estructura se compone de dos campos:

- `key` el valor real del tipo de clave.

- `value` el valor del objeto asociado.

Se usa para almacenar los valores devueltos de [CMapStringToString::P lookup](#plookup), [CMapStringToString::P getfirstassoc](#pgetfirstassoc)y [CMapStringToString::P getnextassoc](#pgetnextassoc).

### <a name="example"></a>Ejemplo

  Para obtener un ejemplo de uso, vea el ejemplo de [CMapStringToString::P lookup](#plookup).

##  <a name="pgetfirstassoc"></a>CMapStringToString::P GetFirstAssoc

Devuelve la primera entrada del objeto de mapa.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la primera entrada del mapa; vea [CMapStringToString:: CPair](#cpair). Si el mapa está vacío, el valor es NULL.

### <a name="remarks"></a>Observaciones

Llame a esta función para devolver un puntero al primer elemento del objeto de mapa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

##  <a name="pgetnextassoc"></a>CMapStringToString::P GetNextAssoc

Recupera el elemento de mapa al que apunta *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parámetros

*pAssoc*<br/>
Apunta a una entrada de mapa devuelta por una llamada anterior a [PGetNextAssoc](#pgetnextassoc) o [PGetFirstAssoc](#pgetfirstassoc) .

### <a name="return-value"></a>Valor devuelto

Puntero a la entrada siguiente en el mapa; vea [CMapStringToString:: CPair](#cpair). Si el elemento es el último en el mapa, el valor es NULL.

### <a name="remarks"></a>Observaciones

Llame a este método para recorrer en iteración todos los elementos del mapa. Recupere el primer elemento con una llamada a `PGetFirstAssoc` y, a continuación, recorra en iteración el mapa con llamadas sucesivas a `PGetNextAssoc`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMapStringToString::P getfirstassoc](#pgetfirstassoc).

##  <a name="plookup"></a>CMapStringToString::P búsqueda

Busca el valor asignado a una clave determinada.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Puntero a la clave del elemento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Puntero a la clave especificada.

### <a name="remarks"></a>Observaciones

Llame a este método para buscar un elemento de mapa con una clave que coincida exactamente con la clave especificada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de recopilación de MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
