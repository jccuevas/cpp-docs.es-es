---
title: Clase CMapWordToOb
ms.date: 11/04/2016
f1_keywords:
- CMapWordToOb
- AFXCOLL/CMapWordToOb
- AFXCOLL/CMapWordToOb::CMapWordToOb
- AFXCOLL/CMapWordToOb::GetCount
- AFXCOLL/CMapWordToOb::GetHashTableSize
- AFXCOLL/CMapWordToOb::GetNextAssoc
- AFXCOLL/CMapWordToOb::GetSize
- AFXCOLL/CMapWordToOb::GetStartPosition
- AFXCOLL/CMapWordToOb::HashKey
- AFXCOLL/CMapWordToOb::InitHashTable
- AFXCOLL/CMapWordToOb::IsEmpty
- AFXCOLL/CMapWordToOb::Lookup
- AFXCOLL/CMapWordToOb::LookupKey
- AFXCOLL/CMapWordToOb::RemoveAll
- AFXCOLL/CMapWordToOb::RemoveKey
- AFXCOLL/CMapWordToOb::SetAt
helpviewer_keywords:
- CMapWordToOb [MFC], CMapWordToOb
- CMapWordToOb [MFC], GetCount
- CMapWordToOb [MFC], GetHashTableSize
- CMapWordToOb [MFC], GetNextAssoc
- CMapWordToOb [MFC], GetSize
- CMapWordToOb [MFC], GetStartPosition
- CMapWordToOb [MFC], HashKey
- CMapWordToOb [MFC], InitHashTable
- CMapWordToOb [MFC], IsEmpty
- CMapWordToOb [MFC], Lookup
- CMapWordToOb [MFC], LookupKey
- CMapWordToOb [MFC], RemoveAll
- CMapWordToOb [MFC], RemoveKey
- CMapWordToOb [MFC], SetAt
ms.assetid: 9c9bcd76-456f-4cf9-b03c-dd28b49d5e4f
ms.openlocfilehash: 80d53f195ba98f853c86a4d9c38fa9fcda52da3b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442585"
---
# <a name="cmapwordtoob-class"></a>Clase CMapWordToOb

Admite mapas de punteros `CObject` con clave de palabras de 16 bits.

## <a name="syntax"></a>Sintaxis

```
class CMapWordToOb : public CObject
```

## <a name="members"></a>Members

Las funciones miembro de `CMapWordToOb` son similares a las funciones miembro de la clase [CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md). Debido a esta similitud, puede utilizar la documentación de referencia de `CMapStringToOb` para obtener información específica de la función miembro. Siempre que vea un `CString` o un puntero **const** a **Char** como un parámetro de función o un valor devuelto, sustituya Word.

`BOOL CMapWordToOb::Lookup( WORD <key>, CObject*& <rValue> ) const;`

por ejemplo, se traduce en

`BOOL CMapStringToOb::Lookup( const char* <key>, CObject*& <rValue> ) const;`

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapWordToOb::CMapWordToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|Constructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapWordToOb:: GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|Devuelve el número de elementos de este mapa.|
|[CMapWordToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|Determina el número actual de elementos de la tabla hash.|
|[CMapWordToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|Obtiene el siguiente elemento para recorrer en iteración.|
|[CMapWordToOb:: obtiene](../../mfc/reference/cmapstringtoob-class.md#getsize)|Devuelve el número de elementos de este mapa.|
|[CMapWordToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|Devuelve la posición del primer elemento.|
|[CMapWordToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|Calcula el valor hash de una clave especificada.|
|[CMapWordToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|Inicializa la tabla hash.|
|[CMapWordToOb:: IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|Comprueba la condición de asignación vacía (no hay elementos).|
|[CMapWordToOb:: Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|Busca un puntero void basado en la clave del puntero void. El valor de puntero, no la entidad a la que apunta, se usa para la comparación de claves.|
|[CMapWordToOb:: LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|Devuelve una referencia a la clave asociada al valor de clave especificado.|
|[CMapWordToOb:: RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|Quita todos los elementos de esta asignación.|
|[CMapWordToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|Quita un elemento especificado por una clave.|
|[CMapWordToOb:: SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|Inserta un elemento en la asignación; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMapWordToOb:: Operator \[ \]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|Inserta un elemento en la asignación: sustitución de operador para `SetAt`.|

## <a name="remarks"></a>Observaciones

`CMapWordToOb` incorpora la macro IMPLEMENT_SERIAL para admitir la serialización y el volcado de sus elementos. Cada elemento se serializa a su vez si una asignación se almacena en un archivo, ya sea con el operador de inserción sobrecargado ( **<<** ) o con la función miembro `Serialize`.

Si necesita un volcado de elementos individuales de `CObject` de palabras, debe establecer la profundidad del contexto de volcado en 1 o más.

Cuando se elimina un objeto de `CMapWordToOb`, o cuando se quitan sus elementos, se quitan los punteros de `CObject`. Los objetos a los que hacen referencia los punteros de `CObject` no se destruyen.

Para obtener más información sobre `CMapWordToOb`, vea las [colecciones](../../mfc/collections.md)de artículos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

`CMapWordToOb`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcoll. h

## <a name="see-also"></a>Consulte también

[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
