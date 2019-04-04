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
ms.openlocfilehash: cfd8e25f98ec1001a8fbd287eaec12408b9f240e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785766"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy (Enumeración)

Indica cómo una operación asincrónica de intentar realizar la transición a un estado terminal de completado o error debería comportarse con respecto a un estado cancelado solicitada por el cliente.

## <a name="syntax"></a>Sintaxis

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Miembros

### <a name="values"></a>Valores

|Name|Descripción|
|----------|-----------------|
|`RemainCanceled`|Si la operación asincrónica está actualmente en un estado cancelado solicitada por el cliente, esto indica que permanecerá en el estado cancelado en lugar de realizar la transición a un terminal completado o el estado de error.|
|`TransitionFromCanceled`|Si la operación asincrónica está actualmente en un estado cancelado solicitada por el cliente, esto indica que debe pasar estado desde que se completó estado cancelado en el estado del terminal o error según lo determinado por la llamada que usa esta marca.|

## <a name="requirements"></a>Requisitos

**Encabezado:** async.h

**Espacio de nombres**: Microsoft::WRL

## <a name="see-also"></a>Vea también

[Microsoft::WRL (espacio de nombres)](microsoft-wrl-namespace.md)