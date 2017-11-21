---
title: DispatchState (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
dev_langs: C++
helpviewer_keywords: DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a6997596876f080ea00611af90d05eb4fddd2857
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="dispatchstate-structure"></a>DispatchState (Estructura)
La estructura `DispatchState` se usa para transferir el estado al método `IExecutionContext::Dispatch`. Describe las circunstancias bajo las que el método `Dispatch` se invoca en una interfaz `IExecutionContext`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct DispatchState;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[DispatchState:: DispatchState](#ctor)|Construye un nuevo objeto `DispatchState`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[M_dispatchstatesize](#m_dispatchstatesize)|Tamaño de esta estructura, que se utiliza para controlar las versiones.|  
|[DispatchState:: M_fispreviouscontextasynchronouslyblocked](#m_fispreviouscontextasynchronouslyblocked)|Indica si este contexto ha escrito el `Dispatch` método porque el contexto anterior se bloqueó de forma asincrónica. Esto sólo se utiliza en el contexto de programación UMS y está establecido en el valor `0` para todos los demás contextos de ejecución.|  
|[DispatchState:: M_reserved](#m_reserved)|Bits reservados para pasar información del futuro.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `DispatchState`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>Constructor DispatchState:: DispatchState  
 Construye un nuevo objeto `DispatchState`.  
  
```
DispatchState();
```  
  
##  <a name="m_dispatchstatesize"></a>Miembro de datos M_dispatchstatesize  
 Tamaño de esta estructura, que se utiliza para controlar las versiones.  
  
```
unsigned long m_dispatchStateSize;
```  
  
##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>Miembro de datos DispatchState  
 Indica si este contexto ha escrito el `Dispatch` método porque el contexto anterior se bloqueó de forma asincrónica. Esto sólo se utiliza en el contexto de programación UMS y está establecido en el valor `0` para todos los demás contextos de ejecución.  
  
```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```  
  
##  <a name="m_reserved"></a>Miembro de datos DispatchState:: M_reserved  
 Bits reservados para pasar información del futuro.  
  
```
unsigned int m_reserved : 31;
```  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
