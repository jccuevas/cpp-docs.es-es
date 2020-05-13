---
title: CMapStringToString (clase)
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
ms.openlocfilehash: 544154569c50369b805ba296aa975849f245d4ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370118"
---
# <a name="cmapstringtostring-class"></a>CMapStringToString (clase)

Admite mapas de objetos `CString` con clave de objetos `CString` .

## <a name="syntax"></a>Sintaxis

```
class CMapStringToString : public CObject
```

## <a name="members"></a>Miembros

Las funciones `CMapStringToString` miembro de son similares a las funciones miembro de la clase [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para obtener información específica de la función miembro. Dondequiera que `CObject` vea un puntero como un valor devuelto o un parámetro de función "salida", sustituya un puntero a **char**. Dondequiera que `CObject` vea un puntero como un parámetro de función "entrada", sustituya un puntero a **char**.

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
|[CMapStringToString::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Devuelve el número de elementos de este mapa.|
|[CMapStringToString::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|
|[CMapStringToString::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtiene el siguiente elemento para iterar.|
|[CMapStringToString::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|Devuelve el número de elementos de este mapa.|
|[CMapStringToString::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Devuelve la posición del primer elemento.|
|[CMapStringToString::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcula el valor hash de una clave especificada.|
|[CMapStringToString::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializa la tabla hash.|
|[CMapStringToString::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Comprueba la condición de mapa vacío (sin elementos).|
|[CMapStringToString::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Busca un puntero void basado en la clave del puntero void. El valor del puntero, no la entidad a la que apunta, se utiliza para la comparación de claves.|
|[CMapStringToString::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Devuelve una referencia a la clave asociada al valor de clave especificado.|
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|Obtiene un puntero al `CString` primero del mapa.|
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|Obtiene un puntero al `CString` siguiente para iterar.|
|[CMapStringToString::PLookup](#plookup)|Devuelve un puntero `CString` a un cuyo valor coincide con el valor especificado.|
|[CMapStringToString::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Elimina todos los elementos de este mapa.|
|[CMapStringToString::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Quita un elemento especificado por una clave.|
|[CMapStringToString::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToString::operator \[\]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Inserta un elemento en el mapa `SetAt`— sustitución del operador para .|

## <a name="remarks"></a>Observaciones

`CMapStringToString` incorpora la macro `IMPLEMENT_SERIAL` para admitir la serialización y el volcado de sus elementos. Cada elemento se serializa a su vez si se almacena un mapa **<<** en un `Serialize` archivo, ya sea con el operador de inserción sobrecargado ( ) o con la función miembro.

Si necesita un volcado `CString` -  `CString` de elementos individuales, debe establecer la profundidad del contexto de volcado en 1 o superior.

Cuando `CMapStringToString` se elimina un objeto, o cuando `CString` se quitan sus elementos, los objetos se quitan según corresponda.

Para obtener `CMapStringToString`más información sobre , vea el artículo [Colecciones](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToString`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll.h

## <a name="cmapstringtostringcpair"></a><a name="cpair"></a>CMapStringToString::CPair

Contiene un valor de clave y el valor del objeto de cadena asociado.

### <a name="remarks"></a>Observaciones

Se trata de una estructura anidada dentro de la clase [CMapStringToString](../../mfc/reference/cmapstringtostring-class.md).

La estructura se compone de dos campos:

- `key`El valor real del tipo de clave.

- `value`El valor del objeto asociado.

Se utiliza para almacenar los valores devueltos de [CMapStringToString::PLookup](#plookup), [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)y [CMapStringToString::PGetNextAssoc](#pgetnextassoc).

### <a name="example"></a>Ejemplo

  Para obtener un ejemplo de uso, vea el ejemplo de [CMapStringToString::PLookup](#plookup).

## <a name="cmapstringtostringpgetfirstassoc"></a><a name="pgetfirstassoc"></a>CMapStringToString::PGetFirstAssoc

Devuelve la primera entrada del objeto de mapa.

```
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la primera entrada del mapa; vea [CMapStringToString::CPair](#cpair). Si el mapa está vacío, el valor es NULL.

### <a name="remarks"></a>Observaciones

Llame a esta función para devolver un puntero el primer elemento en el objeto de mapa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]

## <a name="cmapstringtostringpgetnextassoc"></a><a name="pgetnextassoc"></a>CMapStringToString::PGetNextAssoc

Recupera el elemento de mapa al que apunta *pAssocRec*.

```
const CPair *PGetNextAssoc(const CPair* pAssoc) const;

CPair *PGetNextAssoc(const CPair* pAssoc);
```

### <a name="parameters"></a>Parámetros

*pAssoc*<br/>
Apunta a una entrada de mapa devuelta por una llamada [PGetNextAssoc](#pgetnextassoc) o [PGetFirstAssoc](#pgetfirstassoc) anterior.

### <a name="return-value"></a>Valor devuelto

Un puntero a la siguiente entrada en el mapa; vea [CMapStringToString::CPair](#cpair). Si el elemento es el último del mapa, el valor es NULL.

### <a name="remarks"></a>Observaciones

Llame a este método para recorrer en iteración todos los elementos del mapa. Recupere el primer elemento `PGetFirstAssoc` con una llamada y, a `PGetNextAssoc`continuación, iterar a través del mapa con llamadas sucesivas a .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc).

## <a name="cmapstringtostringplookup"></a><a name="plookup"></a>CMapStringToString::PLookup

Busca el valor asignado a una clave determinada.

```
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Un puntero a la clave para el elemento que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un puntero a la clave especificada.

### <a name="remarks"></a>Observaciones

Llame a este método para buscar un elemento de mapa con una clave que coincida exactamente con la clave dada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]

## <a name="see-also"></a>Consulte también

[RECOPILACIÓN de muestras de MFC](../../overview/visual-cpp-samples.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
