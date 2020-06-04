---
title: Clase CMapPtrToWord
ms.date: 11/04/2016
f1_keywords:
- CMapPtrToWord
- AFXCOLL/CMapPtrToWord
- AFXCOLL/CMapPtrToWord::CMapPtrToWord
- AFXCOLL/CMapPtrToWord::GetCount
- AFXCOLL/CMapPtrToWord::GetHashTableSize
- AFXCOLL/CMapPtrToWord::GetNextAssoc
- AFXCOLL/CMapPtrToWord::GetSize
- AFXCOLL/CMapPtrToWord::GetStartPosition
- AFXCOLL/CMapPtrToWord::HashKey
- AFXCOLL/CMapPtrToWord::InitHashTable
- AFXCOLL/CMapPtrToWord::IsEmpty
- AFXCOLL/CMapPtrToWord::Lookup
- AFXCOLL/CMapPtrToWord::LookupKey
- AFXCOLL/CMapPtrToWord::RemoveAll
- AFXCOLL/CMapPtrToWord::RemoveKey
- AFXCOLL/CMapPtrToWord::SetAt
helpviewer_keywords:
- CMapPtrToWord [MFC], CMapPtrToWord
- CMapPtrToWord [MFC], GetCount
- CMapPtrToWord [MFC], GetHashTableSize
- CMapPtrToWord [MFC], GetNextAssoc
- CMapPtrToWord [MFC], GetSize
- CMapPtrToWord [MFC], GetStartPosition
- CMapPtrToWord [MFC], HashKey
- CMapPtrToWord [MFC], InitHashTable
- CMapPtrToWord [MFC], IsEmpty
- CMapPtrToWord [MFC], Lookup
- CMapPtrToWord [MFC], LookupKey
- CMapPtrToWord [MFC], RemoveAll
- CMapPtrToWord [MFC], RemoveKey
- CMapPtrToWord [MFC], SetAt
ms.assetid: 4631c6b6-d49f-49d9-adc0-1e0491e32d7b
ms.openlocfilehash: 698e306896fd62888a84b6d6ce55fb4c9678187b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442648"
---
# <a name="cmapptrtoword-class"></a>Clase CMapPtrToWord

Admite mapas de palabras de 16 bits con clave de punteros void.

## <a name="syntax"></a>Sintaxis

```
class CMapPtrToWord : public CObject
```

## <a name="members"></a>Members

Las funciones miembro de `CMapPtrToWord` son similares a las funciones miembro de la clase [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para obtener información específica de la función miembro. Siempre que vea un puntero `CObject` como un parámetro de función o un valor devuelto, sustituya WORD. Siempre que vea un `CString` o un puntero **const** a **Char** como un parámetro de función o un valor devuelto, sustituya un puntero a **void**.

`BOOL CMapPtrToWord::Lookup( const void* <key>, WORD& <rValue> ) const;`

por ejemplo, se traduce en

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapPtrToWord::CMapPtrToWord](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapPtrToWord:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Devuelve el número de elementos de este mapa.|
|[CMapPtrToWord::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|
|[CMapPtrToWord::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtiene el siguiente elemento para recorrer en iteración.|
|[CMapPtrToWord:: obtiene](../../mfc/reference/cmapstringtoob-class.md#getsize)|Devuelve el número de elementos de este mapa.|
|[CMapPtrToWord::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Devuelve la posición del primer elemento.|
|[CMapPtrToWord::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcula el valor hash de una clave especificada.|
|[CMapPtrToWord::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializa la tabla hash.|
|[CMapPtrToWord:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Comprueba la condición de asignación vacía (no hay elementos).|
|[CMapPtrToWord:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Busca un puntero void basado en la clave del puntero void. El valor de puntero, no la entidad a la que apunta, se usa para la comparación de claves.|
|[CMapPtrToWord:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Devuelve una referencia a la clave asociada al valor de clave especificado.|
|[CMapPtrToWord:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Quita todos los elementos de esta asignación.|
|[CMapPtrToWord::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Quita un elemento especificado por una clave.|
|[CMapPtrToWord:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapPtrToWord:: Operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Inserta un elemento en la asignación: sustitución de operador para `SetAt`.|

## <a name="remarks"></a>Observaciones

`CMapWordToPtr` incorpora la macro IMPLEMENT_DYNAMIC para admitir el acceso de tipo en tiempo de ejecución y el volcado a un objeto `CDumpContext`. Si necesita un volcado de elementos de mapa individuales, debe establecer la profundidad del contexto de volcado en 1 o más.

Los mapas de puntero a palabra no se pueden serializar.

Cuando se elimina un objeto de `CMapPtrToWord`, o cuando se quitan sus elementos, se quitan los punteros y las palabras. No se quitan las entidades a las que hacen referencia los punteros de clave.

Para obtener más información sobre `CMapPtrToWord`, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMapPtrToWord`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
