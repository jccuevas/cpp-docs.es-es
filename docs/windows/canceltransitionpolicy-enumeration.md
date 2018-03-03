---
title: "CancelTransitionPolicy (enumeración) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14c3016d767e38e032a745a5957fa93d51f2dae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy (Enumeración)
Indica cómo una operación asincrónica de intentar realizar la transición a un estado terminal de completado o debe comportarse el error con respecto a un estado cancelado solicitada por el cliente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum CancelTransitionPolicy;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`RemainCanceled`|Si la operación asincrónica está actualmente en un estado cancelado solicitada por el cliente, esto indica que permanecerá en el estado cancelado en lugar de realizar la transición a un estado de error o terminal completado.|  
|`TransitionFromCanceled`|Si la operación asincrónica está actualmente en un estado cancelado solicitada por el cliente, esto indica que el estado deberá pasar desde que se completó estado cancelado para el estado terminal de o error según lo determinado por la llamada que usa esta marca.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)