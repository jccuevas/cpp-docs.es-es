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
ms.openlocfilehash: 99ca0c475d7fe700c2350ae05a87b8e64b10d775
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509972"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy (Enumeración)

Indica cómo una operación asincrónica de intentar realizar la transición a un estado terminal de completado o error debería comportarse con respecto a un estado cancelado solicitada por el cliente.

## <a name="syntax"></a>Sintaxis

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Nombre|Descripción|
|----------|-----------------|
|`RemainCanceled`|Si la operación asincrónica está actualmente en un estado cancelado solicitada por el cliente, esto indica que permanecerá en el estado cancelado en lugar de realizar la transición a un terminal completado o el estado de error.|
|`TransitionFromCanceled`|Si la operación asincrónica está actualmente en un estado cancelado solicitada por el cliente, esto indica que debe pasar estado desde que se completó estado cancelado en el estado del terminal o error según lo determinado por la llamada que usa esta marca.|

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)