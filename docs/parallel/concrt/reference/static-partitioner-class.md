---
title: "static_partitioner (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppl/concurrency::static_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "static_partitioner (clase)"
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# static_partitioner (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `static_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`.  La clase Partitioner divide el intervalo en tantos fragmentos como trabajadores hay disponibles para el programador subyacente.  
  
## Sintaxis  
  
```  
class static_partitioner;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[static\_partitioner::static\_partitioner \(Constructor\)](../Topic/static_partitioner::static_partitioner%20Constructor.md)|Construye un objeto `static_partitioner`.|  
|[static\_partitioner::~static\_partitioner \(Destructor\)](../Topic/static_partitioner::~static_partitioner%20Destructor.md)|Destruye un objeto `static_partitioner`.|  
  
## Jerarquía de herencia  
 `static_partitioner`  
  
## Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)