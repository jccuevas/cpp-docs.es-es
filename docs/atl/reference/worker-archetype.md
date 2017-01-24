---
title: "Worker Archetype | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Worker archetype"
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
caps.latest.revision: 16
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Worker Archetype
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases que se ajustan al arquetipo *worker* proporcionan el código a los elementos de trabajo de proceso en cola en un grupo de subprocesos.  
  
 **Implementación**  
  
 Para implementar una clase en este arquetipo, la clase debe proporcionar las características siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[Inicializar](../Topic/WorkerArchetype::Initialize.md)|Denominado para inicializar el objeto worker antes de cualquier solicitud se pasan a [Ejecutar](../Topic/WorkerArchetype::Execute.md).|  
|[Ejecutar](../Topic/WorkerArchetype::Execute.md)|denominado para procesar un elemento de trabajo.|  
|[Terminar](../Topic/WorkerArchetype::Terminate.md)|Denominado para desinicializar el objeto worker después de todas las solicitudes se han pasado a [Ejecutar](../Topic/WorkerArchetype::Execute.md).|  
  
|Definición de tipos|Descripción|  
|-------------------------|-----------------|  
|[RequestType](../Topic/WorkerArchetype::RequestType.md)|Una definición de tipos para el tipo de elemento de trabajo que puede ser procesado por la clase worker.|  
  
 Una clase típica *worker* tiene el siguiente aspecto:  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/CPP/worker-archetype_1.cpp)]  
  
 **Las implementaciones**  
  
 estas clases se ajustan a este arquetipo:  
  
|Clase|Descripción|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Recibe solicitudes de grupo de subprocesos y las pasa en un objeto worker que se cree y se destruya para cada solicitud.|  
  
 **Utilice**  
  
 Estos parámetros de plantilla esperan que la clase se ajuste a este arquetipo:  
  
|Nombre del parámetro|Utilizado por|  
|--------------------------|-------------------|  
|*Trabajo*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*Trabajo*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
## Requisitos  
 **encabezado:** atlutil.h  
  
## Vea también  
 [Archetypes](../../atl/reference/atl-archetypes.md)   
 [Conceptos](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)