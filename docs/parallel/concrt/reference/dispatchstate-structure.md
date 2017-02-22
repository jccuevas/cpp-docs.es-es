---
title: "DispatchState (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::DispatchState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DispatchState (estructura)"
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# DispatchState (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La estructura `DispatchState` se usa para transferir el estado al método `IExecutionContext::Dispatch`.  Describe las circunstancias bajo las que el método `Dispatch` se invoca en una interfaz `IExecutionContext`.  
  
## Sintaxis  
  
```  
struct DispatchState;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[DispatchState::DispatchState \(Constructor\)](../Topic/DispatchState::DispatchState%20Constructor.md)|Crea un nuevo objeto `DispatchState`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[DispatchState::m\_dispatchStateSize \(Miembro de datos\)](../Topic/DispatchState::m_dispatchStateSize%20Data%20Member.md)|Tamaño de esta estructura, que se utiliza para control de versiones.|  
|[DispatchState::m\_fIsPreviousContextAsynchronouslyBlocked \(Miembro de datos\)](../Topic/DispatchState::m_fIsPreviousContextAsynchronouslyBlocked%20Data%20Member.md)|Indica si este contexto ha escrito el método `Dispatch` porque el contexto anterior se bloqueó de forma asincrónica.  Se usa únicamente en el contexto de programación UMS y está establecido en el valor `0` en todos los demás contextos de ejecución.|  
|[DispatchState::m\_reserved \(Miembro de datos\)](../Topic/DispatchState::m_reserved%20Data%20Member.md)|Bits reservados para el paso futuro de la información.|  
  
## Jerarquía de herencia  
 `DispatchState`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IExecutionContext::Dispatch \(Método\)](../Topic/IExecutionContext::Dispatch%20Method.md)