---
title: "IWorkerThreadClient Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IWorkerThreadClient"
  - "ATL::IWorkerThreadClient"
  - "IWorkerThreadClient"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IWorkerThreadClient interface"
ms.assetid: 56f4a2f5-007e-4a33-9e20-05187629f715
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# IWorkerThreadClient Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`IWorkerThreadClient` es la interfaz implementada por los clientes de la clase de [CWorkerThread](../../atl/reference/cworkerthread-class.md) .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
__interface IWorkerThreadClient  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[CloseHandle](../Topic/IWorkerThreadClient::CloseHandle.md)|Implemente este método para cerrar el identificador asociado a este objeto.|  
|[Ejecutar](../Topic/IWorkerThreadClient::Execute.md)|Implemente este método para ejecutar código cuando el identificador asociado a este objeto se señala.|  
  
## Comentarios  
 Implemente esta interfaz cuando ha codificado que necesita para ejecutarse en un subproceso de trabajo en respuesta a un identificador de señalización.  
  
## Requisitos  
 **encabezado:** atlutil.h  
  
## Vea también  
 [Clases](../../atl/reference/atl-classes.md)   
 [CWorkerThread Class](../../atl/reference/cworkerthread-class.md)