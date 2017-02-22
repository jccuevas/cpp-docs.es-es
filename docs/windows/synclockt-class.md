---
title: "SyncLockT (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SyncLockT (clase)"
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# SyncLockT (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   typename SyncTraits  
>  
class SyncLockT;  
```  
  
#### Parámetros  
 `SyncTraits`  
 El tipo que puede tomar propiedad de un recurso.  
  
## Comentarios  
 Representa un tipo que pueda tomar propiedad exclusivo o compartido de un recurso.  
  
 La clase de SyncLockT se utiliza, por ejemplo, para ayudar a implementar la clase de [SRWLock](../windows/srwlock-class.md) .  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SyncLockT::SyncLockT \(Constructor\)](../Topic/SyncLockT::SyncLockT%20Constructor.md)|Inicializa una nueva instancia de la clase de SyncLockT.|  
|[SyncLockT::~SyncLockT \(Destructor\)](../windows/synclockt-tilde-synclockt-destructor.md)|Desinicializa una instancia de la clase de SyncLockT.|  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SyncLockT::SyncLockT \(Constructor\)](../Topic/SyncLockT::SyncLockT%20Constructor.md)|Inicializa una nueva instancia de la clase de SyncLockT.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SyncLockT::IsLocked \(Método\)](../windows/synclockt-islocked-method.md)|Indica si el objeto actual de SyncLockT posee un recurso; es decir, el objeto de SyncLockT *está bloqueado*.|  
|[SyncLockT::Unlock \(Método\)](../windows/synclockt-unlock-method.md)|Control de versiones de recursos almacenado por el objeto actual de SyncLockT, si existe.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SyncLockT::sync\_ \(Miembro de datos\)](../Topic/SyncLockT::sync_%20Data%20Member.md)|Contiene el recurso subyacente representado por la clase de SyncLockT.|  
  
## Jerarquía de herencia  
 `SyncLockT`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::Details  
  
## Vea también  
 [Microsoft::WRL::Wrappers::Details \(Espacio de nombres\)](../windows/microsoft-wrl-wrappers-details-namespace.md)   
 [SRWLock \(Clase\)](../windows/srwlock-class.md)