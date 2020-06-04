---
title: Clase CSimpleArrayEqualHelper
ms.date: 11/04/2016
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
ms.openlocfilehash: 386b005777b3e31dd74916a41bc5af2ab82df210
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330884"
---
# <a name="csimplearrayequalhelper-class"></a>Clase CSimpleArrayEqualHelper

Esta clase es una aplicación auxiliar para la [clase CSimpleArray.](../../atl/reference/csimplearray-class.md)

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CSimpleArrayEqualHelper
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Una clase derivada.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Estático) Prueba `CSimpleArray` la igualdad de dos elementos de objeto.|

## <a name="remarks"></a>Observaciones

Esta clase de rasgos `CSimpleArray` es un suplemento a la clase. Proporciona un método para comparar dos `CSimpleArray` elementos almacenados en un objeto. De forma predeterminada, los elementos se comparan mediante **operator -()**, pero si la matriz contiene tipos de datos complejos que carecen de su propio operador de igualdad, deberá reemplazar esta clase.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

## <a name="csimplearrayequalhelperisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual

Prueba `CSimpleArray` la igualdad de dos elementos de objeto.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Parámetros

*T1*<br/>
Objeto de tipo T.

*t2*<br/>
Objeto de tipo T.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los elementos son iguales, false en caso contrario.

## <a name="see-also"></a>Consulte también

[Clase CSimpleArray](../../atl/reference/csimplearray-class.md)<br/>
[Clase CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
