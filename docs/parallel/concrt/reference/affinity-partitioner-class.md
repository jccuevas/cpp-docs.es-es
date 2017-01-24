---
title: "affinity_partitioner (Clase) | Microsoft Docs"
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
  - "ppl/concurrency::affinity_partitioner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "affinity_partitioner (clase)"
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# affinity_partitioner (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `affinity_partitioner` es similar a la clase `static_partitioner`, pero mejora la afinidad de caché eligiendo la asignación de subintervalos para subprocesos de trabajo.  Esta clase puede mejorar considerablemente el rendimiento cuando un bucle se vuelve a ejecutar sobre el mismo conjunto de datos, y los datos se ajustan al caché.  Observe que el mismo objeto `affinity_partitioner` debe utilizarse con iteraciones posteriores de un bucle paralelo que se ejecuta sobre un conjunto de datos determinado, para beneficiarse de la situación de los datos.  
  
## Sintaxis  
  
```  
class affinity_partitioner;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[affinity\_partitioner::affinity\_partitioner \(Constructor\)](../Topic/affinity_partitioner::affinity_partitioner%20Constructor.md)|Construye un objeto `affinity_partitioner`.|  
|[affinity\_partitioner::~affinity\_partitioner \(Destructor\)](../Topic/affinity_partitioner::~affinity_partitioner%20Destructor.md)|Destruye un objeto `affinity_partitioner`.|  
  
## Jerarquía de herencia  
 `affinity_partitioner`  
  
## Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)