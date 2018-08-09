---
title: CancelTransitionPolicy (enumeración) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
dev_langs:
- C++
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd203ee0413b60bc7aa713e7923fd4d69bde665e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642963"
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