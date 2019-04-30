---
title: CDefaultCharTraits (clase)
ms.date: 11/04/2016
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
ms.openlocfilehash: fe599ee0e84c393bed656b7304fd13d55ce95a50
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258746"
---
# <a name="cdefaultchartraits-class"></a>CDefaultCharTraits (clase)

Esta clase proporciona dos funciones estáticas para la conversión de caracteres entre mayúsculas y minúsculas.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class CDefaultCharTraits
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenará en la colección.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDefaultCharTraits::CharToLower](#chartolower)|(Estático) Llame a esta función para convertir un carácter a mayúsculas.|
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Estático) Llame a esta función para convertir un carácter a minúsculas.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona funciones que se utilizan en la clase [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower

Llame a esta función para convertir un carácter a minúsculas.

```
static wchar_t CharToLower(wchar_t x);
static char CharToLower(char x);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Carácter que se va a convertir en minúsculas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]

##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper

Llame a esta función para convertir un carácter a mayúsculas.

```
static wchar_t CharToUpper(wchar_t x);
static char CharToUpper(char x);
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Carácter que se va a convertir en mayúsculas.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
