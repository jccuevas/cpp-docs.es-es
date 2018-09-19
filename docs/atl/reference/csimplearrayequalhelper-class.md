---
title: CSimpleArrayEqualHelper (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2613a885dd5399c3655ecb853f3977be71928526
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021062"
---
# <a name="csimplearrayequalhelper-class"></a>CSimpleArrayEqualHelper (clase)

Esta clase es una aplicación auxiliar para el [CSimpleArray](../../atl/reference/csimplearray-class.md) clase.

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

|Name|Descripción|
|----------|-----------------|
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Estático) Comprueba si dos `CSimpleArray` igualdad de los elementos de objeto.|

## <a name="remarks"></a>Comentarios

Esta clase de rasgos es un complemento para el `CSimpleArray` clase. Proporciona un método para comparar dos elementos almacenados en un `CSimpleArray` objeto. De forma predeterminada, los elementos se comparan mediante **operator=()**, pero si la matriz contiene los tipos de datos complejos que no tienen su propio operador de igualdad, deberá invalidar esta clase.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsimpcoll.h

##  <a name="isequal"></a>  CSimpleArrayEqualHelper::IsEqual

Comprueba si dos `CSimpleArray` igualdad de los elementos de objeto.

```
static bool IsEqual(
    const T& t1,
    const T& t2);
```

### <a name="parameters"></a>Parámetros

*T1*<br/>
Un objeto de tipo T.

*T2*<br/>
Un objeto de tipo T.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los elementos si no son iguales, es false.

## <a name="see-also"></a>Vea también

[CSimpleArray (clase)](../../atl/reference/csimplearray-class.md)<br/>
[CSimpleArrayEqualHelperFalse (clase)](../../atl/reference/csimplearrayequalhelperfalse-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
