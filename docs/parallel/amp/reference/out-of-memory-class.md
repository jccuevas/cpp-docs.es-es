---
title: "out_of_memory (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::out_of_memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "out_of_memory (clase)"
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# out_of_memory (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La excepción se produce cuando un método produce un error debido a la falta de memoria del sistema o del dispositivo.  
  
## Sintaxis  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[out\_of\_memory::out\_of\_memory \(Constructor\)](../Topic/out_of_memory::out_of_memory%20Constructor.md)|Inicializa una nueva instancia de la clase `out_of_memory`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)