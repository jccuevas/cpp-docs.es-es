---
title: Clase CSimpleMapEqualHelper
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: d137a35a517ea93139f036f6e9a7a8de06d518a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330754"
---
# <a name="csimplemapequalhelper-class"></a>Clase CSimpleMapEqualHelper

Esta clase es una aplicación auxiliar para la [clase CSimpleMap.](../../atl/reference/csimplemap-class.md)

## <a name="syntax"></a>Sintaxis

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parámetros

*TKey*<br/>
El elemento clave.

*TVal*<br/>
El elemento value.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Estático) Prueba dos claves para la igualdad.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Estático) Prueba dos valores para la igualdad.|

## <a name="remarks"></a>Observaciones

Esta clase de rasgos `CSimpleMap` es un suplemento a la clase. Proporciona métodos para `CSimpleMap` comparar dos elementos de objeto (específicamente, los componentes de clave y valor) para la igualdad. De forma predeterminada, las claves y los valores se comparan mediante **operator ()),** pero si el mapa contiene tipos de datos complejos que carecen de su propio operador de igualdad, esta clase se puede invalidar para proporcionar la funcionalidad adicional necesaria.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

## <a name="csimplemapequalhelperisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey

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

## <a name="csimplemapequalhelperisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue

Prueba dos valores para la igualdad.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parámetros

*v1*<br/>
Primer valor.

*v2*<br/>
Segundo valor.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los valores son iguales, false en caso contrario.

## <a name="see-also"></a>Consulte también

[Clase CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
