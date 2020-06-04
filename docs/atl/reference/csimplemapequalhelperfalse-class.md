---
title: Clase CSimpleMapEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: b6bf1d4e3be849004e13e593fb5f4b5cb87f8123
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330741"
---
# <a name="csimplemapequalhelperfalse-class"></a>Clase CSimpleMapEqualHelperFalse

Esta clase es una aplicación auxiliar para la [clase CSimpleMap.](../../atl/reference/csimplemap-class.md)

## <a name="syntax"></a>Sintaxis

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Estático) Prueba dos claves para la igualdad.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Estático) Devuelve false.|

## <a name="remarks"></a>Observaciones

Esta clase de rasgos `CSimpleMap` es un suplemento a la clase. Proporciona un método para comparar dos elementos contenidos en el `CSimpleMap` objeto, específicamente dos elementos de valor o dos elementos clave.

La comparación de valores siempre devolverá `ATLASSERT` false y, además, llamará con un argumento de false si alguna vez se hace referencia a ella. En situaciones donde la prueba de igualdad no está suficientemente definida, esta clase permite que un mapa que contenga pares clave/valor funcione correctamente para la mayoría de los métodos, pero se produce un error de forma bien definida para métodos que dependen de comparaciones como [CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

## <a name="csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey

Prueba dos claves para la igualdad.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Parámetros

*k1*<br/>
La primera llave.

*k2*<br/>
La segunda llave.

### <a name="return-value"></a>Valor devuelto

Devuelve true si las claves son iguales, false en caso contrario.

### <a name="remarks"></a>Observaciones

Este método llama a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).

## <a name="csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue

Devuelve false.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>Valor devuelto

Devuelve false.

### <a name="remarks"></a>Observaciones

Este método siempre devuelve false `ATLASSERT` y llamará con un argumento de false si alguna vez se hace referencia a él. El propósito `CSimpleMapEqualHelperFalse::IsEqualValue` de ser forzar métodos que utilizan comparaciones fallan de manera bien definida cuando las pruebas de igualdad no se han definido adecuadamente.

## <a name="see-also"></a>Consulte también

[Clase CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
