---
title: "simple_partitioner (Clase) | Microsoft Docs"
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
  - "ppl/concurrency::simple_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "simple_partitioner (clase)"
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# simple_partitioner (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `simple_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`.  La clase Partitioner divide el intervalo en fragmentos de forma que cada fragmento tiene al menos el número de iteraciones especificadas por el tamaño del fragmento.  
  
## Sintaxis  
  
```  
class simple_partitioner;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[simple\_partitioner::simple\_partitioner \(Constructor\)](../Topic/simple_partitioner::simple_partitioner%20Constructor.md)|Construye un objeto `simple_partitioner`.|  
|[simple\_partitioner::~simple\_partitioner \(Destructor\)](../Topic/simple_partitioner::~simple_partitioner%20Destructor.md)|Destruye un objeto `simple_partitioner`.|  
  
## Jerarquía de herencia  
 `simple_partitioner`  
  
## Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)