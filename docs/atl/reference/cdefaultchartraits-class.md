---
title: Clase CDefaultCharTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: 40c4d107d05e6d7b610e7c46be920d91d8fe6086
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327093"
---
# <a name="cdefaultchartraits-class"></a>Clase CDefaultCharTraits

Esta clase proporciona dos funciones estáticas para convertir caracteres entre mayúsculas y minúsculas.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en la colección.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|(Estático) Llame a esta función para convertir un carácter a mayúsculas.|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Estático) Llame a esta función para convertir un carácter a minúsculas.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona funciones que utiliza la clase [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cdefaultchartraitschartolower"></a><a name="chartolower"></a>CDefaultCharTraits::CharToLower

Llame a esta función para convertir un carácter a minúsculas.

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Carácter que se va a convertir en minúsculas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

## <a name="cdefaultchartraitschartoupper"></a><a name="chartoupper"></a>CDefaultCharTraits::CharToUpper

Llame a esta función para convertir un carácter a mayúsculas.

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Carácter que se va a convertir en mayúsculas.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
