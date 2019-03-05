---
title: CSimpleMapEqualHelper (clase)
ms.date: 11/04/2016
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
ms.openlocfilehash: c614cbb11376c5ae338762c0feaa54c8f1bb3e27
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282778"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper (clase)

Esta clase es una aplicación auxiliar para el [CSimpleMap](../../atl/reference/csimplemap-class.md) clase.

## <a name="syntax"></a>Sintaxis

```
template <class TKey, class TVal>
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parámetros

*TKey*<br/>
El elemento clave.

*TVal*<br/>
El elemento de valor.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Estático) Comprueba la igualdad de dos claves.|
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Estático) Comprueba la igualdad de dos valores.|

## <a name="remarks"></a>Comentarios

Esta clase de rasgos es un complemento para el `CSimpleMap` clase. Proporciona métodos para comparar dos `CSimpleMap` elementos (en concreto, los componentes clave y valor) para la igualdad de objetos. De forma predeterminada, las claves y valores se comparan mediante **operator==()**, pero si el mapa contiene tipos de datos complejos que no tienen su propio operador de igualdad, se puede invalidar esta clase para proporcionar la funcionalidad adicional necesaria.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey

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

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

Comprueba la igualdad de dos valores.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parámetros

*v1*<br/>
Primer valor.

*v2*<br/>
Segundo valor.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los valores si no son iguales, es false.

## <a name="see-also"></a>Vea también

[CSimpleMapEqualHelperFalse (clase)](../../atl/reference/csimplemapequalhelperfalse-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
