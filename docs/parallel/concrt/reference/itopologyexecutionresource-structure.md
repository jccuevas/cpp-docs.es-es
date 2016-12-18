---
title: "ITopologyExecutionResource (Estructura) | Microsoft Docs"
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
  - "concrtrm/concurrency::ITopologyExecutionResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITopologyExecutionResource (estructura)"
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
caps.latest.revision: 10
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ITopologyExecutionResource (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una interfaz a un recurso de ejecución definido por el Administrador de recursos.  
  
## Sintaxis  
  
```  
struct ITopologyExecutionResource;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ITopologyExecutionResource::GetId \(Método\)](../Topic/ITopologyExecutionResource::GetId%20Method.md)|Devuelve el identificador único del administrador de recursos para este recurso de ejecución.|  
|[ITopologyExecutionResource::GetNext \(Método\)](../Topic/ITopologyExecutionResource::GetNext%20Method.md)|Devuelve una interfaz al siguiente recurso de ejecución en orden de enumeración.|  
  
## Comentarios  
 Esta interfaz se utiliza normalmente para recorrer la topología de sistema según lo definido por el administrador de recursos.  
  
## Jerarquía de herencia  
 `ITopologyExecutionResource`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)