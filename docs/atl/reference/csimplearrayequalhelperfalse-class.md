---
title: Clase CSimpleArrayEqualHelperFalse
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
ms.openlocfilehash: 5eca3145d64895e34b599fbf83834af142b65973
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330897"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Clase CSimpleArrayEqualHelperFalse

Esta clase es una aplicación auxiliar para la [clase CSimpleArray.](../../atl/reference/csimplearray-class.md)

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CSimpleArrayEqualHelperFalse
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Estático) Devuelve false.|

## <a name="remarks"></a>Observaciones

Esta clase de rasgos `CSimpleArray` es un complemento de la clase. Siempre devuelve false y, además, llamará `ATLASSERT` con un argumento de false si alguna vez se hace referencia a él. En situaciones donde la prueba de igualdad no está suficientemente definida, esta clase permite que una matriz que contenga elementos funcione correctamente para la mayoría de los métodos, pero produce un error de manera bien definida para métodos que dependen de comparaciones como [CSimpleArray::Find](../../atl/reference/csimplearray-class.md#find).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

## <a name="csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual

Devuelve false.

```
static bool IsEqual(const T&, const T&);
```

### <a name="return-value"></a>Valor devuelto

Devuelve false.

### <a name="remarks"></a>Observaciones

Este método siempre devuelve false `ATLASSERT` y llamará con un argumento de false si se hace referencia a él. El propósito `CSimpleArrayEqualHelperFalse::IsEqual` de ser forzar métodos que utilizan comparaciones fallan de manera bien definida cuando las pruebas de igualdad no se han definido adecuadamente.

## <a name="see-also"></a>Consulte también

[Clase CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
