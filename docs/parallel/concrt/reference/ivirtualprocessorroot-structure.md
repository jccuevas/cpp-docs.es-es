---
title: "IVirtualProcessorRoot (Estructura) | Microsoft Docs"
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
  - "concrtrm/concurrency::IVirtualProcessorRoot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IVirtualProcessorRoot (estructura)"
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
caps.latest.revision: 18
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IVirtualProcessorRoot (Estructura)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una abstracción para un subproceso de hardware en el que un proxy del subproceso puede ejecutarse.  
  
## Sintaxis  
  
```  
struct IVirtualProcessorRoot : public IExecutionResource;  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IVirtualProcessorRoot::Activate \(Método\)](../Topic/IVirtualProcessorRoot::Activate%20Method.md)|Hace que el proxy del subproceso asociado a la interfaz del contexto de ejecución `pContext` empiece a ejecutarse en esta raíz de procesador virtual.|  
|[IVirtualProcessorRoot::Deactivate \(Método\)](../Topic/IVirtualProcessorRoot::Deactivate%20Method.md)|Hace que el proxy del subproceso que se está ejecutando actualmente en esta raíz de procesador virtual deje de enviar el contexto de ejecución.  El proxy del subproceso reanudará la ejecución en una llamada al método `Activate`.|  
|[IVirtualProcessorRoot::EnsureAllTasksVisible \(Método\)](../Topic/IVirtualProcessorRoot::EnsureAllTasksVisible%20Method.md)|Hace que los datos almacenados en la jerarquía de la memoria de procesadores individuales se vuelvan visible a todos los procesadores del sistema.  Asegura que una barrera de memoria completa se ha ejecutado en todos los procesadores antes de que el método se devuelva.|  
|[IVirtualProcessorRoot::GetId \(Método\)](../Topic/IVirtualProcessorRoot::GetId%20Method.md)|Devuelve un identificador único para la raíz del procesador virtual.|  
  
## Comentarios  
 Cada raíz del procesador virtual tiene un recurso de ejecución asociado.  La interfaz `IVirtualProcessorRoot` se hereda de la interfaz [IExecutionResource](../../../parallel/concrt/reference/iexecutionresource-structure.md).  Varias raíces del procesador virtual pueden corresponder al mismo subproceso del hardware subyacente.  
  
 El administrador de recursos concede las raíces del procesador virtual a programadores en respuesta a las solicitudes de recursos.  Un programador puede usar una raíz del procesador virtual para realizar el trabajo activándolo con un contexto de ejecución.  
  
## Jerarquía de herencia  
 [IExecutionResource](../../../parallel/concrt/reference/iexecutionresource-structure.md)  
  
 `IVirtualProcessorRoot`  
  
## Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)