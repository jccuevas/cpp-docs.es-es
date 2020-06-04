---
title: CancelTransitionPolicy (Enumeración)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: e820b3fffb4a00e95a1210a5c0beb3229c6d1657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214128"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy (Enumeración)

Indica cómo se debe comportar un intento de transición de una operación asincrónica a un estado de terminal completado o de error con respecto a un estado cancelado solicitado por el cliente.

## <a name="syntax"></a>Sintaxis

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Members

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`RemainCanceled`|Si la operación asincrónica se encuentra actualmente en un estado cancelado solicitado por el cliente, esto indica que permanecerá en el estado cancelado, en lugar de pasar a un terminal completado o a un estado de error.|
|`TransitionFromCanceled`|Si la operación asincrónica se encuentra actualmente en un estado cancelado solicitado por el cliente, esto indica que el estado debe pasar de ese estado cancelado al estado de terminal completado o error, según lo determinado por la llamada que use esta marca.|

## <a name="requirements"></a>Requisitos

**Encabezado:** Async. h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Consulte también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)
