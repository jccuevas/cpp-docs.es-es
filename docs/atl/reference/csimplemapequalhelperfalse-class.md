---
title: CSimpleMapEqualHelperFalse (clase)
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
ms.openlocfilehash: 9c4241049ad323047f06c0b29f946521f2c02167
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268907"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse (clase)

Esta clase es una aplicación auxiliar para el [CSimpleMap](../../atl/reference/csimplemap-class.md) clase.

## <a name="syntax"></a>Sintaxis

```
template <class TKey, class TVal>
class CSimpleMapEqualHelperFalse
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Estático) Comprueba la igualdad de dos claves.|
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Estático) Devuelve "false".|

## <a name="remarks"></a>Comentarios

Esta clase de rasgos es un complemento para el `CSimpleMap` clase. Proporciona un método para comparar dos elementos que contiene el `CSimpleMap` objeto específicamente dos elementos de valor o dos elementos clave.

La comparación de valor siempre devolverá false y, además, se llamará a `ATLASSERT` con el argumento false si nunca se hace referencia. En situaciones donde no se define lo suficientemente la prueba de igualdad, esta clase permite que un mapa que contiene pares de clave/valor para funcionar correctamente para la mayoría de los métodos, pero producirá un error de forma bien definida para los métodos que dependen de las comparaciones como [CSimpleMap:: FindVal](../../atl/reference/csimplemap-class.md#findval).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey

Comprueba la igualdad de dos claves.

```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```

### <a name="parameters"></a>Parámetros

*k1*<br/>
La primera clave.

*k2*<br/>
La segunda clave.

### <a name="return-value"></a>Valor devuelto

Devuelve true si las claves si no son iguales, es false.

### <a name="remarks"></a>Comentarios

Este método llama a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue

Devuelve false.

```
static bool IsEqualValue(const TVal&, const TVal&);
```

### <a name="return-value"></a>Valor devuelto

Devuelve false.

### <a name="remarks"></a>Comentarios

Este método siempre devuelve false y llamará a `ATLASSERT` con el argumento false si nunca se hace referencia. El propósito de `CSimpleMapEqualHelperFalse::IsEqualValue` es forzar a métodos mediante comparaciones genere un error de una manera bien definida cuando las pruebas de igualdad no se han definido correctamente.

## <a name="see-also"></a>Vea también

[CSimpleMapEqualHelper (clase)](../../atl/reference/csimplemapequalhelper-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
