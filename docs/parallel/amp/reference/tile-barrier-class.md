---
title: "tile_barrier (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::tile_barrier"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tile_barrier (clase)"
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# tile_barrier (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Sincroniza la ejecución de los subprocesos que se ejecutan en el grupo de subprocesos \(el mosaico\) mediante los métodos de `wait`.  Solo el runtime puede crear instancias de esta clase.  
  
## Sintaxis  
  
```  
class tile_barrier;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tile\_barrier::tile\_barrier \(Constructor\)](../Topic/tile_barrier::tile_barrier%20Constructor.md)|Inicializa una nueva instancia de la clase `tile_barrier`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tile\_barrier::wait \(Método\)](../Topic/tile_barrier::wait%20Method.md)|Indica a todos los subprocesos del grupo de subprocesos \(mosaico\) que detengan la ejecución hasta que todos los subprocesos del mosaico hayan terminado de esperar.|  
|[tile\_barrier::wait\_with\_all\_memory\_fence \(Método\)](../Topic/tile_barrier::wait_with_all_memory_fence%20Method.md)|Bloquea la ejecución de todos los subprocesos de una tesela hasta que se hayan completado todos los accesos a memoria y todos los subprocesos del mosaico hayan alcanzado esta llamada.|  
|[tile\_barrier::wait\_with\_global\_memory\_fence \(Método\)](../Topic/tile_barrier::wait_with_global_memory_fence%20Method.md)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los accesos globales a memoria se hayan completado y todos los subprocesos del mosaico hayan alcanzado esta llamada.|  
|[tile\_barrier::wait\_with\_tile\_static\_memory\_fence \(Método\)](../Topic/tile_barrier::wait_with_tile_static_memory_fence%20Method.md)|Bloquea la ejecución de todos los subprocesos de una tesela hasta que se hayan completado todos los accesos a memoria `tile_static` y todos los subprocesos del mosaico hayan alcanzado esta llamada.|  
  
## Jerarquía de herencia  
 `tile_barrier`  
  
## Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)