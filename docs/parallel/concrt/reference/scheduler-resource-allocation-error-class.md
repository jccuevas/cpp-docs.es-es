---
title: "scheduler_resource_allocation_error (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::scheduler_resource_allocation_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "scheduler_resource_allocation_error (clase)"
ms.assetid: 8b40449a-7abb-4d0a-bb85-c0e9a495ae97
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# scheduler_resource_allocation_error (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce debido a un error al adquirir un recurso crítico en el runtime de simultaneidad.  
  
## Sintaxis  
  
```  
class scheduler_resource_allocation_error : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scheduler\_resource\_allocation\_error::scheduler\_resource\_allocation\_error \(Constructor\)](../Topic/scheduler_resource_allocation_error::scheduler_resource_allocation_error%20Constructor.md)|Sobrecargado.  Construye un objeto `scheduler_resource_allocation_error`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[scheduler\_resource\_allocation\_error::get\_error\_code \(Método\)](../Topic/scheduler_resource_allocation_error::get_error_code%20Method.md)|Devuelve el código de error que generó la excepción.|  
  
## Comentarios  
 Normalmente se produce esta excepción cuando se produce un error en una llamada al sistema operativo desde dentro del runtime de simultaneidad.  El código de error que se devolvería normalmente de una llamada al método `GetLastError` de Win32 se convierte en un valor de `HRESULT` escrito y se puede recuperar utilizando el método de `get_error_code` .  
  
## Jerarquía de herencia  
 `exception`  
  
 `scheduler_resource_allocation_error`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)