---
title: Swap (función) (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
ms.openlocfilehash: daa5ab94146866dfa8f1983afc1ad7b37cdb6b06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476419"
---
# <a name="swap-function-wrl"></a>Swap (función) (WRL)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

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

## <a name="remarks"></a>Comentarios

Intercambia los valores de los dos argumentos especificados.

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Namespace:** wrl

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (espacio de nombres)](../windows/microsoft-wrl-details-namespace.md)