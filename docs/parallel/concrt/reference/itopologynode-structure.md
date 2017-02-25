---
title: "ITopologyNode (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::ITopologyNode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITopologyNode (estructura)"
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ITopologyNode (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una interfaz a un nodo de topología definido por el Administrador de recursos.  Un nodo contiene uno o varios recursos de ejecución.  
  
## Sintaxis  
  
```  
struct ITopologyNode;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ITopologyNode::GetExecutionResourceCount \(Método\)](../Topic/ITopologyNode::GetExecutionResourceCount%20Method.md)|Devuelve el número de recursos de ejecución agrupados bajo este nodo.|  
|[ITopologyNode::GetFirstExecutionResource \(Método\)](../Topic/ITopologyNode::GetFirstExecutionResource%20Method.md)|Devuelve el primer recurso de ejecución agrupados bajo este nodo en orden de enumeración.|  
|[ITopologyNode::GetId \(Método\)](../Topic/ITopologyNode::GetId%20Method.md)|Devuelve el identificador único del administrador de recursos para este nodo.|  
|[ITopologyNode::GetNext \(Método\)](../Topic/ITopologyNode::GetNext%20Method.md)|Devuelve una interfaz al siguiente nodo de la topología en orden de enumeración.|  
|[ITopologyNode::GetNumaNode \(Método\)](../Topic/ITopologyNode::GetNumaNode%20Method.md)|Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.|  
  
## Comentarios  
 Esta interfaz se utiliza normalmente para recorrer la topología de sistema según lo definido por el administrador de recursos.  
  
## Jerarquía de herencia  
 `ITopologyNode`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)