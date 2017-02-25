---
title: "location (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::location"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "location (clase)"
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# location (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una abstracción de una ubicación física en el hardware.  
  
## Sintaxis  
  
```  
class location;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[location::location \(Constructor\)](../Topic/location::location%20Constructor.md)|Sobrecargado.  Construye un objeto `location`.|  
|[location::~location \(Destructor\)](../Topic/location::~location%20Destructor.md)|Destruye un objeto `location`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[location::current \(Método\)](../Topic/location::current%20Method.md)|Devuelve un objeto de `location` que representa el lugar más específico que el subproceso de llamada se está ejecutando.|  
|[location::from\_numa\_node \(Método\)](../Topic/location::from_numa_node%20Method.md)|Devuelve un objeto de `location` que representa un nodo NUMA especificado.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[location::operator\!\= \(Operador\)](../Topic/location::operator!=%20Operator.md)|Determina si dos objetos de `location` representan la ubicación diferente.|  
|[location::operator\= \(Operador\)](../Topic/location::operator=%20Operator.md)|Asigna el contenido de un objeto diferente de `location` éste.|  
|[location::operator\=\= \(Operador\)](../Topic/location::operator==%20Operator.md)|Determina si dos objetos de `location` representan la misma ubicación.|  
  
## Jerarquía de herencia  
 `location`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)