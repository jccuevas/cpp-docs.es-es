---
title: "uninitialized_object (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::uninitialized_object"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uninitialized_object (clase)"
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# uninitialized_object (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La excepción que se produce cuando se usa un objeto no inicializado.  
  
## Sintaxis  
  
```  
class uninitialized_object : public runtime_exception;  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[uninitialized\_object::uninitialized\_object \(Constructor\)](../Topic/uninitialized_object::uninitialized_object%20Constructor.md)|Inicializa una nueva instancia de la clase `uninitialized_object`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
 `uninitialized_object`  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)