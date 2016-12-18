---
title: "ScheduleGroup (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::ScheduleGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ScheduleGroup (clase)"
ms.assetid: 86d380ff-f2e8-411c-b1a8-22bd3079824a
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ScheduleGroup (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa una abstracción para un grupo de programación.  Los grupos de programación organizan un conjunto de trabajos relacionados que se benefician de programarse juntos ya sea temporalmente, mediante la ejecución de otra tarea en el mismo grupo antes de trasladarse a otro grupo, o espacialmente, mediante la ejecución de varios elementos del mismo grupo en el mismo nodo NUMA o socket físico.  
  
## Sintaxis  
  
```  
class ScheduleGroup;  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ScheduleGroup::~ScheduleGroup \(Destructor\)](../Topic/ScheduleGroup::~ScheduleGroup%20Destructor.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ScheduleGroup::Id \(Método\)](../Topic/ScheduleGroup::Id%20Method.md)|Devuelve un identificador para el grupo de programación que es único dentro del programador al que pertenece el grupo.|  
|[ScheduleGroup::Reference \(Método\)](../Topic/ScheduleGroup::Reference%20Method.md)|Incrementa el contador de referencias del grupo de programación.|  
|[ScheduleGroup::Release \(Método\)](../Topic/ScheduleGroup::Release%20Method.md)|Disminuye el contador de referencias del grupo de programación.|  
|[ScheduleGroup::ScheduleTask \(Método\)](../Topic/ScheduleGroup::ScheduleTask%20Method.md)|Programa una tarea ligera dentro del grupo de programación.|  
  
## Jerarquía de herencia  
 `ScheduleGroup`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [CurrentScheduler \(Clase\)](../../../parallel/concrt/reference/currentscheduler-class.md)   
 [Scheduler \(Clase\)](../../../parallel/concrt/reference/scheduler-class.md)   
 [Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)