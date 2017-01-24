---
title: "auto_partitioner (Clase) | Microsoft Docs"
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
  - "ppl/concurrency::auto_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_partitioner (clase)"
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
caps.latest.revision: 8
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_partitioner (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `auto_partitioner` representa a los métodos predeterminados `parallel_for`, `parallel_for_each` y usa `parallel_transform` para dividir el intervalo sobre el que iteran.  Este método de particiones emplea la apropiación del intervalo para el equilibrio de carga, así como la cancelación por iterar.  
  
## Sintaxis  
  
```  
class auto_partitioner;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[auto\_partitioner::auto\_partitioner \(Constructor\)](../Topic/auto_partitioner::auto_partitioner%20Constructor.md)|Construye un objeto `auto_partitioner`.|  
|[auto\_partitioner::~auto\_partitioner \(Destructor\)](../Topic/auto_partitioner::~auto_partitioner%20Destructor.md)|Destruye un objeto `auto_partitioner`.|  
  
## Jerarquía de herencia  
 `auto_partitioner`  
  
## Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)