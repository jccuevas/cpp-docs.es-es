---
title: Clase CMapStringToPtr
ms.date: 11/04/2016
f1_keywords:
- CMapStringToPtr
- AFXCOLL/CMapStringToPtr
- AFXCOLL/CMapStringToPtr::CMapStringToPtr
- AFXCOLL/CMapStringToPtr::GetCount
- AFXCOLL/CMapStringToPtr::GetHashTableSize
- AFXCOLL/CMapStringToPtr::GetNextAssoc
- AFXCOLL/CMapStringToPtr::GetSize
- AFXCOLL/CMapStringToPtr::GetStartPosition
- AFXCOLL/CMapStringToPtr::HashKey
- AFXCOLL/CMapStringToPtr::InitHashTable
- AFXCOLL/CMapStringToPtr::IsEmpty
- AFXCOLL/CMapStringToPtr::Lookup
- AFXCOLL/CMapStringToPtr::LookupKey
- AFXCOLL/CMapStringToPtr::RemoveAll
- AFXCOLL/CMapStringToPtr::RemoveKey
- AFXCOLL/CMapStringToPtr::SetAt
helpviewer_keywords:
- CMapStringToPtr [MFC], CMapStringToPtr
- CMapStringToPtr [MFC], GetCount
- CMapStringToPtr [MFC], GetHashTableSize
- CMapStringToPtr [MFC], GetNextAssoc
- CMapStringToPtr [MFC], GetSize
- CMapStringToPtr [MFC], GetStartPosition
- CMapStringToPtr [MFC], HashKey
- CMapStringToPtr [MFC], InitHashTable
- CMapStringToPtr [MFC], IsEmpty
- CMapStringToPtr [MFC], Lookup
- CMapStringToPtr [MFC], LookupKey
- CMapStringToPtr [MFC], RemoveAll
- CMapStringToPtr [MFC], RemoveKey
- CMapStringToPtr [MFC], SetAt
ms.assetid: 1ac11143-eb0a-4511-a662-2df0d1d9005b
ms.openlocfilehash: 0e722b305dad6595eb67b1a235c375d21f674353
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442603"
---
# <a name="cmapstringtoptr-class"></a>Clase CMapStringToPtr

Admite mapas de punteros void con clave de objetos `CString` .

## <a name="syntax"></a>Sintaxis

```
class CMapStringToPtr : public CObject
```

## <a name="members"></a>Members

Las funciones miembro de `CMapStringToPtr` son similares a las funciones miembro de la clase [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para obtener información específica de la función miembro. Siempre que vea un puntero `CObject` como un parámetro de función o un valor devuelto, sustituya un puntero a **void**.

`BOOL CMapStringToPtr::Lookup( LPCTSTR <key>, void*& <rValue> ) const;`

por ejemplo, se traduce en

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToPtr::CMapStringToPtr](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToPtr:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Devuelve el número de elementos de este mapa.|
|[CMapStringToPtr::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|
|[CMapStringToPtr::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtiene el siguiente elemento para recorrer en iteración.|
|[CMapStringToPtr:: obtiene](../../mfc/reference/cmapstringtoob-class.md#getsize)|Devuelve el número de elementos de este mapa.|
|[CMapStringToPtr::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Devuelve la posición del primer elemento.|
|[CMapStringToPtr::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcula el valor hash de una clave especificada.|
|[CMapStringToPtr::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializa la tabla hash.|
|[CMapStringToPtr:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Comprueba la condición de asignación vacía (no hay elementos).|
|[CMapStringToPtr:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Busca un puntero void basado en la clave del puntero void. El valor de puntero, no la entidad a la que apunta, se usa para la comparación de claves.|
|[CMapStringToPtr:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Devuelve una referencia a la clave asociada al valor de clave especificado.|
|[CMapStringToPtr:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Quita todos los elementos de esta asignación.|
|[CMapStringToPtr::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Quita un elemento especificado por una clave.|
|[CMapStringToPtr:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapStringToPtr:: Operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Inserta un elemento en la asignación: sustitución de operador para `SetAt`.|

## <a name="remarks"></a>Observaciones

`CMapStringToPtr` incorpora la macro IMPLEMENT_DYNAMIC para admitir el acceso de tipo en tiempo de ejecución y el volcado a un objeto `CDumpContext`. Si necesita un volcado de elementos de mapa individuales, debe establecer la profundidad del contexto de volcado en 1 o más.

No se pueden serializar los mapas de cadena a puntero.

Cuando se elimina un objeto de `CMapStringToPtr`, o cuando se quitan sus elementos, se quitan los objetos de clave `CString` y las palabras.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMapStringToPtr`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
