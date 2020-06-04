---
title: Move (función)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 65fe85e95453165430c7ef3cfd4c4bb2babd9868
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213712"
---
# <a name="move-function"></a>Move (función)

Es compatible con la infraestructura de WRL y no está diseñada para utilizarse directamente desde el código.

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
Argumento que se va a quitar.

## <a name="return-value"></a>Valor devuelto

Se ha quitado el parámetro *arg* después de la referencia o los rasgos de referencia rvalue, si existen.

## <a name="remarks"></a>Observaciones

Mueve el argumento especificado de una ubicación a otra.

Para obtener más información, vea la sección sobre la **semántica de movimiento** del [declarador de referencia de valor r: & &](../../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** Internal. h

**Espacio de nombres:** Microsoft:: WRL::D etalles

## <a name="see-also"></a>Consulte también

[Microsoft::WRL::Details (espacio de nombres)](microsoft-wrl-details-namespace.md)
