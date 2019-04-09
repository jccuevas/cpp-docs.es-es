---
title: Move (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 8d7c959ecb2d3c06872871ba062d2be603489141
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031279"
---
# <a name="move-function"></a>Move (función)

Admite la infraestructura WRL y no está pensado para utilizarse directamente desde el código.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo del argumento.

*arg*<br/>
Para mover un argumento.

## <a name="return-value"></a>Valor devuelto

Parámetro *arg* después de rasgos de referencia o referencia de rvalue, si los hay, se quitaron.

## <a name="remarks"></a>Comentarios

Mueve el argumento especificado de una ubicación a otra.

Para obtener más información, consulte el **mover semántica** sección de [declarador de referencia Rvalue: & &](../../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** internal.h

**Espacio de nombres**: Microsoft::WRL::Details

## <a name="see-also"></a>Vea también

[Microsoft::WRL::Details (Espacio de nombres)](microsoft-wrl-details-namespace.md)