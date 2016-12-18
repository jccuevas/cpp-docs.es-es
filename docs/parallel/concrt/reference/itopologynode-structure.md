---
title: "ITopologyNode (Estructura) | Microsoft Docs"
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
  - "concrtrm/concurrency::ITopologyNode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITopologyNode (estructura)"
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: 10
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
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