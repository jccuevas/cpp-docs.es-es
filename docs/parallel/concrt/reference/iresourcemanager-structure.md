---
title: "IResourceManager (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IResourceManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IResourceManager (estructura)"
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# IResourceManager (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una interfaz al Administrador de recursos del runtime de simultaneidad.  Esta es la interfaz que usan los programadores para comunicares con el Administrador de recursos.  
  
## Sintaxis  
  
```  
struct IResourceManager;  
```  
  
## Miembros  
  
### Enumeraciones públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[IResourceManager::OSVersion \(Enumeración\)](../Topic/IResourceManager::OSVersion%20Enumeration.md)|Un tipo enumerado que representa la versión del sistema operativo.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IResourceManager::CreateNodeTopology \(Método\)](../Topic/IResourceManager::CreateNodeTopology%20Method.md)|Presente únicamente en compilaciones de depuración del runtime, este método es un enlace de pruebas diseñado para facilitar las pruebas del administrador de recursos en diversas topologías de hardware, que no requieren hardware real que coincida con la configuración.  Con compilaciones del runtime, este método se devolverá sin realizar ninguna acción.|  
|[IResourceManager::GetAvailableNodeCount \(Método\)](../Topic/IResourceManager::GetAvailableNodeCount%20Method.md)|Devuelve el número de nodos disponibles al administrador de recursos.|  
|[IResourceManager::GetFirstNode \(Método\)](../Topic/IResourceManager::GetFirstNode%20Method.md)|Devuelve el primer nodo de la enumeración ordenada definidos por el administrador de recursos.|  
|[IResourceManager::Reference \(Método\)](../Topic/IResourceManager::Reference%20Method.md)|Incrementa el contador de referencia en la instancia del administrador de recursos.|  
|[IResourceManager::RegisterScheduler \(Método\)](../Topic/IResourceManager::RegisterScheduler%20Method.md)|Registra un programador con el administrador de recursos.  Una vez registrado el programador, debería comunicar con el administrador de recursos usando la interfaz `ISchedulerProxy` que se devuelve.|  
|[IResourceManager::Release \(Método\)](../Topic/IResourceManager::Release%20Method.md)|Disminuye el contador de referencia en la instancia del administrador de recursos.  Se destruye el administrador de recursos cuando su recuento de referencias va a `0`.|  
  
## Comentarios  
 Use la función [CreateResourceManager](../Topic/CreateResourceManager%20Function.md) para obtener una interfaz a la instancia singleton del administrador de recursos.  El método incrementa un recuento de referencias en el Administrador de recursos y se debería invocar el método [IResourceManager::Release](../Topic/IResourceManager::Release%20Method.md) para liberar la referencia cuando haya terminado de trabajar con el Administrador de recursos.  Normalmente, cada programador que se crea invocará este método durante su creación y liberará la referencia al administrador de recursos después de cerrarse.  
  
## Jerarquía de herencia  
 `IResourceManager`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISchedulerProxy \(Estructura\)](../../../parallel/concrt/reference/ischedulerproxy-structure.md)   
 [IScheduler \(Estructura\)](../../../parallel/concrt/reference/ischeduler-structure.md)