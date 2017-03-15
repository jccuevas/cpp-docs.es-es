---
title: "Semaphore (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Semaphore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Semaphore (clase)"
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Semaphore (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un objeto de sincronización que controla un recurso compartido que puede admitir un número limitado de usuarios.  
  
## Sintaxis  
  
```  
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>  
```  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`SyncLock`|Un sinónimo de una clase que admita sincrónico bloqueos.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Semaphore::Semaphore \(Constructor\)](../windows/semaphore-semaphore-constructor.md)|Inicializa una nueva instancia de la clase semaphore.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[InvokeHelper::Invoke \(Método\)](../windows/invokehelper-invoke-method.md)|Llama al controlador de eventos cuya firma contiene el número especificado de argumentos.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Semaphore::Lock \(Método\)](../windows/semaphore-lock-method.md)|Espera hasta que el objeto actual, o el objeto asociado al identificador especificado, está en el estado señalado o ha transcurrido el intervalo de tiempo de espera especificado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Semaphore::operator\= \(Operador\)](../windows/semaphore-operator-assign-operator.md)|Mueve el identificador especificado de un objeto semaphore al objeto actual del semáforo.|  
  
## Jerarquía de herencia  
 `Semaphore`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [Microsoft::WRL::Wrappers \(Espacio de nombres\)](../Topic/Microsoft::WRL::Wrappers%20Namespace.md)