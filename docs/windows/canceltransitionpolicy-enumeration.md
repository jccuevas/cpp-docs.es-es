---
title: "CancelTransitionPolicy (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled"
  - "module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled"
  - "module/Microsoft::WRL::CancelTransitionPolicy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CancelTransitionPolicy (Enumeración)"
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# CancelTransitionPolicy (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica cómo el intento de una operación asincrónica para la transición a un estado terminal de completo o error debe comportarse con respecto a un estado cancelado cliente\- solicitada.  
  
## Sintaxis  
  
```  
enum CancelTransitionPolicy;  
```  
  
## Miembros  
  
### Valores  
  
|Name|Descripción|  
|----------|-----------------|  
|`RemainCanceled`|Si la operación asincrónica se encuentra en un estado cancelado cliente\- solicitada, esto indica que permanecerá en el estado cancelado en comparación con la transición a un terminal completado o el estado de error.|  
|`TransitionFromCanceled`|Si la operación asincrónica se encuentra en un estado cancelado cliente\- solicitada, esto indica que estado si la transición del estado cancelado el estado terminal de completo o error determinado por la llamada que utiliza este marcador.|  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)