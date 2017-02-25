---
title: "IThreadPoolConfig Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IThreadPoolConfig"
  - "ATL::IThreadPoolConfig"
  - "ATL.IThreadPoolConfig"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IThreadPoolConfig interface"
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# IThreadPoolConfig Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta interfaz proporciona métodos para configurar un grupo de subprocesos.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      __interface  
__declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660"))  
IThreadPoolConfig :  
public IUnknown  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[GetSize](../Topic/IThreadPoolConfig::GetSize.md)|Llame a este método para obtener el número de subprocesos del grupo.|  
|[GetTimeout](../Topic/IThreadPoolConfig::GetTimeout.md)|Llame a este método para obtener el tiempo máximo de milisegundos que el grupo de subprocesos esperará un subproceso para cerrar.|  
|[SetSize](../Topic/IThreadPoolConfig::SetSize.md)|Llame a este método para establecer el número de subprocesos del grupo.|  
|[SetTimeout](../Topic/IThreadPoolConfig::SetTimeout.md)|Llame a este método para establecer la hora máxima de milisegundos que el grupo de subprocesos esperará un subproceso para cerrar.|  
  
## Comentarios  
 Esta interfaz se implementa por [CThreadPool](../../atl/reference/cthreadpool-class.md).  
  
## Requisitos  
 **encabezado:** atlutil.h  
  
## Vea también  
 [Clases](../../atl/reference/atl-classes.md)   
 [CThreadPool Class](../../atl/reference/cthreadpool-class.md)