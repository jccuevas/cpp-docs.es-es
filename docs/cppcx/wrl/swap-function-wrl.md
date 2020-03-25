---
title: Swap (función) (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
ms.openlocfilehash: e665dbca025da56ba81c3fdf1749b2d653b78c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213569"
---
# <a name="swap-function-wrl"></a>Swap (función) (WRL)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>Parámetros

*left*<br/>
Primer argumento.

*right*<br/>
Segundo argumento.

## <a name="return-value"></a>Valor devuelto

## <a name="remarks"></a>Observaciones

Intercambia los valores de los dos argumentos especificados.

## <a name="requirements"></a>Requisitos

**Encabezado:** Internal. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
