---
title: CSimpleMapEqualHelper (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1670ff7ed53d05b1dfc09e6953650892b0335f61
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761474"
---
# <a name="csimplemapequalhelper-class"></a>CSimpleMapEqualHelper (clase)

Esta clase es una aplicación auxiliar para el [CSimpleMap](../../atl/reference/csimplemap-class.md) clase.

## <a name="syntax"></a>Sintaxis

```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```

#### <a name="parameters"></a>Parámetros

*TKey*  
El elemento clave.

*TVal*  
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

*k1*  
La primera clave.

*k2*  
La segunda clave.

### <a name="return-value"></a>Valor devuelto

Devuelve true si las claves si no son iguales, es false.

##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue

Comprueba la igualdad de dos valores.

```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```

### <a name="parameters"></a>Parámetros

*V1*  
Primer valor.

*v2*  
Segundo valor.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los valores si no son iguales, es false.

## <a name="see-also"></a>Vea también

[CSimpleMapEqualHelperFalse (clase)](../../atl/reference/csimplemapequalhelperfalse-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)
