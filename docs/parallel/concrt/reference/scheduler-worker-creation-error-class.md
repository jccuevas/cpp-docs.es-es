---
title: "scheduler_worker_creation_error (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::scheduler_worker_creation_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_worker_creation_error (clase)"
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# scheduler_worker_creation_error (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción producida debido a un error al crear un contexto de ejecución del trabajo en el runtime de simultaneidad.  
  
## Sintaxis  
  
```  
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scheduler\_worker\_creation\_error::scheduler\_worker\_creation\_error \(Constructor\)](../Topic/scheduler_worker_creation_error::scheduler_worker_creation_error%20Constructor.md)|Sobrecargado.  Construye un objeto `scheduler_worker_creation_error`.|  
  
## Comentarios  
 Esta excepción se produce normalmente cuando falla una llamada al sistema operativo para crear contextos de ejecución desde dentro del runtime de simultaneidad.  Los contextos de ejecución son los subprocesos que ejecutan tareas del runtime de simultaneidad.  El código de error que se devolvería normalmente de una llamada al método `GetLastError` de Win32 se convierte en un valor de `HRESULT` escrito y se puede recuperar utilizando el método `get_error_code`de la clase base.  
  
## Jerarquía de herencia  
 `exception`  
  
 [scheduler\_resource\_allocation\_error](../../../parallel/concrt/reference/scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)