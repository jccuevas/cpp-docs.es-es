---
title: "event (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::event"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "event (clase)"
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# event (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un evento de reinicio manual que es explícitamente consciente del runtime de simultaneidad.  
  
## Sintaxis  
  
```  
class event;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[event::~event \(Destructor\)](../Topic/event::~event%20Destructor.md)|Destruye un evento.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[event::reset \(Método\)](../Topic/event::reset%20Method.md)|Restablece el evento a un estado no señalado.|  
|[event::set \(Método\)](../Topic/event::set%20Method.md)|Señala el evento.|  
|[event::wait \(Método\)](../Topic/event::wait%20Method.md)|Espera a que se señale el evento.|  
|[event::wait\_for\_multiple \(Método\)](../Topic/event::wait_for_multiple%20Method.md)|Espera a que se señalen varios eventos.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[event::timeout\_infinite \(Constante\)](../Topic/event::timeout_infinite%20Constant.md)|Valor que indica que una espera nunca debe agotar el tiempo de espera.|  
  
## Comentarios  
 Para obtener más información, vea [Estructuras de datos de sincronización](../../../parallel/concrt/synchronization-data-structures.md).  
  
## Jerarquía de herencia  
 `event`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)